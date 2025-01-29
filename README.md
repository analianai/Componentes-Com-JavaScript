# Componentização para paginas HTML com JavaScript

A componentização envolve a divisão de um bloco de código ou estrutura em vários mini sistemas, transformando-os em componentes completos. Por exemplo, ao separar uma tela, identificamos o que pode se tornar um componente e o que não pode. É evidente que a maior parte do código pode ser componentizada. Esse processo reduz a complexidade do script, além de facilitar a sua manutenção e reutilização. Assim, este projeto tem como objetivo demonstrar como criar um menu, footer e qualquel componente reutilizável em várias páginas de um site, utilizando JavaScript para carregar o conteúdo do menu dinamicamente. Isso permite centralizar a manutenção do menu em um único arquivo e reutilizá-lo facilmente em diferentes páginas.

## Estrutura do Projeto

````diff
/Sistema 
│-- /componentes
│── menu.html # Arquivo que contém o código HTML do menu
│── footer.html # Arquivo que contém o código HTML do rodapé
│-- -- /js
│-- includes.js # Script que carrega o menu e o footer nas páginas 
│-- index.html # Página inicial 
└── Sobre.html # Página de Sobre
````

## Funcionalidade

O menu e o footer são carregado dinamicamente através do JavaScript em cada página, evitando duplicação de código e facilitando a manutenção. Qualquer alteração no menu pode ser feita apenas no arquivo `menu.html`, e será refletida em todas as páginas do projeto.

## Como Funciona

1. O arquivo `menu.html` e `footer.html` contém o código HTML do menu.
2. O script `menu.js` e `footer.html`  usa a função `fetch()` para carregar o conteúdo do `menu.html` dentro de um contêiner nas páginas.
3. Cada página do projeto inclui o script `menu.js` e `footer.html`, que carrega o menu na `<div id="menu-container">` para menu e `<div id="footer-container">` para o footer.

## Como Usar

1. Clone este repositório para o seu ambiente local:

```bash
 git clone https://github.com/analianai/Exemplo-componentiza-o-Com-JavaScript.git
````

### Explicação do conteúdo:

1. Crie uma pasta chamada `includes.js` e insira o seguinte codigo

````js
document.addEventListener("DOMContentLoaded", function () {
    fetch("componentes/menu.html")
        .then(response => response.text())
        .then(data => {
            document.getElementById("menu-container").innerHTML = data;
        })
        .catch(error => console.error("Erro ao carregar o menu:", error));
});

document.addEventListener("DOMContentLoaded", function () {
    fetch("componentes/footer.html")
        .then(response => response.text())
        .then(data => {
            document.getElementById("footer-container").innerHTML = data;
        })
        .catch(error => console.error("Erro ao carregar o rodapé:", error));
});
````

2. O  event listener aguarda o carregamento completo do DOM (Document Object Model). O evento DOMContentLoaded é disparado quando o HTML da página é completamente carregado e o DOM é construído, mas antes que o CSS e imagens externas sejam totalmente carregados. Isso garante que o script só será executado depois que o conteúdo básico da página estiver pronto.

````js
 document.addEventListener("DOMContentLoaded", function () {...})
````

3. A função fetch() é usada para realizar uma requisição HTTP para buscar o conteúdo do arquivo menu.html que está dentro da pasta componentes. O método fetch() retorna uma Promise, o que significa que ele será assíncrono e não bloqueará o restante da execução do código.

````js
fetch("componentes/menu.html")
````

4. A primeira parte do .then() é chamada assim que a resposta da requisição HTTP é recebida. Essa função recebe o objeto response, que contém os dados da requisição. O método response.text() é usado para extrair o conteúdo do arquivo (no caso, o HTML) como uma string de texto.

````js
then(response => response.text())
````

5. O segundo .then() recebe o conteúdo do arquivo (data) como uma string de HTML. Dentro desse bloco, o código pega esse conteúdo e o insere na página.

````js
then(data => {...})
````


Copyright (c) 2025 Anália Souza

Permissão é concedida, gratuitamente, a qualquer pessoa que obtenha uma cópia deste software e dos arquivos de documentação associados (o "Software"), para lidar no Software sem restrição, incluindo sem limitação os direitos de usar, copiar, modificar, mesclar, publicar, distribuir, sublicenciar e/ou vender cópias do Software, e para permitir que as pessoas a quem o Software é fornecido o façam, desde que as condições a seguir sejam atendidas:

A notificação de copyright acima e esta permissão devem ser incluídas em todas as cópias ou partes substanciais do Software.

O Software é fornecido "no estado em que se encontra", sem garantia de qualquer tipo, expressa ou implícita, incluindo, mas não se limitando às garantias de comercialização, adequação a um propósito específico e não infração. Em nenhum caso o(s) autor(es) ou detentor(es) do copyright serão responsáveis por qualquer reclamação, dano ou outra responsabilidade, seja em uma ação de contrato, ato ilícito ou outro, decorrente de, fora de ou em conexão com o Software ou o uso ou outros negócios no Software.

Este projeto é licenciado sob a MIT License.

