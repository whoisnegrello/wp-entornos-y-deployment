# Curso de Entornos de Desarrollo y Deployment para WordPress

## Comando para otorgar permisos a XAMPP para manipular la carpeta de contenidos de WordPress y al archivo .htaccess

    chmod -R 0777 ./tu-ruta/

El comando `chmod` permite modificar los permisos de los archivos a los que se les aplique el comando.

La bandera `-R` es para que aplique dichos permisos recursivamente a todos los directorios y archivos desde la raíz.

Los permisos `0777` le otorgan a todos los usuarios la capacidad de leer, escribir y ejecuar dichos archivos.

El último parámetro es la carpeta en donde está instalado WordPress.

## Definición necesario para habilitar la instalación de plugins automática en XAMPP

    define('FS_METHOD', 'direct');

Esta definición se debe incorporar en el archivo `wp-config.php` dentro de la carpeta raíz de la instalación de WordPress.

## Comando para instalar wp-env

    npm -g i @wordpress/env

Este comando instala de forma global el paquete para poder generar servidores para WordPress en todo el entorno.

Recordar que es necesario instalar **Docker** previamente para que funcione ([Windows](https://docs.docker.com/docker-for-windows/install/), [Mac](https://docs.docker.com/docker-for-mac/install/), [Linux](https://docs.docker.com/v17.12/install/linux/docker-ce/ubuntu/#install-using-the-convenience-script)).

Podés ver la documentación completa del paquete [aquí](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-env/).

## Comando para exportar la base de datos con WP-CLI

Para realizar este proceso, es necesario hacerlo desde una terminal conectada a la maquina que está virtualizando el sitio web y que esta máquina tenga instalado WP-CLI.

Cómo vimos en clase, para poder hacerlo desde Local, es necesario hacer clic derecho sobre el sitio y presionar la opción "Abrir terminal del sitio".

Cuando la abramos, veremos la versión de WP-CLI y sabremos que estamos en condiciones de comenzar a utilizarlo.

Para otras instalaciones con módulos nativos puede servir instalar WP-CLI de forma global en el sistema.

El comando para poder exportar la base de datos con el cambio de URL es:

    wp search-replace "url_actual" "url_nueva" --export="./nombre-archivo.sql"

Este comando exportará la base de datos dentro de la carpeta `public` del proyecto en Local.

## Cómo habilitar phpMyAdmin para acceso remoto en XAMPP-VM

    <Directory "/opt/lampp/phpmyadmin">
        ...
        Require all granted
        ...

Para habilitar el acceso remoto a phpMyAdmin utilizando XAMPP-VM se debe modificar el archivo `/opt/lampp/etc/extra/httpd-xampp.conf` de esta manera.

Luego se deben reiniciar los servicios.
