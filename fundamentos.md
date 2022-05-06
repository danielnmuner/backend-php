## Fundamentos PHP

![php](https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/PHP-logo.svg/1200px-PHP-logo.svg.png)

- [x] [Instalacion](#instalacion)
- [x] [Cómo ejecutar tus archivos PHP](#cómo-ejecutar-tus-archivos-php)
- [x] [Sintaxis básica de PHP](#sintaxis-básica-de-php)
- [x] [Debugging y comentarios](#debugging-y-comentarios)
- [x] [Variables y constantes](#variables-y-constantes)

### Tipos de Datos
- [x] [Tipos de datos](#tipos-de-datos)


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

- Abrir la consola interactiva de **PHP** desde la terminal `php -a` y `ctrl + C` para salir de la consola.

**Agunos comandos de PHP**  

- `-a` Se ejecuta interactivamente.
- `-c` <ruta>|<fichero> Busca el fichero php.ini en este directorio.
- `-n` No se usará el fichero php.ini.
- `-d foo[=bar]` Define la entrada INI de foo con el valor ‘bar’
- `-e` Generate información extendida para el depurador/perfilador.
- `-f <fichero>` Analiza y ejecuta el <fichero>.
- `-h` Esta ayuda.
- `-i` Información de PHP.
- `-l` Solamente revisa la sintáxis (lint).
- `-m` Muestra lo compilado en módulos.
- `-r <code>` Ejecuta el <código> PHP sin utilizar las etiquetas del script

 ### Cómo ejecutar tus archivos PHP
  
**Windows**  
  
- **Tip** el path `C:/xampp/htdocs` es importante por que todo lo que este en esta carpeta sera automaticamente alojado(__Hosteado__) en el navegador y que podemos visualizar en nuestro `localhost:8080` o puerto que hayamos configurado.  
 
Teniendo en cuenta lo anterior en esa carpeta **htdocs** vamos crear nuestro archivo `index.php` para que se ejecute automaticamente cuando iniciemos XAMPP.   
  
  
**Linux**
1. Ubicarnos en path `/var/www/html`.
2. Modificamos permisos para poder escribir sobre la carpeta `html` esto se hace asi: `sudo chmod 777 html`
3. Creamos archivo `touch index.php` y añadimos algo de codigo:
```php
<?php
echo "Hola Mundo"
```
4. Iniciamos apache con Ubuntu nativo `sudo systemctl start apache2` 
5. Iniciamos apache con WSL `sudo /etc/init.d/apache2 start` 🚀

![StandingOvationGIF](https://user-images.githubusercontent.com/60556632/167160269-94d00366-2250-436d-9370-48dd9f7ce7a9.gif)

### Sintaxis básica de PHP

Son basicamente reglas que se deben seguir para determinado lenguaje. Ahora empezemos con **PHP**.

```php

<?php
/*🙄Etiqueta de Apertura, tambien es importante 
el punto y coma ";" al final de cada linea.
*/

/*Imprimir en pantalla*/
echo "Hola, World Ich bin haciendolo great! \n";

/*Declaracion de Variables*/
$nombre = "Daniel";
$apellido = " Diaz";

/*Concatenar variables a texto
Opcion # 1
*/
echo "Yo me llamo ".$nombre.$apellido."\n";

/*Opcion # 2, siempre usando comillas dobles*/
echo "Yo me llamo $nombre $apellido \n";
/*
Operacion Numerica*/
echo "El resultado de 2 X 12 es: ".(2*12)."\n";

/*Etiqueta de Cierre - solo se usa si combinamos PHP con otro lenguaje como HTML*/
?>
```
 
### Debugging y comentarios

El profe aplica el concepto de debugging a una lista que luce mas como un diccionario. Debugging seria sinonimo de inspeccionar y eso es lo que hacemos con la variable `$personas`.  
 ```PHP
<?php
/*Creamos un arreglo en PHP*/
$personas = [
	"Andrew" => 22,
	"Mr. Michi" => 15,
	"Albert" => 65
];

/*Inspeccionar el contenido de una variable*/
var_dump($personas);

/*Es igual que var_dump()*/
print_r($personas);

echo "\n";
?>
```
Output **var_dump**($personas):
```php
array(3) { 
 ["Andrew"]=> int(22) 
 ["Mr. Michi"]=> int(15) 
 ["Albert"]=> int(65) 
 }
``` 
Output **print_r**($personas):
```php
Array ( 
 [Andrew] => 22 
 [Mr. Michi] => 15 
 [Albert] => 65 
 )
``` 
### Variables y constantes
	
Una **variable** es un caja `Espacio en Memoria` donde podemos guardar cualquier cosa `Tipos de Datos` que puede cambiar en el tiempo. 

```php
<?php
#Las variables van en minuscula

$num_a = 8;
$num_a = 4;

echo $num_a + $num_b;
#Output: 12
```
	
Una **constante** es una caja con cualquier cosa pero no cambia en el tiempo. A diferencia de una variable se escribe en **MAYUSC** y no lleva signo **$**.
 
```php
#Definimos una constante, siempre en Mayusculas
define("NUMERO_PI",3.14);

echo NUMERO_PI;
```	

### Tipos de Datos
---
**PHP** es de tipado debil luego no debemos indicar que tipo de dato estamos declarando.🧐.
**Integer**:
```php
<?php
$num =  25;
var_dump($num);
#🙃Out: int(25)
```
**String**:
```php
<?php
$num =  "2500";
var_dump($num);
#🙃Out: string(2) "25"
```

**Integer + String(Number)**:
```php
<?php
$num_a =  "25";
$num_b = 25;
$num_c = $num_a + $num_b;
var_dump($num_c);
#🙃Out: int(50)
```
**Integer + String**:
```php
<?php
$papas = "10 papas en el costal";
$cuantas_papas_hay = $papas + 5;

echo $cuantas_papas_hay;

/*🙃Out: Warning: A non-numeric value encountered in C:\xampp\htdocs\index.php on line 3
15*/ Basicamente toma unicamente el 10 y lo suma a 5.
El tipado es demasiado debil 😂, anyway es una mala pratica.
```

### Casting de Datos

Es cuando cambiamos el tipo de dato de una **variable** o **constante** previamente declarada. 

|Sintax|
| --- |
|`(int)` |
|`(bool)` |
|`(float)` |
|`(string)` |
|`(array)` |
|`(object)` |

Algunos de casting en **PHP**:

|str-int | float-int |
|--- | --- |
|```php
<?php
#Casting str-int
$num = "5";
$num = (int)$num;
var_dump($num);
#🙃Out: int(5)
``` | ```php
<?php
#Casting de float a int
$dias = 5.89;
$dias =(int)5.89;
var_dump($dias);
#🙃Out: int(5)
``` |


