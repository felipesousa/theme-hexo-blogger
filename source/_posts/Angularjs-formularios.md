---
title: 'AngularJS | Formulários'
date: 2015-09-14 18:20:07
tags: ['angularjs', 'frontend', 'html5']
comments: true
music: "Red Radio City - Two out of three ain't rad"
musicLink: "https://open.spotify.com/track/2A9pBtvEuy3Kp2WcJawm4L"
---

Validar formulários é uma atividade um pouco chata, porém, super importante de ser praticada, nesse artigo falarei um pouco sobre como podemos utilizar o AngularJS para nos auxiliar a validarmos formulários de forma simples e rápida.

<!--more-->

Umas das coisas mais interessantes de se validar com o AngularJS é que podemos acessar diversos estados do nosso formulário, de um campo em específico e por ai vai.

Começando por uma análise simples de estados do nosso formulário, vamos considerar o seguinte formulário: 

*recomendo criar um arquivo para exemplo para acompanhar mais precisamente o artigo com os resultados que serão obtidos..*
```html
<!DOCTYPE html >
<html lang="pt-BR">
<head>
	<title>AngularJS | Formulários </title>
	<link   href="bootstrap.min.css" rel="stylesheet" >
	<script src="angular.min.js" ></script>
</head>

<body ng-app>
<nav class="navbar navbar-inverse navbar-fixed-top" >
	<div class="container">
		<div class="navbar-header">
			<a class="navbar-brand"
			   href="/" >Formulários
			</a>
		</div>
	</div>
</nav>

<div class="container main-content">
	<form name="formName">
		<div class="form-group" >
			<label for="name" >Name</label >
			<input type="text"
			       class="form-control"
			       ng-model="formField.name"
			       required
			       name="name">
		</div>
		<div class="form-group" >
			<label for="email" >Email</label >
			<input type="email"
			       class="form-control"
			       ng-model="formField.email"
			       required
			       name="email" >
		</div>
		<div class="form-group">
			<button class="btn btn-primary">Register
			</button>
		</div>
	</form >
	<pre>{{ formName | json }}</pre>
</div>
</body>
</html>	
```

No exemplo acima temos uma 2 tipos de campos, um *name* e um *email*, todos eles com um *ng-model* e um *name* definidos, vale lembrar que o uso do atributo **required** é super importante e irá nos auxiliar mais na frente. 

Se olharmos o código na linha **41**, estamos fazendo um bind do formulário, e filtrando-o para JSON. O resultado nos mostra vários estados do formulário e também dos campos. Dentre todos os estados, iremos trabalhar com alguns mais expecificamente: 

- **$dirty** - Avalia se o formulário foi utilizado.
- **$pristine** - Avalia se o formulário **não** foi utilizado.
- **$invalid** - Avalia se o formulário está invalido.
- **$valid** - Avalia se o formulário está válido
- **$name** -  Retorna o nome do formulário. 

*Todos acima podem ser utilizados em campos específicos e não somente no formulário por completo.*

Como podemos ver como retorno do nosso *formName | json*, obtemos uma json com um conjunto de estados: 
```json
{
  "$error": {},
  "$name": "formName",
  "$dirty": false,
  "$pristine": true,
  "$valid": true,
  "$invalid": false,
  "$submitted": false
}

```

Esses são os atuais estados do formulário, só que dai vem a pergunta, "Qual a importância desses estados pra mim?", a resposta é simples, o AngularJS nos oferece algumas diretivas que com elas podemos adicionar um comportamento ao formulário de acordo com esses estados. 

Umas das diretivas que podemos utilizar é a *ng-class*, que adiciona ou remove classes no DOM de acordo com uma condição, que pode ser predefinida, ou comandada por um controller, etc., onde com elas, poderemos fazer uso no nossa view para informar que o campo está ou não corretamente preenchido. [leia um pouco sobre essa diretiva.](https://docs.angularjs.org/api/ng/directive/ngClass)

Usaremos o seguinte exemplo, adicionar uma classe quando o campo de email for inválido e outra quando o campo for válido. Iremos utilizar os estados $invalid e $valid do campo para esse exemplo. O uso da atributo **required** vai nos auxiliar bastante. Antes de tudo vamos analisar os estados especificamente do campo de email:

```html
<div class="form-group" >
			<label for="email" >Email</label >
			<input type="email"
			       class="form-control"
			       ng-model="formField.email"
			       required
			       name="email" >
		</div>
		<pre>
			 {{formName.email | json}}
		</pre>
```

Com o campo ainda não preenchido, temos o seguintes estados:

```json
{
  "$validators": {},
  "$asyncValidators": {},
  "$parsers": [],
  "$formatters": [
    null
  ],
  "$viewChangeListeners": [],
  "$untouched": true,
  "$touched": false,
  "$pristine": true,
  "$dirty": false,
  "$valid": false,
  "$invalid": true,
  "$error": {
    "required": true
  },
  "$name": "email",
  "$options": null
}
```

Os estados $valid e $invalid retornam `false` e `true` respectivamente. Segundo os nossos estados, o campo email está invalido. Com essas informações já podemos comecar com o uso da diretiva *ng-class*. A diretiva será adicionada na tag `div`, a diretiva recebe como parâmetro um objeto, onde lá iremos fazer o uso das classes que queremos no elemento, sintaxe ficará desta forma: 

```html 
<div class="form-group" ng-class="{'classe': valor}">
<!-- continuação do codigo -->
```

Nos exemplos, iremos utilizar duas classes do framework Bootstrap, a classe `has-warning` para quando o campo estiver inválido e a classe `has-success` quando o campo estiver válido. Para podermos acessar estados específico, basta adicionar o nome do mesmo, logo apoś o nome do campo, dessa forma `campo.estado`, como por exemplo, se quisermos acessar o estado do campo *email* no estado **$dirty**, a sintaxe ficaria dessa forma: 

```json 
{{ formName.email.$dirty }}
```

O valor retornado será um booleano, e é aqui que nós vamos usar para implementar as classes. Continuando com o exemplo do campo de email: 

```html
<div class="form-group" ng-class="{
	'has-warning': formName.email.$invalid, 
	'has-success': formName.email.$valid}"
>
```

Se estivessemos conversando com a diretiva, estariamos falando o seguinte: "**ôôô ng-class, quando o campo for inválido, tu adiciona a classe `has-warning`, quando ele for válido tu adiciona a `has-success` beleza?**".

Dessa forma, estamos alterando as classes do campo de acordo com estado do elemento, sendo ele válido ou não. Existem algumas outras diretivas que nos auxiliam no desenvolvimento e na validação dos nossos formulários. Em outros artigos, poderemos abordar sobre esse assunto utilizando outras formas de validação.  

Bem galera, era isso, caso encontre algum erro, algo que deveria ser implemenetado, ou algum comentário sobre o artigo, basta comentar. Até a próxima o/.