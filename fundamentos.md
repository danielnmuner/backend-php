## Fundamentos PHP

- [x] [Instalacion](#instalacion)


### Instalacion

PHP `Hypertext Preprocessor` es un preprocesador de **HTML**. practicamente podemos hacer lo que necesitemos con **PHP**

- Codigo en el Servidor **API**
- Comandos para la termianal
- Aplicaciones de Escritorio con la libreria **PHK**
- Es un lenguaje de alto nivel
- Es de tipado debil
- Es un lenguaje interpretado

> **"PHP puede ser utilizado para cualquier cosa, pero solo porque puedas escribir algo con PHP no significa que debas hacerlo"** Rasmus Lerdof

**Intalacion Windows**
1. Descargamos [XAMPP](https://www.apachefriends.org/es/index.html)
2. **XAMPP** usualmente corre en los puertos **443** y **80** si tenemos un .log como:

```sh
Error: Apache shutdown unexpectedly.
This may be due to a blocked port, missing dependencies, 
```
Abrimos el archivo `httpd.conf` y modificamos puerto `80` por `8080` y el `443` por `4433`. Asi no se ejecutara el mismo error.


**Instalacion Linux**

1. Añadir repo de **PHP** `sudo add-apt-repository ppa:ondej/php`
2. Actilizamos repo de Ubuntu `sudo apt update`
3. Cargamos paquetes de Ubuntu `sudo apt upgrade`
4. Instalar **PHP** `sudo apt install php8.0 apache2`
5. Installamos otra version de **PHP**(Lo podemos hacer con la versiones que queramos) `sudo apt install php7.0`
6. Listamos las versiones instaladas de **PHP** `sudo dpkg --get-selections | grep php`
7. Verificamos la version de **PHP** `php8.0 --version`
8. Habilitar modulo `sudo a2enmod php7.4` o deshabilitar `sudo a2dismod php7.4` alguna version de **PHP**.
9. Creamos un archivo **PHP** `touch index.php`
10. Escribimos sobre el archivo:
```php
<?php
phpinfo();
```
11. Abrimos el localhost desde el navegador `localhost` asi veremos la informacion general del modulo **PHP** habilitado.
12. Debemos modificar el archivo **php.ini** `sudo nano /etc/php/8.0/apache2/php.ini` buscamos `display_error=Off` y lo modificamos a `display_error=On`.
13. Si algo no funciona podemos ademas installar `sudo apt install libapache2-mod-php8.0`


