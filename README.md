    __        __   _     _              _ _                               _ 
    \ \      / /__| |__ | |_ ___   ___ | (_)_ __   __ _    __ _ _ __   __| |
     \ \ /\ / / _ \ '_ \| __/ _ \ / _ \| | | '_ \ / _` |  / _` | '_ \ / _` |
      \ V  V /  __/ |_) | || (_) | (_) | | | | | | (_| | | (_| | | | | (_| |
       \_/\_/ \___|_.__/ \__\___/ \___/|_|_|_| |_|\__, |  \__,_|_| |_|\__,_|
                                                  |___/                     
        _         _                        _   _             
       / \  _   _| |_ ___  _ __ ___   __ _| |_(_) ___  _ __  
      / _ \| | | | __/ _ \| '_ ` _ \ / _` | __| |/ _ \| '_ \ 
     / ___ \ |_| | || (_) | | | | | | (_| | |_| | (_) | | | |
    /_/   \_\__,_|\__\___/|_| |_| |_|\__,_|\__|_|\___/|_| |_|
    
> Webtooling and Automation

- Editor favorito do instrutor:
    - Sublime
    - https://www.sublimetext.com/3
    - Tem uma base de usuários 4 ou 5 vezes maior do que seu maior concorrente, Atom.

# Atalhos para Funções Importantes no Sublime

| Função                  | Atalho              |
|-------------------------|---------------------|
| Fuzzy Search            | ctrl + p            |
| Goto Definition in File | "@" no fuzzy search | 
| Go to next occurrence   | ctrl + d            |
| Tab completion          | tab                 |
| Select all contents of the current parentheses | ctrl + m |
| To lowercase            | ctrl + k, ctrl + l  |
| To uppercase            | ctrl + k, ctrl + u  |

# Customizar Sublime 3 para Desenvolvimento Front End

- Ir para https://packagecontrol.io/installation e seguir as instruções
- ctrl + shift + p: digitar "pac" para procurar "package control"
- Selecionar "Package Control: Install Package"
  - Emmet (https://packagecontrol.io/packages/Emmet)
  - SideBar Enhancements (https://packagecontrol.io/packages/SideBarEnhancements)
  - ColorPicker (https://packagecontrol.io/packages/ColorPicker)
  - ColorHighlighter (https://packagecontrol.io/packages/Color%20Highlighter)

# Gulp x Grunt

- Ambos são chamados de __Build Tools__
- Gulp é mais rápido para executar tarefas porque executa-as em paralelo.
- As tarefas no Gulp são escritas num roteiro Javascrit. No Grunt, é um objeto javasript de configuração
- Gulp faz o stream dos arquivos internamente e isso diminui o I/O.

# Instalar Gulp

- https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md

```bash
# 1 . Install gulp globally
$ sudo npm install --global gulp-cli 
# 2 . Install gulp in your project devDependencies
$ cd [diretório raíz do projeto]
$ sudo npm install --save-dev gulp
# 3 . Create a gulpfile.js at the root of your project
$ touch gulpfile.js
```

```javascript
//gulpfile.js
var gulp = require('gulp');
gulp.task('default', function() {
  console.log("Hello!")
});
```

# gulp-sass

```bash
$ sudo npm install gulp-sass
```

- Crie um diretório ```/sass``` sob o diretório raíz do seu projeto. 
- Mova seus arquivos __.css__ para ```/sass``` e mude a extensão dos arquivos para __.scss__
- Acrescente em gulpfile.js
```javascript
var sass = require('gulp-sass');
//...
gulp.task('styles', function() {
    gulp.src('sass/**/*.scss')
        .pipe(sass().on('error', sass.logError))
        .pipe(gulp.dest('./css'))
})
```

# gulp-autoprefixer

Adds vendor prefixes to CSS rules using values from [Can I Use](http://caniuse.com/#cats=CSS)

```bash
npm install --save-dev gulp-autoprefixer
```

- Acrescente em gulpfile.js
```javascript
var sass = require('gulp-autoprefixer');
//...
gulp.task('styles', function() {
	gulp.src('sass/**/*.scss')
		.pipe(sass().on('error', sass.logError))
		.pipe(autoprefixer({
			browsers: ['last 2 versions']
		}))
		.pipe(gulp.dest('./css'));
});
```

> ## Troubleshoot
> **Descrição**
> 
> Ao rodar ```$ gulp styles```, tive a seguinte mensagem de erro: 
> 
> ```ReferenceError: Promise is not defined```
> - Ubuntu 14.04
> - node: v0.10.35
> - gulp-autoprefixer: 3.1.0
> 
> **Solução:**
> 
> ```$ sudo npm install es6-promise```
> 
> Incluir na 1a linha de gulpfile.js
> 
> ```var Promise = require('es6-promise').Promise;```

# gulp-watch

```bash
$ sudo npm install --save-dev gulp-watch
```

- Acrescente em gulpfile.js
```javascript
var watch = require('gulp-watch');
//...
gulp.task('styles', function() {
	gulp.src('sass/**/*.scss')
		.pipe(sass().on('error', sass.logError))
		.pipe(autoprefixer({
			browsers: ['last 2 versions']
		}))
		.pipe(gulp.dest('./css'));
});
```

# browser-sync

Browsersync will start a mini-server and provide a URL to view your site.

```bash
$ sudo npm install --save-dev browser-sync
```

- Acrescente em gulpfile.js
```javascript
var browserSync = require('browser-sync').create();
// ...
browserSync.init({
    server: "./"
});
browserSync.stream();
```
 
# ESLint

Segui as intruções em [Getting Started with ESLint](http://eslint.org/docs/user-guide/getting-started) 
e não consegui fazer o ESLint funcionar com os plugins _Sublime Linter_ e _linter-eslint_. 
Usei Ubuntu (14 e 15), (Atom e Sublime) e Gulp. 

Concluí que a instalação não deve usar o parâmetro ```-g``` no ```npm``` e nem 
```sudo```. 

```bash
# Não funciona 
$ sudo npm install -g eslint
```

Funcionou quando instalei todos os módulos no diretório do projeto (sem ```sudo```).

```
# Criar packages.js
$ npm init
# Instalar gulp, eslint e gulp-eslint no diretório /node_modules do projeto. 
$ npm install --save-dev gulp
$ npm install --save-dev eslint 
$ npm install --save-dev gulp-eslint
# Criar arquivo de configuração .eslintrc.js
$ ./node_modules/eslint/bin/eslint.js --init
# Escolhi: 
# ? Answer questions about your style
# ? Are you using ECMAScript 6 features? n
# ? Where will your code run? Browser
# ? Do you use CommonJS? No
# ? Do you use JSX? No
# ? What style of indentation do you use? Tabs
# ? What quotes do you use for strings? Single
# ? What line endings do you use? Unix
# ? Do you require semicolons? Yes
# ? What format do you want your config file to be in? JSON
```

- gulp-eslint não depende de ESLint mas procura por .eslintrc.json.

Em gulpfile.js: 
```javascript
var eslint = require('gulp-eslint');
// ...
gulp.task('lint', function () {
    return gulp.src(['./js/**/*.js','!node_modules/**'])
        .pipe(eslint())
        .pipe(eslint.format())
        .pipe(eslint.failAfterError());
});
```