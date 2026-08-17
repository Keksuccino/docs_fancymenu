---
title: API JavaScript do navegador
description: >-
  Como usar a API JavaScript do FancyMenu em recursos baseados no Rinku, como o
  elemento Browser.
---
# API JavaScript do FancyMenu

O FancyMenu injeta uma ponte JavaScript em todos os recursos baseados no [Rinku](https://modrinth.com/mod/rinku) (por exemplo, o elemento **Browser**). A ponte permite que o conteúdo web:

- execute qualquer [ação](./action-scripts) do FancyMenu diretamente pelo JavaScript;
- leia qualquer [placeholder](/placeholders) do FancyMenu de forma assíncrona.

Dois globais expõem a API:
- `window.fancymenu` – namespace principal
- `window.FancyMenu` – alias (espelha exatamente a estrutura de `fancymenu`)

Use o evento `fancymenu-ready` ou a detecção de recursos para garantir que a ponte esteja disponível antes de chamá-la.

## 1. Namespaces e estrutura

- `fancymenu.actions` – executa ações do FancyMenu no navegador.
- `fancymenu.placeholders` – lê valores de placeholders do FancyMenu de forma assíncrona.
- `FancyMenu` espelha `fancymenu`, portanto ambos expõem os mesmos subnamespaces.

As ações oferecem dois auxiliares:
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

O conteúdo também pode ser hospedado localmente: coloque os arquivos HTML em `<game-directory>/config/fancymenu/assets/` e carregue-os por meio de URLs no formato `file:///config/fancymenu/assets/<name>.html`.

## 3. Executando ações

Use o namespace `fancymenu.actions`. Cada chamada corresponde às strings de ação usadas nos scripts do FancyMenu.

### Chamadas rápidas

```javascript
fancymenu.actions.execute('quitgame');                // ação sem valor
fancymenu.actions.execute('opengui', 'title_screen'); // ação com valor
fancymenu.actions.execute('set_variable', 'hp:20');   // o valor usa o formato nome:valor
```

### Com callbacks

```javascript
fancymenu.actions.executeWithCallback(
    'opengui',
    'title_screen',
    result => console.log('Tela inicial aberta'),
    error  => console.error('Falha ao abrir:', error)
);

// O parâmetro de valor é opcional. Quando omitido, passe os callbacks diretamente após actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Saída iniciada'),
    error  => console.error('Falha ao sair:', error)
);
```

Os auxiliares legados `fancymenu.execute(...)` e `fancymenu.executeWithCallback(...)` continuam encaminhando as chamadas para o namespace `actions`.

### Tipos de ação comuns

- `quitgame` – sai do jogo imediatamente (sem valor)
- `back_to_last_screen` – retorna à GUI anterior (sem valor)
- `opengui` – abre uma tela do FancyMenu ou do vanilla (valor: identificador da tela)
- `openlink` – abre um navegador (valor: URL)
- `sendmessage` – envia uma mensagem no chat (valor: texto da mensagem)
- `set_variable` – atribui uma variável do FancyMenu (valor: `nome:valor`)
- `joinserver` – conecta-se a um servidor (valor: endereço)
- `disconnect_server_or_world` – desconecta e vai para uma tela de destino (valor: identificador da tela)

Todas as ações existentes no FancyMenu estão disponíveis pela ponte; consulte os [scripts de ação](./action-scripts) para ver o catálogo completo.

## 4. Lendo placeholders

O sistema de [placeholders](/placeholders) do FancyMenu é exposto por `fancymenu.placeholders` (e `FancyMenu.placeholders`). Ambos os métodos auxiliares retornam `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Fornecendo variáveis

- As variáveis são strings no formato `nome:valor`. A ponte divide a string somente no **primeiro** dois-pontos, portanto o valor pode conter dois-pontos adicionais.
- Nomes e valores têm os espaços removidos; nomes vazios são rejeitados.
- Forneça todas as variáveis exigidas pelo placeholder. Omita as opcionais.

### Exemplos

```javascript
// Sem variáveis
fancymenu.placeholders.get('playername')
    .then(name => console.log('Jogador:', name));

// Uma variável
fancymenu.placeholders.getWithVars('uptime_duration', 'output_as_millis:false')
    .then(seconds => console.log('Tempo de atividade (s):', seconds));

// Várias variáveis
fancymenu.placeholders.getWithVars(
    'split_text',
    'input:apple|banana|carrot',
    'regex:\\|',
    'max_parts:-1',
    'split_index:1'
).then(part => console.log('Parte selecionada:', part));
```

### Modelo de erros

Promises rejeitadas contêm um erro estruturado:

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

## 5. Exemplo completo

```html
<!DOCTYPE html>
<html>
<head>
    <title>Integração com o FancyMenu</title>
</head>
<body>
    <h1>Controles do jogo</h1>
    
    <button onclick="quitGame()">Sair do jogo</button>
    <button onclick="openTitleScreen()">Tela inicial</button>
    <button onclick="disconnectFromServer()">Desconectar</button>
    <button onclick="setVariable()">Definir variável</button>
    <button onclick="loadPlaceholders()">Carregar placeholders</button>

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
                () => console.log('Tela inicial aberta!'),
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
                    'Tempo de atividade (segundos): ' + uptimeSeconds + '\n' +
                    'Segunda fruta: ' + secondFruit;
            }).catch(error => {
                console.error('Falha na solicitação do placeholder:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Práticas recomendadas e observações

- **Detecte a ponte** antes de usá-la ou escute o evento `fancymenu-ready`.
- **Trate os erros** (callbacks para [ações](/action-scripts), `.catch` para [placeholders](/placeholders)) para apresentar informações úteis.
- **Valide as entradas** antes de passá-las para ações ou variáveis de [placeholders](/placeholders).
- **Limite as solicitações**; evite sobrecarregar a ponte com chamadas rápidas e repetidas (especialmente em loops de atualização de placeholders).
- **Segurança:** o conteúdo do navegador pode invocar qualquer ação registrada do FancyMenu, incluindo ações de arquivo, rede, comando, área de transferência, pacote de recursos, link e saída. Carregue somente páginas confiáveis e valide todos os dados recebidos do conteúdo web.

## 7. Solução de problemas

1. Confirme se a página foi carregada em um navegador Rinku controlado pelo FancyMenu.
2. Verifique o console do navegador em busca de erros de JavaScript.
3. Confira se o identificador do [placeholder](/placeholders) ou o tipo de [ação](/action-scripts) está correto e se os valores exigidos foram fornecidos.
4. Consulte o log do Minecraft (`latest.log`) em busca de mensagens de erro do FancyMenu caso a execução falhe inesperadamente.
