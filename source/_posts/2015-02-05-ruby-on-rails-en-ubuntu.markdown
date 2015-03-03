---
layout: post
title: "Ruby on Rails en Ubuntu"
date: 2015-02-05 23:31:53 -0300
comments: true
categories: ruby rails
---
Hoy en día es super comodo desarrollar con algún Framework MVC, más si esta bien documentado y es fácil de usar.
Para ser justo existen muchos framework en distintos lenguajes uno más cómodo, documentado o mejor que el otro. Por ejemplo en php tenemos más framework que estrellas en el cielo.

Lo que en esta publicación veremos es un framework que en un instante de la historia fue muy popular, no hablamos de codeigniter(espero nunca tener que volver a usar este framework), sino que hablamos de Ruby on Rails en su versión 3 y/o 4.

Primeramente lo que vamos a hacer asumiendo que ya tienes configurado tu ubuntu.
Vamos a partir instalando lo que es ruby, en este caso 1.9.3

```bash
sudo apt-get install ruby1.9.3
```

instalar rails

Tenemos dos formas, ¿Como dos formas?
la de instalar rails 3 y la de instalar rails 4.
en el caso de rails 3
sudo apt-get install rails3

y en el caso de rails 4

```bash
gem install rails 
```
si lo instala como una gema de ruby cosa que es interesante, ahora lo que no me agrada de la instalación de rails 4 es que en instantes uno tiende a pensar  que esta haciendo nada pero por debajo esta trabajando.( Si da error de privilegios tirenle un sudo antes de gem).

una vez instalado esto ya podemos crear un proyecto en rails ya sea 3 o 4.

```bash
rails new miapp
```
va a crear el esqueleto de ruby on rails. podemos tirar un "rails s" o "rails server" que es lo mismo, pero no va a correr el server de rails, entonces para qué tiene un server si no funciona. En realidad si funciona lo que pasa es que nos faltó instalar algo que es importante nodejs

```bash
sudo apt-get install nodejs
```
si te dice que no existe nodejs te toca agregar el repositorio
```bash
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs
```
En este punto ya podemos correr el server de rails y no va a mostrar la pagina por defecto del proyecto

ahora mismo nos falta algo importante, si le atinaste la Base de Datos.

cuando generamos un proyecto rails new nombre_proyecto nos genera una configuración con sqlite3, en este punto veremos como instalar sqlite3 y la libreria para que corra la conexión.
```bash
sudo apt-get install sqlite3
sudo apt-get install libsqlite3-dev 
```
con esto ya podemos crear la base de datos.
```bash
rake db:create
```
y acaba de crear una base de datos con sqlite3

De momento nos quedamos hasta acá. Quien sabe si vuelvo a escribir de hacerlo seguire con un poco más de rails.





