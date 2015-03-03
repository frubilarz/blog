---
layout: post
title: "Primeros pasos en rails 4"
date: 2015-02-06 20:34:17 -0300
comments: true
categories: ruby rails
---
En esta parte vamos a ver el manejo de ruby on rails 4.

Entendiendo que en el post anterior vimos como instalar ruby on rails ya sea en su version 3 o 4, aqui ocuparemos un poco mas el framework.

Primero instalaremos mysql.

```bash
sudo apt-get install mysql-server
```
y Luego sus librerias para conectar: 
```bash
sudo apt-get install libmysqld-dev 
```
Una vez que ya tenemos instalado la Base de Datos podemos comenzar a jugar.
```bash
rails new ferreteria -d mysql
```
si vemos tenemos algo nuevo, si el "-d mysql" lo que hace es generar un fichero que se llama "database.yml" que se encuentra dentro del directorio config/, y nos agrega la gema "mysql2".

he dicho talvez un par de cosas que no he explicado como por ejemplo gema.

las gemas vienen a ser las librerias si así lo quieres llamar, y las que vayas a utilizar en tu proyecto estan el fichero Gemfile, el cual trae incorporadas gemas una de ellas es la gema de base de datos, que en este caso sera mysql o "gem mysql2".
Que nos falta para poder tirar lineas de codigo y poder ver el framework en acción ?
2 cosas crear un usuario en mysql y segundo configurar el proyecto con dicho usuario, ya que no vamos a trabajar con el usuario root

```sql
GRANT ALL ON ferreteria_development.* TO ferreteria@localhost IDENTIFIED BY 'ferreteria+123';
GRANT ALL ON ferreteria_test.* TO ferreteria@localhost IDENTIFIED BY 'ferreteria+123';
```
Lo que acabamos de hacer es crear el usuario y darle permiso para manipular dos base de datos 'ferreteria_development' y 'ferreteria_test', estas bases de datos existen aun pero las crearemos o mas bien lo hara rails.

entonces abriremos una consola e iremos al directorio donde creamos el proyecto. Una vez dentro de este mismo comenzaremos.
```bash
rake db:create
```
que acabamos de hacer y por que la consola no dijo nada??
Bueno la respuesta es acabamos de crear las dos bases de datos que mas arriba le dijimos al usuario ferreteria podia manejar, si no me hagan
```bash
mysql -uferreteria -pferreteria+123
```
```sql
show databases;
```
bien ahora que comprobamos esto nos vamos a poner a trabajar 

lo que primeramente vamos a hacer es explicar es que usaremos bastante dos comandos rails y rake, en el caso de rails usaremos 4 (bueno 5 ya usamos el primero que es new):

- rails generate o rails g
- rails  console o rails c
- rails server o rails s
- rails dbconsole o rails db

El primero lo que hace es generar ficheros tales como assets, model, controller,helper, migration, scaffold (este no es un fichero), etc
El segundo llama a la consola de ruby para manejar las clases del proyecto.
Rails s como ya lo vimos lo que hace es hacer partir el server de rails que por defecto corre en el puerto 3000
y rails db lo que hace es conectarse con la base de datos que estemos trabajando si no le damos otro argumento corre con la base de datos development.

Digamos que tenemos una ferreteria y necesitamos que solamente nos vea productos y estos que tengan una boleta asociada,por lo que tendriamos de momento dos tablas,
la primera productos que tendria la cantidad, un precio,un nombre. 
y las boletas tendrian fecha, n productos y un numero de boleta.

Lo que haremos es crear el MVC con un CRUD (Create Read Update Delete), para los dos modelos

```bash
rails g scaffold Producto nombre:string cantidad:integer precio:float
```
que acabamos de hacer????? y por que nos arrojo tantas lineas, bueno lo que esto nos crea es el modelo, el controlador, la vista bajo la logica DRY (don't repet yourself) y mas importante nos crea la migración. Las migraciones son la herramienta que crean las tablas y de esta manera nos da la flexibilidad de cambiar el motor de base de datos ya que la migración depende de la gema y del database.yml. encontraremos el fichero de migración en db/migrate/aaaammddhhcreate_table.rb (el nombre table varia segun lo que coloquemos).

```bash
rake db:migrate
```
Lo que acabamos de hacer es migrar la tabla o crearla.
```bash
rails db
```
lo que hacemos aqui es ver la base de datos (si es lo mismo que un mysql -uferreteria -p) pero solo toma la ferreteria_development, entonces si le damos un 
show tables solo nos mostrara una tabla que se llama productos, espera un momento estaba casi seguro que cuando escribí el scaffold le dije producto en signular no en plural. Pues esto se debe a que rails trabaja con ORM (mapeo objeto relacional, claro traduje el nombre), ya hablaremos de ORM.
```sql
describe productos;
```

```bash
rails g scaffold Boleta
```









