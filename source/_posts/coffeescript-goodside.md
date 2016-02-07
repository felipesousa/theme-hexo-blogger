---
title: CoffeeScript - Nada é tão ruim quanto parece!
date: 2016-02-06
tags: ['coffeescript', 'project', 'frontend', 'languages']
comments: true
music: ""
musicLink: ""
timeRead: ""
---
<img src="/images/posts/coffeescript-goodside.png" alt="CoffeeScript - Nada é tão ruim quanto parece!" title="CoffeeScript - Nada é tão ruim quanto parece!">
Durante muito tempo, escrever em JavaScript puro era pra mim uma perfeita combinação, sem o uso de pré-processadores ou coisas que me fizessem mudar a maneira de se escrever em JS nativo. Porém, de uns tempos pra cá, comecei a experimentar um cara chamado CoffeeScript, que é por muitos vistos com maus olhos...

<!-- more -->
Sempre tive em minha cabeça que escrever em .js era a melhor escolha, claro, amamos a sintaxe nativa do JavaScript, mas temos de concordar que, se torna bastante verboso em alguns pontos, mas claro, varia de desenvolvedor pra desenvolvedor.

Estou tendo a oportunidade em trabalhar usando Coffee como o compiler pra JavaScript. Antes de mais nada é interessante lembrarmos que, a principal proposta de um compilador, seja de CSS como Stylus, HTML como o Jade, ou de JavaScript como o CoffeeScript é principalmente facilitar o desenvolvimento, produtividade, etc, de um determinado grupo ou desenvolvedor. Seja implementando algumas particularidades para criar A ou não precisar utilizar regras de pontuação para fazer B e por ai vai.

A questão é que, ouvi falar tanto sobre esse cara nos ultimos tempos, e por incrivel que pareça 99% dos comentários são apenas sobre coisas não tão boas, ou melhor dizendo, ridicularizando o compiler. Alguns utilizam do termo de ser 'limpo demais' e ficar subtendido algumas coisas, ou alegar que 'É muito Ruby pro meu gosto!' entre outros diversos comentários que mostram o desconhecimento sobre os benefícios que vem junto a ele.

O foco CoffeeScript é compilar JavaScript, nada mais que isso, a linguagem não nasceu pra mudar a maneira de pensar - apesar de algumas coisas você precise se abstrair para entender mais perfeitamente - quando se escreve em Coffee já se sabe qual o resultado, simplesmente pelo fato de que ele apenas facilita sua vida pra você não ter que escrever tanto. Não espere que ele faça um cavalo com asas aparecer no seu código e simplifique tudo que existe ali. Sempre quando vamos usar algum pré-processador ou linguagem nova, temos de aprender como ela se comporta, suas especificades, o que precisa e o que não precisa e assim por diante, funciona assim com Sass, Jade, Less, ou qualquer outra coisa.

Primeiramente, antes de tudo e antes de usar qualquer compiler, temos que saber no mínimo escrever de forma nativa, aprender uma linguagem por meio de compiler com certeza não é uma boa escolha. Caso você não saiba, o resultado final, ou o que determinada linha faz, usar essas ferramentas não são uma boa pedida, aconselho escrever da forma nativa de ser, e com o tempo, escolher algo que lhe ajude.

## Good - Limpo e direto!

Bem, pontos que por muito desenvolvedores são considerados como negativos, vejo como vantagem, a sua sintax *light*, agiliza bastante se tratando de escrita. Vejamos alguns exemplos:

Declarando variáveis: Sem necessidade de usar o `var`.
``` coffeescript
# coffee
a = 'coffeescript'

# js
var a = 'javascript'
```

Declarando funções: Sem parâmetros, sem `()` e `{}`.

``` coffeescript
# coffee
a = ->

# js
var a = function(){}
```

Funções com parâmetros:
``` coffeescript
# coffee
a = (a, b) ->

# js
var a = function(a , b){}
```

Olhando de uma forma em exemplos simples, pouco se muda, isso porque a ideia do CoffeeScript é simplesmente se abstrair da quantidade de pontuação em trechos simples, como por exemplo, `()`, `{}`, `;`, etc.  


## Bad - O tal do `return`

Em CoffeeScript a ultima linha sempre é considerada o `return`, vamos ao exemplo:
``` coffeescript
# coffee
a = (a, b) ->
  c = a + b

# js
var a = function(a, b) {
  var c;
  return c = a + b;
};
```

Como a ùltima linha é o próprio `return`, nesse caso a função retorna `c = a + b;`, até ai muito lindo, legal.. Mas caso não queiramos retornar nada? Simples, basta adicionar na ultima linha um `return ` sem nada após ele, assim não sera retornado nada.

``` coffeescript
# coffee
a = (a, b) ->
  c = a + b
  return
```
Por mais óbvio que pareca, em alguns casos de erros, esquecer de declarar o return no fim de uma função, ou expressão, pode causar uma grande confusão, mas, basta atenção e nunca esquecer do carinha.

## Bad - Cuidado com espaços em branco!
Outro ponto do CoffeeScript que pode causar alguns problemas é que o em alguns casos podemos eliminar o uso dos `()` em determinados casos, vejamos o exemplo:

``` coffeescript
# js
var http = require('http');

# coffee
http = require 'http'
```
CoffeeScript trata como o que vem depois de um espaço em branco em alguns casos, como parâmetro do método ou função, e é o que acontece no exemplo anterior, ele considerou o `'http'` como parâmetro do `require`.

Se olharmos pelo ponto de diminuir o uso de caracteres, se trata de vantagem ter isso em alguns pontos do código, o grande problema ocorre quando podemos usar isso em lugares que são mais propícios a erros, como por exemplo, chamar uma função que não possui parâmetros e depois adicionar logo em seguida, algo que não faça parte do escopo da função, ou simplesmente outro trecho de código, vejamos o exemplo:

``` coffeescript
# coffee
a = ->
b = ->

a b

# js
var a = function (){}
var b = function (){}
a(b)
```

Ele considerou a função `b` como parâmetro da função `a`, que não recebe parâmetros na sua declaração, e isso, pode causar bastante dor de cabeça, por isso, atenção nos `" "`.

Resumindo, existem diversos outros pontos positivos e negativos ao se usar tanto o CoffeeScript, como qualquer outro compiler, cabe da experiência de usar e saber se vale ou não a pena o uso de um deles. Importante antes de tudo, experimentar para saber qual vai facilitar sua vida no dia a dia.

Para saber mais sobre o CoffeeScript,  galera do [Loop Infinito](http://loopinfinito.com.br/) fez a vez uma versão da [documentação em português](http://coffeescript.loopinfinito.com.br/).


#### Outros links:
[CoffeeScript Equivalents In ES6](https://github.com/hemanth/coffeescript-equivalents-in-es6)
[JS to Coffee](http://js2.coffee/)
[Replace CoffeeScript with ES6](https://robots.thoughtbot.com/replace-coffeescript-with-es6)
