---
title: Básico em Git - Parte 2
tags: ['control', 'versionamento', 'git']
date: 2015-01-18
comments: true
---

<img src="/images/posts/gitpost.jpg" alt="Básico em Git - Parte 2" title="Básico em Git - Parte 2">

Bem, voltando com a segunda parte o artigo sobre GIT, vamos aprender sobre como verificar as mudanças realizadas nos arquivos, aprender como verificar os logs do projeto e como desfazer algumas ações. 
<!--more-->

Primeiramente vamos dar um recapitulada no post anterior, lá aprendemos a adicionar, commitar, e excluir arquivos do controle do GIT. 

### Verificar modificações com GIT 
Agora vamos aprender como verificar as diferenças de um arquivo que está para ser adicionado. Vamos usar o mesmo exemplo. Vamos supor que temos um arquivo em um repositório e o modificamos, quando damos um `git status`, para ver o status do projeto, aparece a seguinte mensagem. 

``` bash
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   teste.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Segundo o GIT, ele nos informa que existem modificações no arquivo e que é preciso adicionar e commitar o mesmo. Mas, se quiséssemos ver as mudanças, como que faríamos? qual comando usariamos? A partir de agora, você vai aprender algo super importante sobre GIT, o GIT é dividido em 3 áreas principais, sendo era a **Working Directory**, **Stage Area** e **Git Directory**, o **Working Directory** é a sua parte de trabalho, arquivos nesse estágio estão pronto para serem adicionados, após adicioandos os arquivos vão para a segunda área, sendo ela a **Stage Area**, arquivos aqui, estão prontos para serem commitados, após commitados vão para o última área, a **Git Directory**, que são seus arquivos versionados e etc. 

Porque é importante aprender sobre essas áreas? Simples! Dependendo de cada área o comando pra verificar as modificações se altera. Vamos supor que eu tenho arquivos a serem *adicionados*, logo eles estão na área `Working Directory`, o comando para verificar as alterações no arquivo é o `git diff`, se aplicado no exemplo acima, ficaria desta forma. 

``` bash
$ git diff 

diff --git a/teste.txt b/teste.txt
index e69de29..8ca3766 100644
--- a/teste.txt
+++ b/teste.txt
@@ -0,0 +1 @@

+Exemplo de verificação.. :)

\ No newline at end of file
```

Para entender o que foi modificado, temos que entender os *simbolos*, o simbolo de `+`, significa as linhas que foram adicionados, já o de `-`, significa que determinada(s) linha(s), foram retiradas. Pronto, sabendo disso podemos deduzir que no arquivo `teste.txt`foi adicionado a linha *+Exemplo de verificação.. :)*. 

Mais vamos supor que já tenhamos adicionado o(s) arquivos(s) e faltando apenas commitar, no caso estamos na **Stage Area**, o comando para verificar as modificações é `git diff --staged`. O mesmo vai ocorrer como no exemplo anterior.

E vamos supor, acidentalmente você(acredite isso acontece muito!) adiciona arquivos que estavam na **Working Directory**, pra **Stage Area**, o que fazer? simples, o GIT nos oferece o comando `git reset HEAD arquivo.ext`, esse comando tira o(s) último(s) arquivo(s), que estavam na **Stage Area** e voltam para o **Working Directory**.

Vamos adicionar arquivos para a **Stage Area** veja o exemplo:

``` bash
$ git status
	On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   teste.txt

no changes added to commit (use "git add" and/or "git commit -a")

//

$ git add .
//

$ git status

On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   teste.txt

```

Pronto, arquivos estão na **Stage Area**, vamos adicionar o comando `git reset HEAD .`, para voltarmos ao **Working Directory** :

``` bash
$ git reset HEAD .

Unstaged changes after reset:
M	teste.txt

// Após feito isso vamos dar um git status.

$ git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   teste.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Pronto, os arquivos voltaram para o nivel inicial.




### Log's com GIT

Logs em GIT são marcados a partir dos seus commits, existem algumas forma de verificar os logs do seu projeto, o comando `git log` mostra de uma forma bem simples os seus commits, com a data, o autor e o nome do commit. Vamos executar o comando e ver o exemplo: 

``` bash
$ git log

commit f448501027e2693af63e892a9bbb371a4ed55745
Author: Felipe Sousa <felipzbr@gmail.com>
Date:   Sun Jan 18 11:39:22 2015 -0300

    initial commit
```

No meu caso, esse repositório nao possui muitos commits, então o seu *log* foi bem pequeno, mostrando apenas 1 commit. 

Mais vamos supor que você está em um projeto gigante com varios meses de trabalho, verificar o log, olhando commit por commit se torna cansativo e estressante. Para esse ocasião o GIT tem o comando, `git log --pretty=oneline`, esse comando vai apenas mostrar os nomes do commits um por um em linha, veja o exemplo: 

``` bash
$ git log --pretty=oneline

f448501027e2693af63e892a9bbb371a4ed55745 initial commit
```
Como visto, ele mostrou os meus commits em linha, como apenas exite 1 commit, ele o listou somente.

Pronto, simples e fácil verificar o log do seu projeto com GIT.

Por hora é só, nesse parte do artigo aprendemos como ver as  modificações de arquivos, aprendemos sobre os estágios do GIT e aprendemos a verificar os logs do projeto. Obrigado e até a proxima! 

