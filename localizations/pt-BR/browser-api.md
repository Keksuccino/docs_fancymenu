---
title: API JavaScript do Browser
description: >-
  Como usar a API JavaScript do FancyMenu em recursos baseados em Rinku, como o
  elemento Browser.
sourceBlobSha: 1dff260c0c5337037200dbf9033300a6bba56ca1
---
# API JavaScript do FancyMenu

O FancyMenu injeta uma ponte JavaScript em todos os recursos baseados em [Rinku](https://modrinth.com/mod/rinku) (por exemplo, o elemento **Browser**). A ponte permite que o conteúdo da web:

- execute diretamente do JavaScript qualquer [ação](/action-scripts) do FancyMenu;
- leia qualquer [placeholder](/placeholders) do FancyMenu de forma assíncrona.

Dois objetos globais expõem a API:
- `window.fancymenu` – namespace principal
- `window.FancyMenu` – alias (espelha exatamente a estrutura de `fancymenu`)

Use o evento `fancymenu-ready` ou a detecção de recursos para garantir que a ponte esteja disponível antes de chamá-la.

## 1. Namespaces e estrutura

- `fancymenu.actions` – executa ações do FancyMenu no navegador.
- `fancymenu.placeholders` – lê os valores dos placeholders do FancyMenu de forma assíncrona.
- `FancyMenu` espelha `fancymenu`, portanto ambos expõem os mesmos subnamespaces.

As ações oferecem dois métodos auxiliares:
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

O conteúdo também pode ser hospedado localmente: coloque os arquivos HTML em `<game-directory>/config/fancymenu/assets/` e carregue-os por URLs no formato `file:///config/fancymenu/assets/<name>.html`.

## 3. Executar ações

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
    result => console.log('Tela de título aberta'),
    error  => console.error('Falha ao abrir:', error)
);

// O parâmetro de valor é opcional. Quando omitido, passe os callbacks logo após actionType.
fancymenu.actions.executeWithCallback(
    'quitgame',
    result => console.log('Saída iniciada'),
    error  => console.error('Falha ao sair:', error)
);
```

Os métodos antigos `fancymenu.execute(...)` e `fancymenu.executeWithCallback(...)` ainda encaminham as chamadas para o namespace `actions`.

### Tipos de ação comuns

- `quitgame` – fecha o jogo imediatamente (sem valor)
- `back_to_last_screen` – retorna à interface anterior (sem valor)
- `opengui` – abre uma tela do FancyMenu ou do vanilla (valor: identificador da tela)
- `openlink` – abre um navegador (valor: URL)
- `sendmessage` – envia uma mensagem no chat (valor: texto da mensagem)
- `set_variable` – define uma variável do FancyMenu (valor: `name:value`)
- `joinserver` – conecta a um servidor (valor: endereço)
- `disconnect_server_or_world` – desconecta e vai para uma tela de destino (valor: identificador da tela)

Todas as ações disponíveis no FancyMenu também podem ser usadas pela ponte. Consulte [scripts de ação](/action-scripts) para ver o catálogo completo.

## 4. Ler placeholders

O sistema de [placeholders](/placeholders) do FancyMenu é exposto por `fancymenu.placeholders` (e `FancyMenu.placeholders`). Os dois métodos auxiliares retornam `Promise<string>`:

```ts
fancymenu.placeholders.get(identifier: string): Promise<string>
fancymenu.placeholders.getWithVars(identifier: string, ...vars: string[]): Promise<string>
```

### Fornecer variáveis

- As variáveis são strings no formato `name:value`. A ponte divide a string somente no **primeiro** sinal de dois-pontos, então o valor pode conter outros sinais de dois-pontos.
- Os nomes e valores têm os espaços em branco removidos; nomes vazios não são aceitos.
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

As promises rejeitadas contêm um erro estruturado:

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
    <button onclick="openTitleScreen()">Tela de título</button>
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
                    'Tempo de atividade (segundos): ' + uptimeSeconds + '\n' +
                    'Segunda fruta: ' + secondFruit;
            }).catch(error => {
                console.error('Falha na solicitação de placeholder:', error);
            });
        }
    </script>
</body>
</html>
```

## 6. Boas práticas e observações

- **Detecte a ponte** antes de usá-la ou escute o evento `fancymenu-ready`.
- **Trate os erros** (callbacks para [ações](/action-scripts), `.catch` para [placeholders](/placeholders)) para fornecer mensagens úteis.
- **Valide as entradas** antes de passá-las para ações ou variáveis de [placeholders](/placeholders).
- **Limite a frequência das solicitações**; evite enviar chamadas em sequência para a ponte (especialmente em ciclos de atualização de placeholders).
- **Segurança:** o conteúdo do Browser pode invocar qualquer ação registrada do FancyMenu, incluindo ações de arquivo, rede, comando, área de transferência, pacote de recursos, link e saída. Carregue apenas páginas confiáveis e valide todos os dados recebidos do conteúdo da web.

## 7. Solução de problemas

1. Confirme se a página foi carregada em um navegador Rinku controlado pelo FancyMenu.
2. Verifique se há erros de JavaScript no console do navegador.
3. Confira se o identificador do [placeholder](/placeholders) ou o tipo de [ação](/action-scripts) está correto e se os valores obrigatórios foram fornecidos.
4. Se a execução falhar inesperadamente, verifique as mensagens de erro do FancyMenu no log do Minecraft (`latest.log`).
