---
title: 'AngularJS | Filtros'
date: 2015-09-02 19:08:50
tags: ['angularjs', 'filtros', 'javascript']
comments: true
music: "Sublime -Wrong Way"
musicLink: "https://open.spotify.com/track/5cPfmNMC3AENizySC5oPu2"
timeRead: 6 minutos
---
<img src="/images/posts/angularjs-filters.png" alt="AngularJS | Filtros" title="AngularJS | Filtros">


Fala pessoal, depois de algum tempo sem escrever pro blog, resolvi levantar as mangas e por uma meta de no mínimo 1 artigo por semana, e quem sabe futuramente 1 por dia. Então, começando com o básico, resolvi escrever sobre um framework bastante conhecido - AngularJS - e sobre uma das 'ferramentas' interessante que ele nos pode proporcionar, sendo essas os chamados *filtros*.

<!--more-->

Filtros como o próprio nome diz, vai filtrar uma informação que será exibida ao usuário, importante lembrar que os filtros apenas formatam dado apenas para uma questão de ordem, ou organização para a visualização. Sendo assim, não vamos modificar os valores reais, apenas formatando e os ordenando para uma melhor 'leitura'.

No AngularJS filtros podem ser declarados na view ou na parte de trás da aplicação - controllers ou services - porém, para uma melhor compreensão e mais comum de se encontrar são filtros declarados na própria view.

### Tipos de filtros

Os tipos de filtros não são tão extensos, porém, com AngularJS você pode criar seus próprios filtros, iremos abordar sobre isso em outro artigo. A seguir uma lista com alguns tipos de filtros:

- **currency** - Acrescenta uma moeda ao valor passado. ex: R$, $ entre outros.
- **number** - Usados para formatar números.
- **date** - Formata o valor em formato de data. Sendo possível inserir parametros para modificarmos o formato da data, etc.
- **lowercase** - Converte tudo pra minúsculo.
- **uppercase** - Converte tudo pra maiúsculo.
- **limitTo** - Usado para limitar o quantidade de valores que serão apresentados. Limitar a quantidade de vezes que vai se repetir, etc.
- **json** - formata para o modelo json.
Esses são os principais tipos de filtros existentes no AngularJS, para mais informações e filtros, confira a [documentação oficial](https://docs.angularjs.org/api/ng/filter) do AngularJS.

### Como utilizar filtros

Depois de mostrarmos a principal usuabilidade de um filtro, e alguns dos principais tipos, vamos agora aprender como podemos usá-los em nossa aplicação, filtros são declarados por um `|` - pipeline - e logo após o tipo de filtro que vamos usar.

```text
{{Dado | Filtro:Parâmetro}}
```
Alguns filtros podem ser adicionados parâmetros para tirarmos melhor proveito, ou para uma melhor formatação do dado. Podemos também adicionar mais de um filtro ao mesmo valor.

```text
{{Dado | Filtro:Parâmetro | Filtro:Parâmetro}}
```
Nesse modelo o filtro seguinte vai se basear no resultado do filtro anterior, e não do valor original.
Usando esse tipo de declaração conseguimos filtrar nossas informações declarando o filtro na própria view. Porém, podemos fazer com que os valores já venha filtrados a partir de um controller ou um service.

#### Usando filtros no controller
Nos controlers, os filtros mudam um pouco a nomeclatura, sendo todos eles seguidos de **Filter** depois do seu nome natural. Para utilizarmos um filtro, devemos importar o mesmo no controller.


```javascript
angular.module('myApp', [])
.controller('mainCtrl', ['currencyFilter', '$scope', function(currencyFilter, $scope){}])
```

Para utilzar eles dentro do controller devemos adicionar seguinte sintaxe:

```javascript
nomeFilter(valoraAlterar, parâmetros)
```

Nesse exemplo, criaremos uma função com o nome do filtro, passando alguns parametrôs, o 1º sendo o valor a ser filtrado e o 2º sendo os parametros do filtro. Com isso podemos chegar ao seguinte código:

```javascript
angular.module('myApp', [])
.controller('mainCtrl', ['currencyFilter', '$scope', function(currencyFilter, $scope){
  $scope.valor = currencyFilter(5000, "R$");
}])
```

Nesse exemplo eu converti o valor `5000`, utilizando o filtro `currencyFilter`, passando como parâmetro o tipo de moeda, que nesse caso foi `R$`, o valor na view, será retornado `R$5000,00`.

Em relação a utilização do filtro na view, o uso nos controllers é um pouco mais complicado, porém, utilizar filtros na view pode em alguns casos afetar a performace da aplicação. Visto que os valores depois de recebidos ainda terão de ser formatados de acordo com o filtro declarado.

O uso de filtros se resumem básicamente a esses exemplos, em uma continuação, mostrarei como poderemos criar nossos próprios filtros. Até o próximo artigo 0/.
