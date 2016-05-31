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
  // place code for your default task here
});
```