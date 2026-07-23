---
title: Texto de Splash
description: Como criar textos de splash personalizados no FancyMenu.
---
# Elemento de Texto de Splash Personalizado

O elemento de Texto de Splash no FancyMenu é uma versão totalmente personalizável e aprimorada dos splashes balançantes do título do Minecraft. Ele mantém o movimento de balanço familiar enquanto oferece controle sobre o que aparece, como fica e quando é atualizado.

> [!WARNING]
> Lembre-se de que você realmente não pode personalizar o elemento original de Texto de Splash Vanilla na tela de título, então você deve **excluí-lo** e usar um elemento de Texto de Splash personalizado no lugar.

## Adicionando e Selecionando o Elemento
- Abra o editor de layout e adicione o elemento chamado `Splash Text`.
- Clique com o botão esquerdo uma vez para selecioná-lo e mostrar a caixa delimitadora, depois clique com o botão direito para abrir o menu de contexto. Todas as opções de configuração ficam nesse menu.

## Escolhendo de Onde o Texto de Splash Vem
- `Source Mode: Vanilla` mantém os splashes aleatórios clássicos que acompanham o Minecraft.
- `Source Mode: Direct Input` permite inserir seu próprio texto por meio de `Input Splash Text`. Isso só suporta uma única linha de texto de splash, mas a linha pode conter placeholders.
- `Source Mode: Text File` pega uma linha aleatória de um arquivo `.txt` que você escolher com `Set Source Text File`. Cada linha não vazia pode se tornar o splash ativo.
- Trocar de modo redefine o texto ativo, então você pode experimentar com segurança. Se o texto parecer preso, altere para outro modo ou clique em `Refresh On Screen Load: Enabled` para forçar um novo sorteio toda vez que o menu abrir.

## Exemplo de Arquivo de Texto
Ao usar o modo de origem "Text File", salve sua lista de splashes como texto simples (UTF-8 sem BOM). Cada linha é um possível splash:

```
Welcome to FancyMenu!
{"placeholder":"your_placeholder_id_here"}
{"text":"This is gold and bold text.","color":"gold","bold":true}
&6Use &lMinecraft formatting codes!
```

Substitua `your_placeholder_id_here` pelo placeholder que você quer resolver em tempo de execução. O FancyMenu escolhe uma linha aleatória não vazia sempre que o splash é atualizado.

## Fazendo com que Fique do Jeito que Você Quer
- Use `Set Scale` e `Set Rotation` para controlar o tamanho e o ângulo de rotação.
- `Set Text Color` aceita um valor hexadecimal (por exemplo `#FFFF00`) para combinar com o seu tema.
- `Shadow: Enabled` adiciona a sombra projetada do Minecraft; desative para texto sem sombra.
- `Bouncing: Enabled` mantém o movimento de balanço familiar; desative para um rótulo estático.
- O FancyMenu renderiza o splash como um componente completo do Minecraft, então códigos de cor e outros destaques de texto funcionam como esperado.

## Recursos de Texto Dinâmico
- Os placeholders são resolvidos antes da renderização, então você pode referenciar nomes de jogadores, datas ou outros valores suportados dentro do texto de splash.
- Como o elemento aceita o JSON serializado de componentes do Minecraft, você pode colar trechos avançados de JSON em Direct Input ou no seu arquivo de texto. O elemento os desserializa automaticamente e cai para texto literal se algo der errado.

## Solução de Problemas
- Texto vazio em Direct Input mostra `< empty splash element >` enquanto você edita. Digite qualquer coisa (até mesmo um espaço) para remover o aviso.
- Se um arquivo de texto não contiver linhas válidas, o elemento exibe `ERROR: SPLASH FILE IS EMPTY`. Adicione pelo menos uma linha não vazia e reabra a tela.
- Erros de JSON serializado voltam para texto simples. Use a estrutura padrão de JSON da Mojang ou teste os trechos com o comando vanilla `/tellraw` antes de colar.
