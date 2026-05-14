---
title: API JavaScript do Browser
description: >-
  Como usar a API JavaScript do FancyMenu em recursos de mods baseados em MCEF,
  como o elemento Browser.
---

# API JavaScript do FancyMenu

O FancyMenu injeta uma ponte JavaScript em todos os recursos com base em MCEF (por exemplo, o elemento **Browser**). A ponte permite que o conteúdo web:

- execute qualquer [ação](./action-scripts) do FancyMenu diretamente do JavaScript,
- leia qualquer [placeholder](/placeholders) do FancyMenu de forma assíncrona.

Duas variáveis globais expõem a API:
- `window.fancymenu` – namespace principal
- `window.FancyMenu` – alias (espelha exatamente a estrutura de `fancymenu`)

Use o evento `fancymenu-ready`, ou detecção de recurso, para garantir que a ponte esteja disponível antes de chamá-la.

## 1. Namespaces e Estrutura

- `fancymenu.actions` – executa ações do FancyMenu a partir do navegador.
- `fancymenu.placeholders` – lê valores de placeholders do FancyMenu de forma assíncrona.
- `FancyMenu` espelha `fancymenu`, então ambos expõem os mesmos subnamespaces.

As ações expõem dois auxiliares:
- `fancymenu.actions.execute(actionType, actionValue?)`
- `fancymenu.actions.executeWithCallback(actionType, actionValue?, onSuccess?, onFailure?)`

## 2. Disponibilidade

```javascript
if (typeof fancymenu !== 'undefined') {
    // seguro para usar
}

window.addEventListener('fancymenu-ready', () => {
    console.log('A API do FancyMenu está pronta');
});
```

O conteúdo também pode ser hospedado localmente: coloque arquivos HTML em `config/fancymenu/assets/` e carregue-os por URLs no formato `file:///config/fancymenu/assets/<nome>.html`.

## 3. Executando Ações

Use o namespace `fancymenu.actions`. Cada chamada corresponde às strings de ação usadas nos scripts do FancyMenu.

### Chamadas Rápidas

```javascript
fancymenu.actions.execute('quitgame');                // ação sem valor
fancymenu.actions.execute('opengui', 'title_screen'); // ação com valor
fancymenu.actions.execute('set_variable', 'hp:20');   // valor usa o formato nome:valor
```

### Com Callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Tela de título aberta'),
    error  => console.error('Falha ao abrir:', error)
);

// O parâmetro value é opcional. Quando omitido, passe os callbacks diretamente após actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Saída acionada'),
    error  => console.error('Falha ao sair:', error)
);

Os helpers legados `fancymenu.execute(...)` e `fancymenu.executeWithCallback(...)` ainda funcionam e delegam para o namespace `actions`, então o conteúdo existente não precisa ser alterado imediatamente.
```

### Tipos de Ação Comuns

- `quitgame` – encerra o jogo imediatamente (sem valor)
- `back_to_last_screen` – retorna à GUI anterior (sem valor)
- `opengui` – abre uma tela do FancyMenu ou vanilla (valor: identificador da tela)
- `openlink` – abre um navegador (valor: URL)
- `sendmessage` – envia uma linha de chat (valor: texto da mensagem)
- `set_variable` – atribui uma variável do FancyMenu (valor: `nome:valor`)
- `joinserver` – conecta a um servidor (valor: endereço)
- `disconnect_server_or_world` – desconecta e vai para uma tela de destino (valor: identificador da tela)

Toda ação existente no FancyMenu está disponível pela ponte; veja os [scripts de ação](./action-scripts) para o catálogo completo.

## 4. Lendo Placeholders

O sistema de [placeholders](/placeholders) do FancyMenu é exposto por meio de `fancymenu.placeholders` (e `FancyMenu.placeholders`). Ambos os métodos auxiliares retornam `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Fornecendo Variáveis

- As variáveis são strings no formato `nome:valor`. A ponte divide apenas no **primeiro** dois-pontos, então o valor pode conter outros dois-pontos.
- Nomes e valores são aparados; nomes vazios são rejeitados.
- Forneça quantas variáveis o placeholder exigir. Omitam-se as opcionais.

### Exemplos

```javascript
// Sem variáveis
fancymenu.placeholders.get('playername')
    .then(name => console.log('Jogador:', name));

// Uma variável
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Tempo ativo (s):', seconds));

// Várias variáveis
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Parte selecionada:', part));
```

### Modelo de Erro

Promessas rejeitadas contêm um erro estruturado:

```ts
interface PlaceholderError {
    code: 'NOT_FOUND' | 'MISSING_VARIABLE' | 'INVALID_VARIABLE' | 'EVALUATION_ERROR' | 'INTERNAL_ERROR';
    message: string;
    details?: unknown;
}
```

Exemplo de tratamento:

```javascript
fancymenu.placeholders.get('unknown')
    .catch(error => console.warn(error.code, error.message));
```

## 5. Exemplo Completo

```html
<!DOCTYPE html>
<html>
<head>
    <title>Integração FancyMenu</title>
</head>
<body>
    <h1>Controles do Jogo</h1>
    
    <button onclick="quitGame()">Sair do Jogo</button>
    <button onclick="openTitleScreen()">Tela de Título</button>
    <button onclick="disconnectFromServer()">Desconectar</button>
    <button onclick="setVariable()">Definir Variável</button>
    <button onclick="loadPlaceholders()">Carregar Placeholders</button>

    <div id="placeholderOutput" style="margin-top:16px;font-family:monospace"></div>
    
    <script>
        function getActions() {
            if (typeof fancymenu === 'undefined') {
                console.warn('A API do FancyMenu ainda não está disponível.');
                return null;
            }
            return fancymenu.actions || fancymenu;
        }

        function quitGame() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('quitgame');
        }
        
        function openTitleScreen() {
            const actions = getActions();
            if (!actions) return;
            actions.executeWithCallback(
                'opengui',
                'title_screen',
                () => console.log('Tela de título aberta!'),
                err => console.error('Erro:', err)
            );
        }
        
        function disconnectFromServer() {
            const actions = getActions();
            if (!actions) return;
            actions.execute('disconnect_server_or_world', 'title_screen');
        }
        
        function setVariable() {
            const actions = getActions();
            if (!actions) return;
            var varName = prompt('Nome da variável:');
            var varValue = prompt('Valor da variável:');
            if (varName && varValue) {
                actions.execute('set_variable', varName + ':' + varValue);
            }
        }

        function loadPlaceholders() {
            if (typeof fancymenu === 'undefined' || !fancymenu.placeholders) {
                console.warn('A API de placeholders do FancyMenu ainda não está disponível.');
                return;
            }

            Promise.all([
                fancymenu.placeholders.get('playername'),
                fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false'),
                fancymenu.placeholders.getWithVars(
                    'split_text',
                    'input:apple|banana|carrot',
                    'regex:\\|',
                    'max_parts:-1',
                    'split_index:1'
                )
            ]).then(([playerName, uptimeSeconds, secondFruit]) => {
                document.getElementById('placeholderOutput').textContent =
                    'Jogador: ' + playerName + '\n' +
                    'Tempo ativo (segundos): ' + uptimeSeconds + '\n' +
                    'Segunda fruta: ' + secondFruit;
            }).catch(error => {
                console.error('Falha na solicitação do placeholder:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Boas Práticas e Observações

- **Detecte a ponte** antes de usá-la, ou escute `fancymenu-ready`.
- **Trate erros** (callbacks para [ações](/action-scripts), `.catch` para [placeholders](/placeholders)) para apresentar feedback útil.
- **Valide a entrada** antes de passá-la para ações ou variáveis de [placeholders](/placeholders).
- **Limite a taxa de requisições**; evite sobrecarregar a ponte com chamadas muito frequentes (especialmente loops de atualização de placeholders).
- **Segurança**: as ações são executadas com as permissões normais do jogador. Trate com cuidado os dados fornecidos pelo usuário para evitar injeção.

## 7. Solução de Problemas

1. Confirme que a página está carregada em um navegador MCEF controlado pelo FancyMenu.
2. Verifique o console do navegador em busca de erros de JavaScript.
3. Confirme se o identificador do [placeholder](/placeholders) ou o tipo de [ação](/action-scripts) está correto e se os valores obrigatórios foram fornecidos.
4. Revise o log do Minecraft (`latest.log`) em busca de mensagens de erro do FancyMenu caso a execução falhe inesperadamente.
