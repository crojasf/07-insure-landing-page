# Insure landing page



## Descripción

Sexto proyecto para practicar como desarrollador front-end, ya a nivel Junior.

Desarrollar un landingpage  el proyecto de [Frontend Mentor](https://www.frontendmentor.io/challenges/insure-landing-page-uTU68JV8).

Se utiliza en este caso Sass como preprocesador a través de PostCSS, dependencias normalize y autoprefixer en PostCSS, y la metodología BEM para el etiquetado de los estilos. Se utiliza Git y Github Pages para el control de versiones y Demo.

## Instalación

Para preparar el entorno se debe instalar Node.js en el equipo e instalar *gulp*, *gulp-cli*, *postcss*, *gulp-postcss*, *autoprefixer* y *gulp-sass* como "--save-dev" dentro del proyecto. Por último configurar gulpfile.js con las tareas necesarias. (Ver ficheros gulpfile.js y package.json)


## Pasos a realizar en el proyecto

+ Iniciar proyecto guardando los ficheros y subiéndolos a Github.
+ Crear la estructura HTML y CSS del componente a crear.
+ Crear estilos para Mobile First y retocar algunas etiquetas HTML.
+ Aplicar MediaQuerys para estilos para Desktop y algunos ajustes finales.
+ Agregar funcionalidades JavaScript


## Demo
El resultado del proyecto puede verse [aquí](https://crojasf.github.io/06-pricing-component-with-toggle/).

![desktop-final](/design/desktop-final.png)


## Detalle para iniciar el proyecto
Para iniciar el proyecto se realizaron los siguientes pasos:

+ Ejecutar `$ npm install --save-dev gulp` para instalar gulp en el proyecto.
+ Ejecutar `$ npm init` para inicar el proyecto y se cree el fichero *package.json*.
+ Crear el fichero *gulpfile.js* para llamar a las dependencias que instalemos, primero agregando el código `$ var gulp = require('gulp');`.
+ Instalar las dependencias que vamos a utilizar ` $ npm install --save-dev gulp-cli postcss gulp-postcss autoprefixer postcss-normalize gulp-sass`.
+ Agregar dependencias y tareas en *gulpfile.js*.

```js
// gulpfile.js
const gulp = require('gulp');
const postcss = require('gulp-postcss');
const sass = require('gulp-sass');

const autoprefixer = require('autoprefixer');
const postcssNormalize = require('postcss-normalize');


function defaultTask(cb) {
	// place code for your default task here
	var processors = [
		autoprefixer,
		postcssNormalize(/* pluginOptions */
			{ browsers: 'last 2 versions' }
		),
	];
	// return gulp.src(['./src/*.scss', '!./src/_*.scss'])
	return gulp.src('./src/**/*.scss')
		.pipe(sass().on('error', sass.logError))
		.pipe(postcss(processors))
		.pipe(gulp.dest('./css'));
}

exports.default = function(){
	gulp.watch('./src/**/*.scss', gulp.series(defaultTask));
}
```
+ Ejecutar tarea de gulp `$ npx gulp` (los cambios en /src/*.scss se guartan en /css/style.css).
+ Crear repositorio en github y configurar GitHub Pages.
+ Agregar en *.gitignore* la carpeta *node_modules*.
+ Iniciar git en el proyecto ejecutando:
```
$ git init
$ git add .
$ git commit -m "Subir ficheros iniciales del proyecto"
$ git branch -M main
$ git remote add origin https://github.com/crojasf/06-pricing-component-with-toggle.git
$ git push -u origin main
```

