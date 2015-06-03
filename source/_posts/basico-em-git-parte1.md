---
title: Básico em Git - Parte 1
tags: ['control', 'versionamento', 'git']
date: 2015-01-17
comments: true
---

<img src="/images/posts/git.jpg" alt="Básico em Git - Parte 1" title="Básico em Git - Parte 1">

Bem, visto que é super importante o uso de Controle de Versões em projetos para organizá-lo de forma mais correta, ver a evolução do projeto com o tempo, etc.
<!--more-->
 Resolvi falar um pouco sobre GIT, um dos Sistemas de Controle de Versão que vem se destacando pela sua facilidade e eficiência em vários ambientes, seja trabalhando individualmente ou em grupo, GIT sempre auxilia da forma mais simples, ajudando no processo, organização e progresso do projeto.

O artigo vai ser dividido em partes. A primeira sendo como configurar, iniciar, adicionar arquivos, commitar e como excluir arquivos com GIT em um projeto individual. 

> Git é um sistema de controle de versão distribuído e um sistema de gerenciamento de código fonte, com ênfase em velocidade. O Git foi inicialmente projetado e desenvolvido por Linus Torvalds para o desenvolvimento do kernel Linux, mas foi adotado por muitos outros projetos. 

### Instalar GIT

Antes de começar, é necessário instalar o GIT na sua máquina, [você pode baixar clicando aqui](http://git-scm.com/downloads), após o download realize a instalação, após isso já estamos com tudo pronto para iniciar com Git.

### Começando com o GIT

Dependendo do seu SO, o GIT pode ser encontrado no caso de Linux e MAC no própio terminal de ambos, bastando executar os comandos a partir do mesmo, já no Windows, vem um programa que simula um terminal, e será por ele que você pode iniciar os comandos. Estou usando Linux, no meu caso, os comandos serão executados a partir do meu terminal.

**A partir de agora todos os exemplos serão executados no terminal.**

Primeiro temos que realizar 2 configurações básicas no GIT. Insira no seu terminal *ou programa* o seguinte comando. 

`$ git config --global user.name "your_username"`, onde `your_username`, você deve substituir pelo seu nome. Depois de ter configurado seu nome, adicione o comando `$ git config --global user.email youremail@example.com`, e edite o `youremail@example.com` pelo seu email, após feito isso, podemos começar de vez a versionar nossos projetos, *uffa*.

Vamos supor que eu vou começar o projeto no caminho `Documentos/teste/` que quero começar a controlar as versões dele, para isso, basta executar o comando `git init` dentro do diretório.

> git init - iniciar o versionamento pelo git.

Esse comando vai criar uma pasta `.git` no seu diretório. 

``` bash
Initialized empty Git repository in /Documentos/teste/.git/

```

Após isso vamos dar um `git status`, esse comando vai ver status do seu projeto, e vai dizer se precisa executar outro comando. Vamos supor que sua projeto está vazio, quando executamos o `git status` a mensagem [que aparece é a seguinte. 

``` bash
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)
``` 

Essa mensagem mostra que ainda não é necessário executar mais nem um comando, é como que seu repositório estivesse correto, ou nada de errado. 

Agora vamos adicionar o arquivos `teste.txt` na pasta e vamos dar novamente um `git status`. Confira o que apareceu.

``` bash
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        teste.txt

nothing added to commit but untracked files present (use "git add" to track)

```

Com essa mensagem o GIT informou que existem arquivos que precisam ser adicionados no sistema paa serem versionados. Para adicionar arquivos para serem versionado podemos usar algumas maneiras. Usando o comando `git add arquivo.ext`, podemos adicionar somente o arquivo em sí. Mais vamos supor que queiramos adicionar 10 arquivos.txt de uma vez, ficar digitando o nome e o tipo do arquivo pode se tornar cansativo. para isso podemos adicionar o comando `git add '*.txt'`, com isso ele vai adicionar todos os arquivos .txt, outra maneira *e mais prática* para adicionar os arquivos é usando o comando `git add .`, com isso ele vai adicionar todos os arquivos de todas as extensões que estão pendentes.

No exemplo vamos usar o comando `git add .`, após isso vamos novamente dar um `git status` e vejamos o que acontece.

``` bash	
On branch master
Initial commit
	Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	        new file:   teste.txt

```

Com a mensagem o GIT nos informou que existem arquivos a serem *commitados*, commitar arquivo(s) nada mais é do que comentar o que foi mudado ou o que foi adicionado naquele(s) arquivo(s). Para commitar é muito simples, basta adicionar `git commit -m "Descrição"`, onde o que está entre *aspas* será o que vamos descrever com a alteração. Veja o exemplo: 

``` bash
[master (root-commit) 194a281] adicionando o arquivo teste.txt
 1 file changed, 1 insertion(+)
 create mode 100644 teste.txt
```

A mensagem mostra que o arquivo foi commitado com sucesso! Pronto, agora já sabemos como adicionar arquivos e comenta-los. 

E se por acaso você queira apagar algum arquivo para que ele não exista mais no meu projeto? Simples! Basta executar o comando `git rm arquivo.ext`, com isso ele vai apagar o arquivo dos seu projeto. 

Bem, com esse artigo inicial aprendemos o básico de Git, tais como, como configurar o ambiente, como iniciar um respositório para que ele possa começar a ser versionado, adicionar arquivos, commitar arquivos e deletá-los. Até a próxima! :) 


