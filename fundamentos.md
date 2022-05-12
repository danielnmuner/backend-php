## Fundamentos PHP

![php](https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/PHP-logo.svg/1200px-PHP-logo.svg.png)

- [x] [Instalacion](#instalacion)
- [x] [Cómo ejecutar tus archivos PHP](#cómo-ejecutar-tus-archivos-php)
- [x] [Sintaxis básica de PHP](#sintaxis-básica-de-php)
- [x] [Debugging y comentarios](#debugging-y-comentarios)
- [x] [Variables y constantes](#variables-y-constantes)

### Tipos de Datos
- [x] [Tipos de datos](#tipos-de-datos)

### Operadores en PHP
- [x] [Operadores Logicos](#operadores-logicos)
- [x] [Operadores aritméticos](#operadores-aritméticos)
- [x] [Operadores relacionales](#operadores-relacionales)
- [x] [Otros operadores](#otros-operadores)
- [x] [Tu primer programa](#tu-primer-programa)

### Arreglos
- [x] [Que son los arreglos](#que-son-los-arreglos)
- [x] [Manipulando arreglos](#manipulando-arreglos)	

### Condicionales
- [x] [Decisiones con if y else](#decisiones-con-if-y-else)
- [x] [Switch](#switch)

### Bucles
- [x] [Ciclo while](#ciclo-while)
- [x] [Do while](#do-while)
- [x] [Ciclo for](#ciclo-for) 
- [x] [Ciclo foreach](#ciclo-foreach)

### Functions
- [x] [Funciones](#funciones)

## Integracion de PHP con HTML
- [x] [Introduccion](#introduccion)
- [x] [PHP como preprocesador de HTML](#php-como-preprocesador-de-html) 

### Manejo de formularios
- [x] [Cómo obtener una solicitud al servidor con PHP](#cómo-obtener-una-solicitud-al-servidor-con-php)
- [x] [Envío de un formulario a través de GET](#envío-de-un-formulario-a-través-de-get) 
- [x] [Proyecto](#proyecto)

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
6. Ejecutamos php desde localhost `php -S localhost:8080` en el puerto que deseemos. 

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
---
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

 ```php
<?php
#Casting str-int
$num = "5";
$num = (int)$num;
var_dump($num);
#🙃Out: int(5)
``` 

```php
<?php
#Casting de float a int
$dias = 5.89;
$dias =(int)5.89;
var_dump($dias);
#🙃Out: int(5)
``` 

### Operadores Logicos

- Union `$str_a and $str_a` alternativa `$str_a && $str_a`
- Disyunsion `$str_a or $str_a` alternativa `$str_a || $str_a`
- Negacion **`!`** como en `!$str_a and $str_a`.

```php
<?php
$michis_felinos = true;
$michis_4_patas = true;
$michis_vuelan = false;
$michis_leen = false;

var_dump($michis_felinos && $michis_leen);
#🙃Out: bool(false)

var_dump(!$michis_felinos && $michis_4_patas);
#🙃Out: bool(false)
```
### Operadores aritméticos
---
|Operador	|Función|
| --- | --- |
|+	|**Adición**: Suma dos o más números |
|-	|**Sustracción**: Resta dos o más números|
|*	|**Multiplicación**: Multiplica dos o más números|
|/	|**División**: Divide y regresa el cociente|
|%	|**Módulo**: Divide y regresa el residuo|
|**	|**Potenciación**: Eleva un número al exponente dato|
|+	|**Identidad**: Convierte un **str** a **int**|

```php
<?php
#Operadores Aritmeticos
$var_a = "5";
$var_b = 6;

#Casteamos var_a de str-int
echo +$var_a;
#🙃Out: 5

echo "A EXP B es: " . ($var_a ** $var_b);
#🙃Out: A EXP B es: 15625

echo $var_b % $var_a;
#🙃Out: 1
```

### Operadores relacionales
---
```php
<?php
#Declaracion de variables en PHP
$var_a = 5.5;
$var_b = "5.5";
$var_c = 2;
$var_d = 10;

#Operador de igualdad
var_dump($var_a == $var_b);
#Out: 🙃 bool(true)

/*El operador identico arroja false
debido a que var_b es de tipo str
*/
var_dump($var_a === $var_b);
#Out: 🙃 bool(false)

/*Operador de diferente
En este caso no importa el tipo
*/
var_dump($var_a != $var_b);
#Out: 🙃 bool(false)

/*Operador de no identico
En este caso si importa el tipo
*/
var_dump($var_a !== $var_b);
#Out: 🙃 bool(true)

#Otros Basicos
var_dump($var_a < $var_d); #bool(true)
var_dump($var_a > $var_d); #boo(false)
var_dump($var_a <= $var_d); #bool(true)
var_dump($var_a >= $var_d); #boo(false)

#Operador de Nave espacial <=>
#Menor-Mayor
echo $var_a <=> $var_d;
#Out: 🙃 -1

#Mayor-Menor
echo $var_d <=> $var_a;
#Out: 🙃 1

#Iguales
echo $var_a <=> $var_b;
#Out: 🙃 0

/*Operador de fusion de nulo
Si la "var_e" no esta definida entonces
se usa "var_b" en vez de arrojar error.
*/
echo $var_e ?? $var_b;
#Out: 🙃 5.5
```

### Otros operadores

```php
<?php
/*Operador de asignacion "="
PHP primero resuelve la asignacion
incluso si hay una doble igualdad
*/
$age_a = ($age_b = 18) + 10;

echo $age_a;
echo $age_b;
#🙃Out: 28,18

/*Operador de incremento*/
$contador = 1;
$contador = $contador + 10;
#$contador += 10;
#$contador ++; Solo incrementa en "1"

var_dump($contador); 
#🙃Out:int(11)

/*Operador de decremento*/
$contador = 1;
$contador = $contador - 10;
#$contador -= 10;
#$contador --; Solo decrementa en "1"

var_dump($contador); 
#🙃Out:int(-9)

/*Operador de concatenacion ".", ".="*/
$nombre = "Nicholas";
$nombre = $nombre . " Weir";
#$nombre .=" Weir";

var_dump($nombre);
#🙃Out: "Nicholas Weir"
```

### Precedencia de operadores
---
Nos indica que ocurre primero y que despues. PHP tiene una [tabla](https://www.php.net/manual/es/language.operators.precedence.php) de precedencia la cual indica para cada operacion si es de izquierda o de derecha. Basicamente de **izquierda** quiere decir que primero se signa y luego se resulve la operacion:

```php
#Usaremos el operador "and" el cual es de precedencia izquierda.
$michis_4_patas = true;
$michis_leen = false;
$resultado = $michis_4_patas and $michis_leen;

#PHP asigna solo $resultado = $michis_4_patas
echo $resultado; #🙃Out: true

/*Para operar y luego asignar sin importar la 
presedencia usamos parentesis "()" para forzar 
la operacion sobre la asignacion.
*/

$resultado = ($michis_4_patas and $michis_leen;
echo $resultado; #🙃Out: false
```
- Aqui hay otro ejemplo que se podria resolver usando **`()`** o colocando el operador antes de la variable como el caso de **`++`**. 

```php
<?php

/*En este caso primero asigna "counter" a
"n_counter" y despues incrementa counter
*/
$counter = 0;
$n_counter = $counter++;
#n_counter = ++$counter;

var_dump($n_counter , $counter);
#🙃Out: int(0),int(1)
```

### Tu primer programa
---

```php
<?php
#Solicitar info al usuario ✌️
$seconds = readline("Enter time in seconds: ");
$seconds = 4460;

/*Convertimos los segundos a horas
hacemos el casteo y tenemos en cuenta
la presedencia por eso debemos usar "()".
*/
$hour = (int) ($seconds / 3600);
#Calculamos el reciduo
#Y asi conseguimos los segundos
$seconds = $seconds % 3600;

#Calulamos los minutos por cada 60s
#Y recalculamos los segundos
$minutes = (int) ($seconds / 60);
$seconds = (int) ($seconds % 60); 

echo "HH: $hour MM: $minutes SS: $seconds";

#🙃Out: HH: 1 MM: 14 SS: 20
```

##Arreglos, Funciones y Estructuras de control

### Que son los arreglos
---
Es una caja donde podemos guardar varios tipos de objetos y para acceder a cada uno de ellos solo debemos utilizar el subindice. 

```php
<?php
#Declaramos un arreglo en PHP
$ages = [20,18,40];
#$ages[1] podemos acceder al subindice [1]
echo "age[1]: $ages[1]";

#Declaramos un array de otra forma.
$age = array(20,18,40);
echo "age[1]: $age[1]";

#🙃Out: age[1]: 18
```

### Arreglos asociativos

El aquel que me permite reemplazar los subindices por valores predeterminados. Es muy similar a JSON por que en realidad asi nos cominucaremos a traves de HTTP/S

```php
<?php
$ages = array(
"Adrian" => 18,
"Carl" => 25,
"Newman" => 15,
);
#Accedemos al valor a partor de una palabra clave
var_dump($ages["Adrian"]);

#Crear un super array() o super dic
$people = array(
"Andrew" => array(
    "age" => 20,
    "language"=>"Spanish"
),
"Carl" => array(
    "age" => 23,
    "language"=>"English"
),
"Boyd" => array(
    "age" => 27,
    "language"=>"German"
),
);
echo $people["Andrew"]["language"];
#🙃Out: Spanish
?>
```
### Manipulando arreglos
---
**PHP** tiene muchas [funciones](https://www.php.net/manual/es/ref.array.php) para manipular **arreglos** apesar de ser muchas a continuacion nos fijaremos en algunas comunes.
	
```php
<?php

#Funciones:


#count: Indica la cantidad de elementos.
$ages = [18,22,40,34];
echo count($ages);
#🙃Out: 4

#array_push: Añade un objeto al final del arreglo
array_push($ages,13);
var_dump($ages);
/*🙃Out: array(5) { 
    [0]=> int(18) 
    [1]=> int(22) 
    [2]=> int(40) 
    [3]=> int(34) 
    [4]=> int(13) }
*/

#is_array: Valida si es un arreglo
echo is_array($ages);
#🙃Out: 1/true

/*explode: Separa un str a traves de un sep
primero indicamos el separador luego el arreglo*/

$fruitlist = "strawberry,berry,apple";
$fruit_list = explode(",",$fruitlist);
var_dump($fruit_list);

/*🙃Out: array(3) { 
    [0]=> string(10) "strawberry" 
    [1]=> string(5) "berry" 
    [2]=> string(5) "apple" 
}*/

/*implode: Convierte un arreglo en un str
separado por un caracter.*/
$implode_list = implode(",",$fruit_list);
var_dump($implode_list);
#🙃Out: "strawberry,berry,apple"	
```
	
### Decisiones con if y else
El tipo de dato usado para tomar decisiones son los valores booleanos `true/false`.

```php
<?php
#Declaramos un variable
$available_seats = 4;

#Usamos un operador relacional para obtener
#una respuesta de tipo booleana.

if ($available_seats > 4){
    echo "You can see the film";
}
elseif ($available_seats == 4){
    echo "Cool you can invite 3 more";
}
else {
    echo "Sorry, but you can't see the film";
}
#🙃Out: You can see the film
?>
```
### switch
![image](https://user-images.githubusercontent.com/60556632/167228992-fc5c7c48-49e4-4d0d-b03f-e7a07960afea.png)

```php
<?php
$age_michi = 11;
#Variable a evaluar
switch ($age_michi) {
    case 11: #Case 11 esta vacio entonces salta a caso 10
    case 10:
        #Codigo caso 1
        echo "Michi is 10 or 11 years";
        break;
    case 12:
        #Codigo caso 2
        echo "Michi is 12 years";
        break;
    case 13:
        #Codigo caso 3
        echo "Michi is 13 years";
        break;
    default:
        #Codigo default
        echo "Michi is young";
}
?>	
```
**Reto-Condicionales**
	
```php
<?php
/*Twitch es una plataforma para realizar
transmisiones en vivo y tambien recibir 
donaciones de los usuarios. Para poder retirar
las donaciones debe haber un minimo de $100 USD
*/

$donations = 98;
if ($donations >= 100) {
    echo "Hey!, You've met $100 USD";
}
else {
    echo "Hold on!,No $100 USD yet";
}
?>
#🙃Out: Hold on!,No $100 USD yet	
```
	
### Ciclo while
---
```php
<?php
#Contador sera el punto de referencia
$contador = 0;
while($contador<=100) {
    #Se imprimiran 100 veces nuestro mensaje
    echo "Este curso esta increible \n";
    $contador ++;
}	
```

### Do While
---
```php
<?php
/*Ejecuta Do al menos usa vez, o tantes veces
como se cumpla la condicion dada.*/
$usernames = ["Nickashh","Muhamad","Strovitchk"];
do {  
    $username = readline("Ingresa tu Nickname: ");
/*in_array: (objeto,array)    
#Ejecuta do siempre que el username ente
en el arreglo de usernames. Este ejemplo es util
para evitar usuarios duplicados pues no admite
aquellos que ya existen. 
*/
}while (in_array($username,$usernames));
```
### Ciclo for

```php
<?php

#1. Inicializamos contador "i"
#2. Establecemos una condicion con "i"
#3. Incrementamos contador "i++"

for ($i=0; $i <10 ; $i++) { 
    /*Se inprime en pantalla hasta
    que se cumple la condicion del paso 2.
    */
    echo $i;
}
#🙃Out:0123456789

/*Agregar mas variables a "for" sin afectar
la condicion inicial del contador.
*/

for($i=0,$j=0;$i<10;$i++,$j+=2){
    echo "i = $i j= $j"."\n";
}
/*🙃Out:  
i = 0 j= 0 
i = 1 j= 2 
i = 2 j= 4 
i = 3 j= 6 
i = 4 j= 8 
i = 5 j= 10 
i = 6 j= 12 
i = 7 j= 14 
i = 8 j= 16 
i = 9 j= 18
*/
```
### Ciclo foreach
	
Nos permite recorrer iterables y realizar operaciones. 
```php
#Sintaxis 
foreach ($iterable as $valor) {
   echo $valor;
}

foreach ($iterable as $llave => $valor) {
   echo $valor, $llave;
}
```

```php
<?php
$cafe_store = array(
    "Americano" => 20,
    "Latte" => 25,
    "Capuccino" => 27.5,
    "Mocca" => 24
);

foreach ($cafe_store as $price) {
    echo "El cafe $$price USD";
}
/*🙃Out: 
El cafe $20 USD
El cafe $25 USD
El cafe $27.5 USD
El cafe $24 USD
*/

#$key => $valor
foreach ($cafe_store as $cafe => $price) {
    echo "El $cafe cuesta $$price USD";
}
/*🙃Out: 
El Americano cuesta $20 USD
El Latte cuesta $25 USD
El Capuccino cuesta $27.5 USD
El Mocca cuesta $24 USD
*/
?>
```
- **Break** y **Continue** son usadas en los bucles para salir a determinado momento o continuar el bucle realizando saltos determinados.

```php
<?php
$cafe_store = array(
    "Americano" => 20,
    "Latte" => 25,
    "Capuccino" => 27.5,
    "Mocca" => 24,
    "Recalentado"=>10
);

#Break

foreach ($cafe_store as $cafe => $price) {

    echo "Actualemente encontre al cafe $cafe";
    if ($cafe ==  "Latte"){
        echo "Encontramos al cafe $cafe";
        break;
    }
}
/*🙃Out: 
Actualemente encontre al cafe Americano
Actualemente encontre al cafe Latte
Encontramos al cafe Latte
*/

#Continue
foreach ($cafe_store as $cafe => $price) { 
    if ($cafe ==  "Recalentado"){
        continue;
    }
    echo "Tenemos cafe $cafe";

}
/*🙃Out:
Tenemos cafe Americano
Tenemos cafe Latte
Tenemos cafe Capuccino
Tenemos cafe Mocca
*/	
```
- **Fibonacci** en PHP

```php
<?php
#Fibonacci con ciclo for
$num_store = 8;
$anterior = 0;
$actual= 1;

for ($i=2; $i <= $num_store ; $i++) { 
    $temporal = $actual;
    $actual += $anterior;
    $anterior = $temporal;
}
echo "Formas de llegar $actual";
#fn = (fn-1) + (fn-2)
```
### Funciones
---
Permiten ejecutar codigo varias veces, solo necesita los datos para procesarlos y entregar una salida.

```php
<?php

function get_pokemon() {

#Asignamos un valor aleatorio de 1 a 5
$random_num = rand(1,5);
#Opciones de 1 a 3 con switch + caso default
    switch ($random_num) {
        case 1:
            echo "Pikachu";
            break;
        case 2:
            echo "Charmander";
            break;
        case 3:
            echo "Burbasor";
            break;
#Si 4 o 5 entonces aplica caso default.
        default:
            echo "I'm sorry!";
    }
}
#Llamamos la funcion varias veces🙂
for (i=0;i<=10;i++)
    get_pokemon();
}
```
### Parámetros en las funciones
---
En este punto le estamos entregando argumentos a la funcion para que sean procesados por la funcion. 

```php
<?php
#Pasamos el arg $platzi_rank a la funcion
function is_legend($platzi_rank)
{
    if($platzi_rank >= 20000){
        echo "!Eres estudiante Legend!";
    }
    else {
        echo "Lo sentimos, aun no alcanzas el nivel!";
    }
}
#Solicitamos al usuario el score de platzi_rank
$score = (int) readline("Cual es tu platzi rank");
is_legend($socre);
```

### Profundicemos en los parametros
---
```php
<?php
/*Asignamos valores por defecto a las variables.
🧐Este valor solo se toma en cuenta si el usuario
no lo indico los argumentos solicitados */
function sum($a = 0,$b = 0)
{
    echo "La suma de $a + $b es: ".$a+$b;
}
#No hay error gracias a los valores por default
sum();
```

- Quick Topic **Array Unpacking**: Es un metodo para concatenar arreglos en **PHP**. 

```php
<?php
#Declaramos dos arrays
$array_a = [1,2,3];
$array_b = [4,5,6];

#Concatemanos arrays usando arrayunpaking method
$concat_result = [...$array_a, ...$array_b];
var_dump($concat_result);
/*🙃Out: Arrays concatenados
array(6) { 
    [0]=> int(1) 
    [1]=> int(2) 
    [2]=> int(3) 
    [3]=> int(4) 
    [4]=> int(5) 
    [5]=> int(6) 
}
*/
```
- Tambien es util para entregar argumentos a una funcion en forma de arreglo. 

```php
<?php

#Funcion suma que requiere dos argumentos.
function sum ($a=0,$b=0){
#Respuesta de la funcion.
    echo "La suma de $a + $b es: ".$a+$b;
}
#Donde $num es un array con los valores $a y $b
$num = [10,100];

#Argumentos entregados a traves de unpacking
#Basicamente los "..." son la clave del metodo.
sum(...$num);
#🙃Out: La suma de 10 + 100 es: 110
```
- **Quick Topic** Paramentros dinamicos: Consiste que el numero de argumentos sea definido por el usuario y no por el programador, asi su tamaño sera dinamico. **Primero**:

```php
<?php
#Esto sucede cuando usamos array-unpacking
function sum (...$args){
#Internamente 1 y 2 se convierten en array([1,2])
#No importan la cantidad de args sum(1,2,3,4,etc)
    var_dump($args);
}
sum (1,2);
/*🙃Out: 
array(2) { 
    [0]=> int(1) 
    [1]=> int(2) 
}
*/
```
- Perfecto!, Ahora que tenemos un array-vector de n valores podemos operarlo dentro de nuestra funcion usando `foreach`. 
 
```php
<?php
function sum (...$args){
#$args = array([1,2,3,4,5]) -> Iterable😎 
#Variable que se sumara con cada valor del array
    $add = 0;
#Recorre el iterable.
    foreach ($args as $num){
        $add += $num;
    }
    echo "La suma total es: $add";
}
sum (1,2,3,4,5);
#🙃Out: La suma total es: 15
```
### Return
---
```php
<?php
#Return es una funcion. 
function freddy(){
#Switch combinado con "rand" 
#para elegir frases aleatorias
    $num = rand(1,4);
    $phrase = "";
    switch ($num) {
        case 1:
            $phrase = "Nunca pares de aprender";
            break;
        case 2:
            $phrase = "Las empresas no son familia";
            break;
        case 3:
            $phrase = "La tecnologia es el futuro";
            break;
        case 4:
            $phrase = "Amo PHP";
            break;
    }
#Return devuelve especificamente lo que le pedimos
#$phrase, variable que se reasigna en casa llamado
    return $phrase;
}
#Imprimimos en pantalla nuestra funcion. 
echo freddy();
```
### Operador de nave espacial
---
- **Quick Tipic** [usort](https://www.php.net/manual/es/function.usort.php): Es una funcion de **PHP** que ordena una lista  y se parece bastante a las de orden superior en Python donde un argumentos es el **array** y otro es otra funcion. **Sintax**: `usort(array &$array, callable $value_compare_func): bool`, donde **callable**: `callback(mixed $a, mixed $b): int`. 

- **Ejemplo**
```php
<?php
/*callback(mixed $a, mixed $b): int, que compara el primer valor
del arreglo con el segundo valor, asi usort va ordenando.
*/
function cmp($a, $b)
{
    if ($a == $b) {
        return 0;
    }
    return ($a < $b) ? -1 : 1;
}
#Arreglo a ordenar.
$a = array(3, 2, 5, 6, 1);

#Transformamos el arreglo "inplace".
usort($a, "cmp");

#Se imprime en pantalla ordenadamente.
foreach ($a as $clave => $valor) {
    echo "$clave: $valor\n";
}
/*🙃Out:
0: 1
1: 2
2: 3
3: 5
4: 6
*/
?>
```
> **Nota**: Obviamente, en este caso tan trivial, la función **sort()** sería más apropiada pero no lo es cuando se usa en arrays multidimencionales, en ese caso usamos usort.
	
```php
$frutas[0]["fruta"] = "uvas";
$frutas[1]["fruta"] = "limones";
$frutas[2]["fruta"] = "manzanas";
	
$array[0] = array('clave_a' => 'z', 'clave_b' => 'c');
$array[1] = array('clave_a' => 'x', 'clave_b' => 'b');
$array[2] = array('clave_a' => 'y', 'clave_b' => 'a');	
```
**End Quick Topic**
	
- **usort** es una funcion de Orden superior puesto que dentro de si misma lleva como argumento otra funcion. 
	
```php
<?php

$cafe_price = [12,34,1,13,23];

#Utilizamos una funcion anonima
usort($cafe_price,function($a,$b){
/*El operador Spaceship "<=>" retorna valores
entre -1 y 1 y esto es exactamente lo que utiliza
usort() para ordenar.
1. usort() toma los dos primeros valores de arreglo
2. function los recibe y retorna:
#$a<$b:
echo $var_a <=> $var_d;
#Out: 🙃 -1

#$a>$b:
echo $var_d <=> $var_a;
#Out: 🙃 1

##$a==$b:
echo $var_a <=> $var_b;
#Out: 🙃 0
    return $a <=> $b;
3. usort utiliza el valor retornado para ordenar
el array. 
*/
return $a<=>$b;
});

var_dump($cafe_price);

/*🙃Out: array(5) { 
    [0]=> int(1) 
    [1]=> int(12) 
    [2]=> int(13) 
    [3]=> int(23) 
    [4]=> int(34) 
}*/	
```
### Build-In Functions
**PHP** cuenta con muchas funciones como **usort()** las cuales podrian resolver muchos de los problemas. Las funciones de encuentran en la documentacion de PHP por lo cual debemos ser especificos al momento de buscarlas. E.g. [Funciones de strings](https://www.php.net/manual/es/ref.strings.php)

```php
<?php
#Reto: Obtener la hora actual. 
function obtener_hora() {

#Set timezone desde php.ini o usando la func
#date_default_timezone_set("America/Bogota");
    date_default_timezone_set("America/Bogota");
    return date("h:i a");
  }
  
  echo "Hola, me podrias decir que hora es? \n";
#Concatenamos la func a un str.
  echo "Claro, son las ". obtener_hora();
```
---
### Hangman Game
---
```php
<?php

#7.Limpiamos pantalla cada despues 
function clear(){

#Asi le decimos al sistema opperativo que
#limpie la pantalla en windows
    if (PHP_OS =="WINNT") {
        system("cls");
    }
#Asi en linux o Mac
    else {
        system("clear");
    }
}


#Reto: Hangman

#1.Lista de palabras:
$words = ["Beberage","Square","High",
"Pain","Singer","Endevour","Doer"];

#Constante max intentos:
define("MAX_ATTEMPS",6);
#Bienvenida al Juego
echo "Hangman Game!";

#2.Elegimos una palabra aleatoria de $words
$choosen_word = $words[rand(0,6)];

#3.Standarizamos la palabra
$choosen_word = strtolower($choosen_word);
$word_len = strlen($choosen_word);
$underscore_letter = str_pad("",$word_len,"_");
#🙃Out: endevour es igual a ________

#Intentos del usuario, indicamos total letras
$atteps = 0;
echo "Esta palabra tiene $word_len letras";

#4. Solicitamos al usuario que ingrese letras
do{
    $player_letter = readline("Ingresa una letra");
    $player_letter = strtolower($player_letter);


    /*5.Validamos si la letra esta dentro de 
    la palabra con "str_contains()" retorna "true" 
    si $player_letter esta en $choosen_word.*/
    if(str_contains($choosen_word, $player_letter)){
        $offset = 0;
    /*La funcion "strpos()" encuentra la posicion 
    de la primera ocurrencia de un caracter 
    en un string, cuando ya no hay mas ocurrencias
    la funcion devuelve "false", por esta razon 
    usamos "ciclo while" pues se detendra cuando la 
    letra no este dentro del str.*/

    #El concepto de presedencia hace posible que podamos
    #declara $letter_position dentro de "while"
        while(
            ($letter_position = strpos($choosen_word,$player_letter,$offset))!==false\
            ){
            $underscore_letter[$letter_position] = $player_letter;

    /*Offset es el punto de partida de "strpos()" luego que
    encontramos la primera ocurrencia por ejemplo en 
    la posicion 3, entonces cambiamos offset para ahora
    strpos() inicie desde la posicion 4, asi hasta 
    que no hay ocurrencias y retorne false para salir
    del ciclo while.*/
            $offset = $letter_position + 1;
        }
    }
    else {
    #6.Notificamos al usuario cuantos intentos le quedan. 
        clear();
        $attemps++;
        echo "Letra incorrecta 😥, Te quedan".(MAX_ATTEMPS-$attemps)." intentos";
        #Delay de 2 segundos para mostrar el mensaje anterior 
        #y luego limpiar la pantalla.
        sleep(2);
    }
}
#Se ejecuta mientras no se sobrepasen los intentos maximos
#y mientras $underscore_letter != $choosen_word no sean iguales
while($attemps < MAX_ATTEMPS && $underscore_letter != $choosen_word);

#Limpiamos pantalla cuando termina el programa.
clear();

#8.Le informa al usuario el resultado del Juego
if ($attemps < MAX_ATTEMPS){
    echo "Felicidades! Has adivinado la palabra";
}
else {
    echo "Suerte para la proxima";
}
#La palabra del PC
echo "La palabra es: $choosen_word";
#Lo que logro el usuario.
echo "Tu descubriste: $underscore_letter";
```
---
### PHP con HTML
---
**PHP** fue diseñado para preprocesar **HTML**, para realmente tratar a HTML como un lenguaje de Programacion. Como se ve en el ejemplo PHP esta completamente arraigado a HTML.

```php
<body>
    <h1>Esto es PHP combinado con HTML</h1>
<!--Hay dos bloques de PHP donde el segundo 
solo y unicamente cierra la llave del foreach-->
    <?php foreach ($iterable as $value){?>

<!-- asigna a "src" $value de cada ciclo donde 
$iterable es una lista de links de imagenes.-->
        <img src="<?php echo $value; ?>">
    <?php }?>
<h1><?php echo "Hola, Servidor Funcionando!😎";?></h1>
<?php echo "<h1>Hola, Servidor Funcionando!😎<br></h1>";?>
</body>
```
	
### Introduccion
---
- **SSR** Server Side Rendering: El servidor es quien procesa y renderiza los documentos. En este caso **PHP** realiza **SSR**.
- **CSR**: Es el tipo de renderizado en `React.js` o `Vue.js`. Es el navegador del cliente quien por medio de codigo JavaSript estructura y renderiza todo el website.
- **SSG** Static Site Generation: La computadora del programador es la que renderiza y estructura y carga al servidor los archivo de alguna forma ya renderizados.

### PHP como preprocesador de HTML
---
Existen una alternativa mas legible para imprimir texto en pantalla con **PHP**.
```php  
<?php 
#Declaramos una variable en PHP para usarla en HTML
$name = "Mr. Chapman";
?> 
```
Forma tradicional 
```php
<?php echo "<b>$name</b>";?>
```
podemos usar 
```php
<?= "<i>$name!</i>"?>
```
donde no tenemos que colocar `php` en cambio `=` y ademas no colocamos `;` al fina del `echo`.
	
### Condicionales
---
Si queremos utilizar condicionales es aceptable utilizar la sinaxis tradicional de **PHP**. En este caso se usan `{}` y esto presimente no es legible asi que mejor usamos una alternativa.
	
1. **Sintaxis PHP**
```php
<h1>Esto es Aceptable</h1>
<?php if (true){ ?>
    <p>✌️</p>
<?php } else{?>
    <p>😥</p>
<?php }?>	
```

2. **Alternativa**: Es una excelente option puesto que es mas legible dentro del codigo **HTML**.
```php
<h1>Esto es lo correcto</h1>
<?php if(true):?>
    <p>🚀</p>
<?php else: ?>
    <p>😥</p>
<?php endif; ?>	
```
### Ciclos
---
Podemos implementar cualquier tipo de ciclo siguiendo una estructura similar a la de los condicionales donde en vez de usar `{}` usamos `:` y en vez de cerrar con `}` usamos `endwhile;`,`endfor;`,`endforeach;`

```php
<body>
    <ul>
    <?php 
    $variable = ["Andres","Rob","Andrew"];
    foreach ($variable as $value):?>
    <li><?= "$value 🚀" ?></li>
    <?php endforeach; ?>
    </ul>
</body>	
```
---
### ¿Cómo pasar variables de PHP a JavaScript?

**SSR**: El **servidor** ejecuta todo el codigo **PHP** y nos devuelve una plantilla para que la ejecute el navegador, puesto que el `navegador no puede ejecutar PHP`. PHP se ejecuta mientras la pagina es preprocesada en el servidor, despues de que esta en el navegador solo interactua JS. Aunque esto es posible no es recomendable a nivel de seguridad no es buena idea que PHP coloque datos a menos que se estrictamente necesario. 
	
```php
<?php 
#Creamos un arreglo de usuarios
$user_list = array(
    array(
        "id" =>0,
        "username"=>"Mr. Michi"
    ),
    array(
        "id" =>1,
        "username"=>"DanMuner"
    ),
    array(
        "id" =>2,
        "username"=>"Chapulin"
    ),
);

#Declaracion variable
$animal_name = "Hektivich";
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Texto</title>
</head>
<body>

<script>
	
//podemos escribir PHP aquí dentro de parse()😎
//func de PHP json_encode() convierte un array-JSON a str
//func de JS JSON.parse() convierte un str a JSON
	
let user_name = JSON.parse('<?= json_encode($user_list) ?>');
let animal_name = "<?= $animal_name ?>";
</script>
</body>
</html>	
```
### Evita el código espagueti
No solo se refiere a codigo anidado sino en general al orden y la legibilidad a nivel visual. Buena practica es colocar toda la logica de **PHP** al inicio del archivo y luego abajo **HTML** con **PHP** que se imprime en pantalla.
	
![image](https://user-images.githubusercontent.com/60556632/167523626-194ac60b-b01d-4e6d-b69f-ca7b79d61477.png)

### Cómo obtener una solicitud al servidor con PHP

PHP define las variables superglobales a traves de las cuales podemos acceder a cierta informacion desde cualquier parte del codigo:

- **$_GET**: Se envian los datos a trves de la URL. 
- **$_POST**: Se envian de forma oculta.
- **$_REQUEST**: Es como tener POST y GET al tiempo.

```php
<script>
    const formData = new FormData();
    formData.append('nombre','Mr.michi');
    formData.append('edad','14');

//Enviamos una solicitud GET y POST al servidor
//en este caso el codigo del servidor solo es:
<?php 
var_dump($_POST);
var_dump($_GET);
?>
    fetch("server.php?color=naranja",{
//Enviamos una solicitud POST
        body:formData,
        method:"POST"
    })

//Se imprime en pantalla los datos enviados a traves 
//de JS.
    .then(res => res.text())
    .then(data => {
        console.log(data);
    })
</script>	
```
### Envío de un formulario a través de GET
---
El metodo por defecto es en PHP es **GET**, luego si no lo especificamos `method="get"` será **$_GET**.
	
1. Creamos un formulario que se conecte con `server.php` y envie informacion a traves del metodo GET. 
	
```php
<body>
<!--Creamos form con metodo GET
indicamos el action que vendria siendo el servidor
een realidad solo crearmos un archivo server.php-->
    <form action="./server.php" method="get">
<!--Creamos input es importante tener siempre
el atributo name pues asi lo identifica el servidor
y opcionalmente colocamos id y para relacionarlo
en la etiqueta label for="nombre", id="nombre"-->
        <label for="nombre">Nombre:</label>
        <input type="text" name="nombre" id="nombre">
        
        <label for="nombre">Edad:</label>
        <input type="text" name="edad" id="edad">
<!--Creamos boton y cuando lo presionamos veremos que
el contenido a enviar se vera en la URL es muy 
importante que el boton sea de tipo "submit"-->
        <button type="submit">Mandar Formulario</button>
    </form>
</body>	
```
2. Creamos nuestro archivo `server.php` donde podremos interactuar con la variable `$_GET`.
	
```php
<?php 
/*<pre> es uuna etiqueta de preformateado
muestra los datos de forma justificada u ordenada */
echo "<pre>";
#Luego que presionar el boton podemos evaluar 
#que contiene nuestra variable $_GET
var_dump($_GET);

#Si queremos podemos validar lo que se encuentra
#en la variable $_GET

$nombre = $_GET["nombre"];
$edad = $_GET["edad"];

echo "El usuario $nombre tiene $edad años";

echo "</pre>";

/*🙃Out:
array(2) {
  ["nombre"]=>
  string(6) "Daniel"
  ["edad"]=>
  string(2) "57"
}
El usuario Daniel tiene 57 años
*/
?>	
```

3. Asi se ve el formulario con la informacion que estamos enviando
![image](https://user-images.githubusercontent.com/60556632/167755537-816eb5d3-3814-4e5f-a2d9-62a01fb9d9b8.png)
	
4. Asi se ve la URL luego de enviar el formulario `http://127.0.0.1:8080/server.php?nombre=Daniel&edad=57`.
	
5. Asi se ve la salida de `server.php` luego de ejecutar `index.php`. 
```php
/*🙃Out:
array(2) {
  ["nombre"]=>
  string(6) "Daniel"
  ["edad"]=>
  string(2) "57"
}
El usuario Daniel tiene 57 años
*/	
```

### Envío de un formulario a través de POST
---
La diferencia pricipal es que **POST** no envia informacion a traves de la URL como lo hace **GET**, sin embargo, aunque la envia de forma oculta si inspeccionamos la consola del navegador podremos encontrar el informacion enviada ingresando a `network`. Respento al codigo es practicamente el mismo solo que el documento principal `index.php` utiliza el metodo **POST**

```php
<form action="./server.php" method="post">
```
 Lo mismo sucede con `server.php` donde `$_POST` podra ser inspeccionado facilmente. 
```php
<?php 
echo "<pre>";
var_dump($_POST);
echo "</pre>";
?>
```
Y si queremos ver la URL podremos comprobar que no hay informacion `http://127.0.0.1:8080/server.php`.
	
- **Important!** Debido a que la informacion no se encuentra oculta realmente; es importante no enviar informacion sensible como passwords, tarjetas de credito, a traves de este metodo. Para esto existen otras alternativas como con JS. ✌️

### Envío de imágenes
Existe una variable superglobal llamada `$_FILES` la cual nos permite enviar cualquier tipo de archivo. Cualquier archivo enviado al servidor se guar de manera temporal y se limpia cada cierto tiempo. `$_FILES` contien informacion en forma de array acerca del archivo que se esta manipulando. 
	
- **quick topic**: Es importante indicar el tipo de encriptado en los formularios de HTML el mas basico es `application/x-www-form-urlencoded` pero cuando nos referimos a archivos multimedia usamos `multipart/form-data`.

```php
 <form action="./server.php" method="post" enctype="multipart/form-data">
```
Ahora que indicamos el tipo de encriptacion solo queda indicar que el input es de tipo file:
	 
```php
<label for="image">Imagen:</label>
<input type="file" name="image" id="image">	 
```
En `server.php` usamos la variable superglobal `$_FILES`.
	 
```php
<?php 
echo "<pre>";
var_dump($_FILES);
echo "</pre>";
$basename= $_FILES["image"]["name"];
echo $basename;
?>
```
Y al ejecutar nuestro codigo podremos confirmar que  `$_FILES` efectivamente es un array con la informacion de file que se cargo.  
![image](https://user-images.githubusercontent.com/60556632/167764988-5db81991-bfc4-4fdf-8454-f5ec990d01fe.png)

### Tipos de inputs
Como ya se menciono el atributo `name` es un identificador para el servidor y si no lo colocamos el servidor no entendera lo que estamos solitando. 
	 
```php
<?php
var_dump($_POST["nombre"]);
?>
<input type="text" name="nombre"/>	 
```
Cuado nos referimos a los **inputs** se esta hablando de lo que colocamos dentro del atributo `name` y en `type` en el caso anterior tenemos un **input** simple pero tambien se pueden tener de tipo array asi el servidor podra manipular arreglos. 
	 
```php	 
<?php
var_dump($_POST["personas"]);
?>
	 
<input type="text" name="personas[]"/>
<input type="text" name="personas[]"/>
<input type="text" name="personas[]"/>	 
```
Existen inputs con arreglos asociativos:	 
```php
<?php
var_dump($_POST["persona"]);
?>
	 
<input type="text" name="persona[nombre]"/>
<input type="email" name="persona[email]"/>
<input type="text" name="persona[telefono]"/>	 
```

Existen inputs tipo checkbox:	 
```php
<input type="checkbox" name="list1"/>
<input type="checkbox" name="list2"/>
<input type="checkbox" name="list3"/> 
```
Existen inputs tipo radio:	 
```php
<?php
var_dump($_POST["pais"]);
?>	 
#Value es lo que se envia al servidor y name es el indicador
<label for="mexico">Mexico</label>
<input type="radio" name="list1" value="Mexico" id="mexico"/>
	 
<label for="colombia">Colombia</label>
<input type="radio" name="list2" value="Colombia" id="colombia"/>
	 
<label for="peru">Peru</label>
<input type="radio" name="list3" value="Peru" id="peru"/> 
```
	 
Existen inputs de multiples archivos, en este caso podemos enviar varias imagenes en forma de arraglos:	 
```php
<?php
var_dump($_FILES["galeria"]);
?>	
	 
<label for="galeria">Carga tus Imagenes</label>
<input type="file" multiple name="galeria[]" id="galeria"/>
```
### Valida si un formulario ha sido enviado.
Colocamos en nuestro HTML los atributos `name` esto aplica incluso en el formulario.
```php
<form action="./server.php" method="post">
    <label for="nombre">Nombre:</label>
    <input type="text" name="nombre" id="nombre">
    <button name="form" type="submit">Submit</button>
</form>   	 
En el codigo **PHP** usaremos dos funciones nuevas como lo es `empty()` y `isste()`.
	 
```php
<?php

#empty() permite saber si el input esta vacio.
#empty() retorna "true" si esta vacio.
#isset() evalua si el atributo name esta definido.


if (isset($_POST["nombre"]) && !empty($_POST["nombre"])) {
    echo "!Hola ".$_POST["nombre"]." !";
}
else {
    echo "No mandaste nada!";
}

/*Tambien podemos colocar el atributo "name" para
validar si el formulario fue enviado, sin embargo es
importe usar empty() de lo contrario de enviaria vacio.
*/
if(isset($_POST["form"])){
    echo "Todo el formulario fue enviado";
}
else{
    echo "No se envio ningun formulario";
}
?>	 
```
### Sanitizando datos de mi formulario
No solo basta evaluar si algo se envio o no, ademas hay que evitar que nos envien informacion no deseada. 
	
- Normalente dilijenciamos un formulario y optenemos una respuesa de este tipo.
![image](https://user-images.githubusercontent.com/60556632/167972588-0176a1f2-6707-441c-bc2b-a04334dd405b.png)

```php
Array
(
    [nombre] => Daniel
    [username] => Danuser
    [correo] => daniel@gmail.com
    [edad] => 27
)	 
```
- Informacion no deseada podria se que por ejemplo que inyectaran codigo **HTML** en el formulario en vez de la informacion solicitada com ose ve a continuacion, donde este codigo modificaria nuestra estructura. 

![image](https://user-images.githubusercontent.com/60556632/167973237-a7b8d446-3d1f-4d6f-a6ee-247dd76c6490.png)

- **Solucion-Sanetizar🤓**
	 
Una de las opciones mas completas y cuya [Documentacion](https://www.php.net/manual/es/function.filter-var.php) es extensa es `filter_var` por lo cual es recomendable revisarla. 
	 
```php
<?php 

$name = $_POST["nombre"];
$username = $_POST["username"];
$email = $_POST["correo"];
$edad = $_POST["edad"];

/*Para sanetizar cada variable de nuestro 
formulario usamos la funcion:*/
$htmlname = htmlentities($name);
$htmlusername = htmlentities($username);
$htmlemail = htmlentities($email);
$htmledad = htmlentities($edad);

#Otras formas de sanetizar pueden ser las
#las siguientes funciones:

#A traves de Expresiones regulares-REGEX
preg_replace("/\d/", "", $username);

/*Funcion con constantes especializadas
dependiento del tipo de dato del formulario
en el ejemplo lo realizamos sobre un correo 
y sobre numeros enteros*/
filter_var($email, FILTER_SANITIZE_EMAIL);
filter_var($age, FILTER_SANITIZE_NUMBER_INT);

?>	 
```

### Validando datos
`filter_var` no solo tiene **filtros de sanetizacion** sino tambien **filtros de validacion** esto se encuentra en la [Documentacion](https://www.php.net/manual/es/filter.filters.php).

```php
<?php 
#Validamos un tipo de dato flotante
#El tercer paramentro es un modificado y es opcional

$is_float = filter_var("This isn't a Float",
FILTER_VALIDATE_FLOAT,FILTER_FLAG_ALLOW_THOUSAND);
var_dump($is_float);
#🙃Out: bool(false)

$is_int = filter_var("120",FILTER_VALIDATE_INT);
var_dump($is_int);
#🙃Out: int(120)

$is_ip = filter_var("167.0.0.9",FILTER_VALIDATE_IP);
var_dump($is_ip);
#🙃Out: string(9) "167.0.0.9"

#La URL debe ser bien escrita ✌️
$is_url = filter_var("platzi.com",FILTER_VALIDATE_URL);
var_dump($is_url);
#🙃Out: bool(false)

#Asi se escribe la URL
$is_url = filter_var("https://platzi.com",FILTER_VALIDATE_URL);
var_dump($is_url);
#🙃Out:"https://platzi.com"

$is_email = filter_var("email@email.com",FILTER_VALIDATE_EMAIL);
var_dump($is_email);
#🙃Out:"email@email.com"
?>	 
```
---	 
### Proyecto
---
### Creando el maquetado	 
Codigo **CSS**
```css
Skip to content
platzi
/
php-html
Public
Code
Issues
Pull requests
Actions
Projects
More
php-html/formulario-contacto/style.css
@RetaxMaster
RetaxMaster Clase 20 Maquetando el formulario
 History
 1 contributor
172 lines (150 sloc)  3.2 KB
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 50px;
    background: #e5e5e5;
    font-family: 'Roboto', sans-serif;
}

.alert {
    margin-bottom: 15px;
    padding: 20px 30px;
    color: #fff;
    text-align: center;
    border-radius: 5px;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    -ms-border-radius: 5px;
    -o-border-radius: 5px;
}

.alert.success {
    background: #59e5a2;
}

.alert.danger {
    background: #e55961;
}

form {
    position: relative;
    background: #fff;
    padding: 30px;
    margin-bottom: 100px;
    border-radius: 6px;
    -webkit-border-radius: 6px;
    -moz-border-radius: 6px;
    -ms-border-radius: 6px;
    -o-border-radius: 6px;
}

form h1 {
    text-align: center;
    margin-bottom: 20px;
}

textarea {
    min-height: 75px;
    resize: none;
}

.input-group {
    display: flex;
    flex-direction: column;
    margin-bottom: 15px;
}

.input-group label {
    margin-bottom: 5px;
}

.input-group input,
.input-group textarea {
    padding: 7px;
    outline: none;
    border: 1px solid #ccc;
    box-shadow: 0 0 0 0 #fff;
    border-radius: 5px;
    transition: 0.2s box-shadow ease;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    -ms-border-radius: 5px;
    -o-border-radius: 5px;
    -webkit-transition: 0.2s box-shadow ease;
    -moz-transition: 0.2s box-shadow ease;
    -ms-transition: 0.2s box-shadow ease;
    -o-transition: 0.2s box-shadow ease;
}

.input-group input:focus,
.input-group textarea:focus {
    box-shadow: 0 0 0 3px rgba(151, 115, 254, 0.25);
}

.button-container {
    display: flex;
    justify-content: center;
}

.button-container button {
    border: none;
    outline: none;
    padding: 8px 20px;
    background: #7392fe;
    color: #fff;
    border-radius: 3px;
    font-weight: bold;
    cursor: pointer;
    transition: 0.3s all ease;
    -webkit-transition: 0.3s all ease;
    -moz-transition: 0.3s all ease;
    -ms-transition: 0.3s all ease;
    -o-transition: 0.3s all ease;
}

.button-container button:hover {
    background: #577bfb;
}

.button-container button:focus {
    box-shadow: 0 0 0 3px rgba(115, 146, 254, 0.25);
}

form::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    background: #7e5dde;
    display: inline-block;
    width: 100%;
    height: 10px;
    border-top-left-radius: 6px;
    border-top-right-radius: 6px;
}

form .contact-info {
    position: absolute;
    top: 96%;
    left: 50%;
    display: flex;
    width: calc(100% + 60px);
    font-size: 13px;
    background: #9773fe;
    color: #fff;
    border-radius: 3px;
    transform: translateX(-50%);
    -webkit-transform: translateX(-50%);
    -moz-transform: translateX(-50%);
    -ms-transform: translateX(-50%);
    -o-transform: translateX(-50%);
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;
    -ms-border-radius: 3px;
    -o-border-radius: 3px;
}

form .contact-info .info {
    display: flex;
    align-items: center;
    width: 50%;
    padding: 30px;
}

form, .alert {
    min-width: 80%;
}

@media (min-width: 450px) {
    
    form, .alert {
        min-width: 370px
    }

}	 
```	
---
Codigo **HTML**
---
	 
```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Formulario de contacto</title>
</head>
<body>

    <?php if($status == "danger"): ?>
    
    <div class="alert danger">
        <span>Surgió un problema</span>
    </div>
    
    <?php endif; ?>
    

    <?php if($status == "success"): ?>
    
    <div class="alert success">
        <span>¡Mensaje enviado con éxito!</span>
    </div>
    
    <?php endif; ?>

    <form action="./" method="POST">

        <h1>¡Contáctanos!</h1>

        <div class="input-group">
            <label for="name">Nombre:</label>
            <input type="text" name="name" id="name">
        </div>

        <div class="input-group">
            <label for="email">Correo:</label>
            <input type="email" name="email" id="email">
        </div>

        <div class="input-group">
            <label for="subject">Asunto:</label>
            <input type="text" name="subject" id="subject">
        </div>

        <div class="input-group">
            <label for="message">Mensaje:</label>
            <textarea name="message" id="message"></textarea>
        </div>

        <div class="button-container">
            <button name="form" type="submit">Enviar</button>
        </div>

        <div class="contact-info">
            
            <div class="info">
                <span><i class="fas fa-map-marker-alt"></i> 13 Saw Mill Circle, North Olmested.</span>
            </div>

            <div class="info">
                <span><i class="fas fa-phone"></i> +1 123 456 7890</span>
            </div>

        </div>

    </form>

    <script src="https://kit.fontawesome.com/bbff992efd.js" crossorigin="anonymous"></script>
    
</body>
</html>	 
```
![image](https://user-images.githubusercontent.com/60556632/167980083-2683c71a-ed45-4052-8ce5-e4fad05ee954.png)

- Diligenciamos el formulario:
![image](https://user-images.githubusercontent.com/60556632/167980287-0009e488-b605-4004-983f-90962663de8d.png)

Codigo **PHP**
---
```php
<?php
#Creamos una funcion que valide si los campos
#fueron diligeciados para esto usamos empty()
function validate($name, $email, $subject, $message, $form) {
    return !empty($name) && !empty($email) && !empty($subject) && !empty($message);
}

#Declaramos variables de estado
$status = "";

#Realizamos un isset() de todo el formulario
if ( isset($_POST["form"]) ) {

#Le pasamos los datos a la funcion a usando unpacking
    if ( validate(...$_POST) ) {
        
        $name = $_POST["name"];
        $email = $_POST["email"];
        $subject = $_POST["subject"];
        $message = $_POST["message"];

        // Mandar el correo
#Modificamos el estado dependiendo la respuesta
# de validate(...$_POST)
        $status = "success";

    }
    else {
        $status = "danger";
    }
   
}

?>	 
```

Esta parte se encuentra en el HTML o `index.php`, esta parte del codigo muestra un indicador de `success`.
	 
```php
<?php if($status == "success"): ?>

<div class="alert success">
<span>¡Mensaje enviado con éxito!</span>
</div>

<?php endif; ?>	 
```
![image](https://user-images.githubusercontent.com/60556632/167981417-75142d1c-5e2c-4ec0-a773-069a2efe9b94.png)

Esta parte del codigo muestra un indicador de `danger`
	
```php
<?php if($status == "danger"): ?>

<div class="alert danger">
<span>Surgió un problema</span>
</div>

<?php endif; ?>
```
![image](https://user-images.githubusercontent.com/60556632/167981496-af117534-ecc4-4a30-9c4d-ff5c99342468.png)
---
### Integrando [PHPMailer](https://packagist.org/packages/phpmailer/phpmailer)
- [Recomendado Composer](https://platzi.com/cursos/php-composer/) puesto que para seguir programando con **PHP** necesitamos aprender **Composer** el cual es un **manejador de paquetes** como **nmp**-JS, **homebrew**-MacOS, **apt**-Ubuntu. Este basicamente sirve para instalar librerias externas como en este caso que necesitamos `phpmailer`.
	 
1. Download Composer and run `Composer-Setup.exe`



