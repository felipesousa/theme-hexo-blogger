---
title: Como instalar Jekyll no Linux
tags: ['Linux', 'static', 'generators', 'jekyll', 'pages']
date: 2015-03-02
comments: true
---
<img src="/images/posts/jekyll-post.jpg" alt="Como instalar Jekyll no Linux" title="Como instalar Jekyll no Linux">

Atualmente, quanto mais simples e funcional a ferramenta for, mais rapidamente ela será estudada e usada, Jekyll é um Static Page Generator criado em Ruby, super fácil de se utilizar e modificar...

<!--more-->

##O que é Jekyll?

Jekyll é um gerador de páginas estáticas criado em Ruby. Geradores de páginas estáticas são aquelas que não possuem um sistema por trás delas, um banco de dados por exemplo, páginas estaticas é uma boa pedida para caso queiramos criar sites simples, onde não temos a necessidade de ter uma interação forte com o usuário. Jekyll é uma boa pedida para caso queiramos criar um blog pessoal ou coisa do tipo, esse blog é um exemplo de site criado em Jekyll.

##Ambiente de Instalação

**Atenção:** É necessário ter Node.js instalado na máquina para executar as funções.

Bem, inicialmente para instalarmos Jekyll que é uma gem de Ruby, temos de primeiramente ter o Ruby instalado na nossa máquina. No caso do Linux, o Ruby já vem pré-instalado, para verificarmos a atual versão do Ruby que está instalada na máquina basta abrir o terminal e digitar `ruby -v`, onde o resultado será basicamente parecido com esse:

``` bash
        ruby 1.9.3p0 (2011-10-30 revision 33570) [x86_64-linux]
```

Segundo podemos ver, a versão do Ruby atual instalada é a **1.9.3**, é importante lembrar que para instalarmos o Jekyll é importante ter uma versão igual ou superior a **1.9.3**,  caso sua versão seja anterior a esta, atualize para evitar futuros possíveis erros de instalação de algumas GEM'S.

###Instalando o Jekyll

A partir de agora, vire best friend forever do seu terminal, pois é a partir dele que iremos instalar e utilizar as funções do Jekyll, e de qualquer outra Gem que você venha futuramente a utilizar.  Para instalar o Jekyll é simples basta ir no terminal e digitar o seguinte comando: `gem install jekyll`, caso precise de permissão execute `sudo gem install jekyll`, no segundo caso será requerida uma senha, insira a senha do usuário **root** e prossiga com a instalação.

**Atenção:** Caso durante a instalação seja informado algum erro, tente executar o comando **sudo gem install jekyll --source http://rubygems.org** e instale.

Caso a instalação seja concluída com sucesso, execute o comando `gem list`, que vai listar as gem's instaladas na máquina, feito isso verifique a versão atual das gem's instaladas. No meu caso ocorreu o seguinte:

``` bash
    ...
    jekyll (2.5.3)
    jekyll-coffeescript (1.0.1)
    jekyll-gist (1.1.0)
    ...
```

Pronto, com isso já temos instalado o Jekyll na versão **2.5.3**, o exemplo segue o mesmo para instalar a maioria das gem's.

##Mãos a Obra!

Bem, após tudo instalado corretamente, vamos criar uma interface 'pastel' do jekyll, basta executarmos 2 comandos para termos um exemplo simples de uma página.
Os comandos são:

* Jekyll new nome da pasta
* jekyll server

Vamos lá, com o primeiro comando, o jekyll vai criar a **estrutura básica** de uma página, onde esse Nome_da_pasta vai ser a pasta onde a estrutura vai ser criada, nesse exemplo vou criar a estrutura em uma pasta que vou chamar de *teste*,vamos ao exemplo:

``` bash
    felipe@felipe-sousa:~/Documentos/projetos$  jekyll new teste
    New jekyll site installed in /home/felipe/Documentos/projetos/teste.
```

A mensagem exibida diz que um novo site em jekyll foi criado no diretório **/home/felipe/Documentos/projetos/teste.**. Agora para vermos como está o exemplo criado localmente, basta acessar pelo terminal a pasta criada, para isso damos um `cd teste`, após isso basta executar o segundo comando `jekyll server`, com isso será exibida uma mensagem basicamente desta forma:

``` bash
    jekyll server
    Configuration file: /home/felipe/Documentos/projetos/teste/_config.yml
            Source: /home/felipe/Documentos/projetos/teste
            Destination: /home/felipe/Documentos/projetos/teste/_site
    Generating...
                    done.

            Configuration file: /home/felipe/Documentos/projetos/teste/_config.yml
                    Server address: http://127.0.0.1:4000/
                    Server running... press ctrl-c to stop.
``` 

 Pronto! Para vermos o exemplo basta irmos no navegador e digitarmos **http://localhost:4000**.

 Resultado..

 {% img img-thumbnail /images/posts/jekyll-exampler.png %}


 Viu como é simples? Qualquer dúvida, crítica ou algum ponto importante que foi mal explicado ou que faltou no artigo, comenta que agradecerei muito! até a pŕoxima!
