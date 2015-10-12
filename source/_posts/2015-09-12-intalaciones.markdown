---
layout: post
title: "Intalaciones"
date: 2015-09-12 18:20:59 -0300
comments: true
categories: mysql postgresql ruby rails git apache2 composer
---

Bueno hoy estaremos viendo como instalar java, ruby, php ,mysql, postgresql,etc. Todo esto obviamente en un ambiente de verdad (algún Ubuntu o derivado).

Vamos a instalar primeramente Java ya que lo vamos a necesitar para casi todo buen IDE,

```bash
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```
Para ser sinceros podemos usar otras versiones de java como por ejemplo el openjdk que se instala

```bash
sudo apt-get insta openjdk-7-jdk
```
cual es mejor? la verdad son versiones distintas pero a mi me gusta mas la 8 de oracle.

Ya tenemos instaldo java ahora a instalar nuestro IDE, en este caso descargaremos el netbeans en su ultima version.

```bash
wget http://download.netbeans.org/netbeans/8.0.2/final/bundles/netbeans-8.0.2-linux.sh
```
Una vez que esté listo le daremos permisos para poder correrlo y luego a instalar.

```bash
chmod +x netbeans-8.0.2-linux.shnetbeans-8.0.2-linux.sh
./netbeans-8.0.2-linux.sh
```

Y con eso tenemos instalado el IDE correctamente :D   


Ya repasando lo que hicimos fue primero instalar el dichoso y famoso lenguaje java ya sea oracle 8 o openjdk-7. Una vez que teniamos ya instalado el lenguaje, luego lo que haremos es descargar el ide (en este caso lo hicimos con wget solo para demostrar conocimiento de terminal). le dimos permisos al .deb   y lo instalamos, creo que la palabra que iria como anillo al dedo es TRIVIAL.


Ya tenemos el IDE ahora veremos Ruby y luego rails :D

##Ruby

Lo primero es instalar ciertas librerias  y otras dependencias necesarias a futuro.

```bash
sudo apt-get install build-essential libssl-dev libyaml-dev libreadline-dev openssl curl git-core zlib1g-dev bison libxml2-dev libxslt1-dev libcurl4-openssl-dev
```

Crearemo un directorio y luego en ese mismo directorio vamos a descargar la versión 2.2 de ruby.

```bash
mkdir ~/ruby
cd ~/ruby
wget http://cache.ruby-lang.org/pub/ruby/ruby-2.2.2.zip
unzip ruby-2.2.2.zip
cd ruby-2.2.2
```
Que xuxa hicimos en esas 5 lineas??? bueno en la primera creamos un directorio(leasé bien no dice carpeta es directorio) en el home y luego entramos, una vez que estamos dentro del directorio descargamos con wget si nos da error ese comando instalamos el wget. Con el cuarto y último comando lo que hicimos fue descomprimir el zip de ruby y con el quinto obviamente ingresamos al directorio que contenia el archivo zip.

Ahora haremos correr el script "configure", igual se demora un tanto pero podemos esperar si igual tenemos tiempo i weas :P
```bash
./configure
```

Ejecutaremos la utilidad Make, que utilizara el Makefile para generar el programa ejecutable.(creo que esto demora mas que el anterior)

```bash
make
```

Lo que necesitamos ahora es copiar los binarios compilados en el directorio /usr/local/bin/,y para esto lo tiraremos con sudo para darle más "permisos".

```bash
sudo make install
```
WALAAAAAAA esta tenemos ruby 2.2 i weas.


Ya si quieren puden borrar el directorio ruby y su contendido

```bash
cd
rm -rf ~/ruby
```
y fuiste directorio ruby y contendido.

##Rails

Que nos falta ?
Si instalar rails, y no cualquiera si no que 4.2 asi que correremos:

```bash
sudo gem install --no-rdoc --no-ri rails
```

se demorara un tanto asi que esperemos y listo lo unico que nos falta es el motor de base de datos y su libreria de conección con rails.



##Laravel

ya ahora vamos a la parte donde se instalara php, laravel y composer.

```bash
sudo apt-get install php5-curl php5-mcrypt php5-cli
sudo php5enmod mcrypt
```

listo ya tenemos el dichoso php, asi que pasamos al composer, quien es el manejador de dependencias php


```bash
wget -O - https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```
Los paquetes/librerías instaladas de esta forma son globales para nuestro usuario.

```bash
composer global require "laravel/installer=~1.1"
echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >> ~/.bashrc
```


# GIT

Primero comenzaremos con la instalación de git por lo que abrimos una terminal e ingresamos

```bash
sudo apt-get install git
```

una vez instalado pasamos a configurar el usuario global.

```bash
git config --global user.name "Fernando Rubilar Z"
git config --global user.email frubilar@icci.cl
```

Con este comando ya estamos READY


y ahora a trabajar eso es todo con git por hoy :D
