#Hexo Blogger Theme

Theme built on the top of [Hexo](http://hexo.io/)'s standard [landscape theme](https://github.com/hexojs/hexo-theme-landscape). This theme's been written to be the new theme of my [blog](http://felipesousa.github.io/) (*originally made with [Jekyll](http://jekyllrb.com/)*).

## [Felipe Sousa](http://felipesousa.github.io)

My personal website where I talk about front-end development like HTML5, CSS3 and JavaScript.

## How it works?

I use [Hexo](http://hexo.io/), a static generator based in JavaScript, to create this blog.

## First steps

1. Install [Git](http://git-scm.com/downloads) and [Node.js](http://nodejs.org/), in case you don't have them yet.

2. Once installed these dependencies, open up the terminal and install [Hexo](http://hexo.io/) with the following command:

  ```sh
  $ [sudo] npm install hexo-cli -g
  ```

3. Now clone the project:

  ```sh
  $ git clone https://github.com/felipesousa/theme-hexo-blogger.git
  ```

4. Navigate to the project folder:

  ```sh
  $ cd theme-hexo-blogger
  ```

5. Install all dependencies of project:
  
  ```sh
  $ [sudo] npm install
  ``` 

6. And finally run:

  ```sh
  $ hexo server --watch
  ```

You'll have access to the website at `0.0.0.0:4000/` 0/

### Generate files and deploy 

1. For generate static pages: 
  
  ```sh
  $ hexo generate
  ```	

2. Deploy: 
  
  ```sh
  $ hexo deploy 
  ```

*Read more about generate files and deploy [here](http://hexo.io/docs/generating.html)*

## File structure

The basic file structure for the project is organized in the following way:

```
.
|-- scaffolds
|-- source
|-- themes/
|------ landscape/
|----------- layout
|----------- scripts
|----------- source
|----------- Gruntfile.js
|----------- _config.yml
|----------- package.json	
|-- package.json
`-- _config.yml
```

##Basic informations about structure of project

### [scaffolds](https://github.com/felipesousa/theme-hexo-blogger/tree/master/scaffolds)

Project layout defaults.  

### [source](https://github.com/felipesousa/theme-hexo-blogger/tree/master/source)

Folder where posts and pages are.

### [package.json](https://github.com/felipesousa/theme-hexo-blogger/blob/master/package.json)

File of configuration of dependencies for project.

### [_config.yml](https://github.com/felipesousa/theme-hexo-blogger/blob/master/_config.yml)

It stores most of the settings of the application.



### Theme Landscape Configurations

### [themes/landscape](https://github.com/felipesousa/theme-hexo-blogger/tree/master/themes/landscape/)

Where configurations and informations of theme are saved.

### [themes/landscape/layout](https://github.com/felipesousa/theme-hexo-blogger/tree/master/themes/landscape/layout)

Informations about all structure of theme.

### [themes/landscape/scripts](https://github.com/felipesousa/theme-hexo-blogger/tree/master/themes/landscape/scripts)

Script request of page.

### [themes/landscape/source](https://github.com/felipesousa/theme-hexo-blogger/tree/master/themes/landscape/source)

Folder and files of JS, CSS, IMAGES.

### [Gruntfile.js](https://github.com/felipesousa/theme-hexo-blogger/tree/master/themes/landscape/Gruntfile.js)

File of configuration for task runner Grunt.js.

### [_config.yml](https://github.com/felipesousa/theme-hexo-blogger/tree/master/themes/landscape/_config.yml)

It stores most of the settings of the only theme.

### [package.json](https://github.com/felipesousa/theme-hexo-blogger/tree/master/themes/landscape/package.json)

File of configuration of dependencies for project.


Any questions, problems or bug ? [Open an issue](https://github.com/felipesousa/theme-hexo-blogger/issues)! = D







