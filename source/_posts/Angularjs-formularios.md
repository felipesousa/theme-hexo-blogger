---
title: 'AngularJS | Formulários'
date: 2015-09-14 18:20:07
tags: ['angularjs', 'frontend', 'html5']
comments: true
music: "Red Radio City - Two out of three ain't rad"
musicLink: "https://open.spotify.com/track/2A9pBtvEuy3Kp2WcJawm4L"
---

Validar formulários, é uma atividade um pouco chata, porém super importante de ser praticada, nesse artigo falarei um pouco sobre como podemos utilizar o AngularJS para validarmos formulários de forma simples e rápida.

<!--more-->

Validar formulários hoje em dia tem se tornado mais simples, alguns novos atributos vieram na bagagem com o HTML5, porém, apenas esses recursos as vezes não são suficientes para uma validação de forma mais completa, o AngularJS tem alguns utilitários que podem nos auxiliar nessa validação. 

Umas das coisas mais interessantes de se validar com o AngularJS é que podemos acessar diversos estados do nosso formulário, de um campo em específico, e por ai vai.

Começando por uma avaliação simples de estados do nosso formulário, vamos considerar o seguinte formulário - utilizando o framework bootstrap: 


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
			       name="name">
		</div>
		<div class="form-group" >
			<label for="email" >Email</label >
			<input type="email"
			       class="form-control"
			       ng-model="formField.email"
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

No exemplo acima temos uma 2 tipos de campos, um *name* e um *email*, todos eles com um *ng-model* definido, vale lembrar que o uso do atributo **required** é super importante e irá nos auxiliar mais na frente. 

Se olharmos o código na linha **41**, estamos fazendo um bind do próprio formulário, e formatando-o para json. O resultado nos mostra vários estados do formulário e também dos campos. Dentre todos os estados, iremos trabalhar com alguns: 

- **$dirty** - Avalia se o formulário foi utilizado
- **$pristine** - Avalia se o formulário **não** foi utilizado.
- **$invalid** - Avalia se o formulário está invalido.
- **$valid** - Avalia se o formulário está válido
- **$name** -  Retorna o nome do formulário. 

Todos acima podem ser utilizados em campos específicos e não somente no formulário por completo.

