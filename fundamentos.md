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
