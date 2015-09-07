---
title: MongoDB - Baby Steps
date: 2015-07-24 00:05:56
tags: ['MongoDB','NoSQL']
comments: true
music: "Green Day - Brain Stew"
musicLink: "https://open.spotify.com/track/1nLnpLXvl68RZCSjfkyiaa"
timeRead: 10 minutos
---
<img src="/images/posts/mongodb.jpg" style=" height:200px ;" alt="MongoDB - Baby Steps" title="MongoDB - Baby Steps">

MongoDB é uma aplicação de open source, de alta performance, orientado a documentos. Foi escrito em C++. Muitas aplicações podem, dessa forma, modelar informações de modo muito mais natural, pois os dados podem ser aninhados em hierarquias complexas e continuar a ser indexáveis e fáceis de buscar.

<!--more-->
Este será um ~~guia~~ que visa apenas listar alguns comandos simples, sem muitas apresentações, apenas sobre algumas partes funcionais da ferramenta. Informações sobre a filosofia e outras coisinhas, [visite a documentação oficial.](http://docs.mongodb.org/)

* Iniciar MongoDB.

```bash
mongo
```
##### Todos os comandos a seguir serão executados após termos iniciado o MongoDB.


* Listar base de dados existentes no banco.

```bash
show dbs
```

* Criar uma base de dados.

```bash
use NomeDoBanco
```

* Verificar em qual base de dados estamos atualmente.

```bash
db
```

### Collections

Collection é como uma estrutura de dados é chamada em MongoDB.

* Criar um collection.

```bash
db.createCollection(name, options);
```

Na criação da collection utilizamos o comando acima com dois parâmetros, o `nome` e as opções, sendo essas configurações de tamanho(em bytes) da collection, quantos documentos são permitidos, enfim, por padrão apenas o valor do `nome` é necessária, o segundo parâmetro é opcional, [leia mais sobre collections aqui.](http://docs.mongodb.org/manual/reference/method/db.createCollection/)

*exemplo da criação de uma collection "pessoas"*:

```bash
db.createCollection('pessoas')
```

* Listar as collections na base de dados atuais:

```bash
show collections
```

### Inserir Dados

Pronto, passos simples de como realizamos a criação e listagem de collections. Vamos agora ver como adicionamos dados as essas collections.

Um ponto importante a citar é que, o mongoDB utiliza arquivos em formatos JSON's para armazenar seus dados. Sabendo disso, para adicionarmos informações em nossas collections basta escrever no formato de arquivos *.json*. Leia um pouco sobre padrões de json [aqui.](http://jsonapi.org/)

* Inserir dados em uma collection:

```bash
db.nomeDaCollection.insert();
```

Com o comando acima, podemos adicionar arquivos, veja um exemplo de como podemos adicionar dados em uma collection através do método .insert():

```bash
db.pessoas.insert({nome: "felipe", idade: 17, sexo: "masculino"});
```

Como visto o exemplo acima, usamos o padrão de escrita de arquivos json para inserir dados.

### Consulta de dados

Para consultarmos uma collection e observar os dados que existem nela de 2 formas:

```bash
db.nomeDaCollection.find();
```
ou

```bash
db.nomeDaCollection.find().pretty();
```

A diferença é simples! Na primeira opção temos como output os dados jogados sem nenhuma organização, na segunda, com o implemento do método `.pretty()` os dados são mostrados de uma forma muito mais agradável e legível. Exemplo:

```bash
db.pessoas.find().pretty();

//output

{
	"_id" : ObjectId("55b190caf8ab876af97e521b"),
	"nome" : "felipe",
	"idade" : 17,
	"sexo" : "Masculino"
}

```
### Update de Dados

No mongoDB, o método `update()` serve como método de atualização de algum dado, como também de criação daquele campo caso não exista o campo.

```bash
db.nomeDaCollection.update(query, modificador, callback);
```

O método `update()` recebe três parâmetros, sendo eles `query`, que vai ser **ONDE** nós vamos alterar os dados, `modificador`, que vai ser **PELO QUE** aquele dado vai ser alterado, e um callback. Vejamos um exemplo:

```bash
db.pessoas.update({name: "felipe"}, { $set:{idade: 20} });
```

Nesse exemplo, estamos dizendo que estamos alterando o valor do campo idade onde o `name` do dado for "felipe".

*Observe que no 2º parametro utilizamos o `$set` para descrevermos que apenas aquela chave de **campo: valor** vai ser alterada quando executarmos o método, caso o `$set` não seja incluído, todos os campos de todos os dados vão ser substituidos.*

### Remover Dados

Para removermos dados de uma collection utilizamos o comando:

```bash
db.nomeDaCollection.remove();
```

Como parâmetro do método `.remove()` passsamos o dado que queremos alterar. Veja o exemplo:

```bash
db.pessoas.remove({name: "felipe"});
```

Com isso, acabo de remover todos os dados do usuário que possui o `name` como "felipe";

*Para removermos todos os dados da collection basta passar como parâmetro `{}` no método `.remove()`.*

### Deletar Collections e Base de dados

Para deletar um collection usamos o comando:

```bash
db.nomeDaCollection.drop();
```

*lembrando que o mongo não pede confirmação para deletar os dados, então avalie corretamente se a collection selecionada é a que você quer apagar.*

Para deletar uma base de dados, usamos o comando:

```bash
db.dropDatabase();
```

Com isso temos o básico em MongoDB. Existem muito mais coisas a se aprender sobre essa ferramenta fantástica. [Leia mais na documentação oficial](http://docs.mongodb.org/).
