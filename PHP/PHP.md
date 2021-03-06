# PHP

## Sintaxis Básica

```php
<?php
	// codigo en php
?>
```

La extensión de los archivos php es ".php".

Todas las instrucciones php deben de terminar en ; (punto y coma).

## Case Sensitivity

En php las palabras clave, clases, funciones y funciones definidas por el usuario son not-case-sensitive, pero los nombres de las variables son case sensitive.

## Comentarios

Para hacer comentarios de una sola linea podemos hacer uso de // y #.

```php
<?php
    // Comentario de una sola linea
    # Comentario de una sola linea
?>
```

En el caso de los comentarios multilinea podemos hacerlo de la siguiente manera:

```php
<?php
    /* 
    Este es un comentario
    de multiples lineas
    */
?>
```

## Variables

En php las variables empiezan con un signo de dolar $.

```php
<?php
    $texto="Hola";
	$numero=5;
	$decimal=10.5;
?>
```

### Reglas para las variables en php

- Toda variable debe empezar con $ seguido del nombre de la variable.
- El nombre de una variable debe empezar con una letra o un guión bajo.
- El nombre de una variable no puede empezar con un número.
- El nombre de una variable solo puede contener caracteres alfanuméricos y guiones bajos.
- Los nombres de las variables son case-sensitive.

### Salida de Variables

En php la instrucción "echo" es la mas usada para mostrar datos en pantalla.

```php
<?php
    $texto="Hola";
    echo "El valor de la variable texto es: $texto";
?>
```

### Typado

php maneja un typado flexible, esto significa que no hay que decirle a php el tipo de dato de cada variable, php de manera automatica asocia el tipo de dato de la variable por el valor que se le asigne.

### Alcance de las variables en php

php tiene 3 alcances con las variables:

- global
- local
- static

Una variable declarada fuera de una función tiene un alcance GLOBAL y solo se puede acceder fuera de una función.

Una variable declarada dentro de una función tiene un alcance LOCAL y solo se puede acceder dentro de esa función.

### La palabra clave global

La palabra clave global se utiliza para acceder a una variable global desde dentro de una función.

```php
<?php
$x = 5;
$y = 10;

function myTest() {
  global $x, $y;
  $y = $x + $y;
}

myTest();
echo $y; // salida 15
?>
```

### La palabra clave static

Normalmente, cuando se completa / ejecuta una función, se eliminan todas sus variables. Sin embargo, a veces queremos que NO se elimine una variable local. Lo necesitamos para otro trabajo. Para hacer esto, use la palabra clave estática cuando declare la variable por primera vez.

```php
<?php
function myTest() {
  static $x = 0;
  echo $x;
  $x++;
}

myTest();
myTest();
myTest();
?>
```

### Las instrucciones echo y print

echo y print son más o menos lo mismo. Ambos se utilizan para enviar datos a la pantalla.

Las diferencias son pequeñas: echo no tiene valor de retorno, mientras que print tiene un valor de retorno de 1, por lo que puede usarse en expresiones. echo puede tomar múltiples parámetros (aunque tal uso es raro) mientras que print puede tomar un argumento. echo es ligeramente más rápido que print.

```php
<?php
echo "<h2>PHP es divertido!</h2>";
echo "Hola mundo!<br>";
echo "Este ", "string ", "está ", "hecho ", "con muchos parametros.";
?>
```

```php
<?php
print "<h2>PHP es divertido!</h2>";
print "Hola mundo!<br>";
?>
```

## Tipo de Datos

php admite los siguientes tipos de datos:

- String
- Integer
- Float
- Boolean
- Array
- Object
- NULL
- Resource

> Nota: la función var_dump() nos permite retornar el el tipo de dato de una variable

```php
<?php
    $texto="Hola"; // String
	$numero=15; // Integer
	$decimal=8.4; //Float
	$booleano=true; // Boolean
	$frutas= array("manzana","pera","naranja") //Array
    $x=null //NULL
?>
```

### Object

Las clases y los objetos son los dos aspectos principales de la programación orientada a objetos. Una clase es una plantilla para objetos y un objeto es una instancia de una clase.

```php
<?php
class Car {
  public $color;
  public $model;
  public function __construct($color, $model) {
    $this->color = $color;
    $this->model = $model;
  }
  public function message() {
    return "My car is a " . $this->color . " " . $this->model . "!";
  }
}

$myCar = new Car("black", "Volvo");
echo $myCar -> message();
echo "<br>";
$myCar = new Car("red", "Toyota");
echo $myCar -> message();
?>
```

### Resource

El tipo de recurso especial no es un tipo de datos real. Es el almacenamiento de una referencia a funciones y recursos externos a PHP. Un ejemplo común de uso del tipo de datos de recursos es una llamada a la base de datos.

## String

Algunas funciones de String mas usadas en php son:

- strlen(): retorna la longitud de un string.
- str_word_count(): cuenta las palabras de un string.
- strrev(): voltea un string.
- strpos(): busca un texto en un string.
- str_replace: remplaza palabras en un string.

## Numbers

Una cosa a tener en cuenta sobre PHP es que proporciona conversión automática de tipos de datos. Entonces, si asigna un valor entero a una variable, el tipo de esa variable será automáticamente un entero. Luego, si asigna una cadena a la misma variable, el tipo cambiará a una cadena. Esta conversión automática a veces puede romper su código.

## Math

### Función pi()

Retorna el valor de pi:

```php
<?php
echo(pi()); // retorna 3.1415926535898
?>
```

### Función min() y max()

Las funciones min () y max () se pueden usar para encontrar el valor más bajo o más alto en una lista de argumentos:

```php
<?php
echo(min(0, 150, 30, 20, -8, -200));  // retorna -200
echo(max(0, 150, 30, 20, -8, -200));  // retorna 150
?>
```

### Función abs()

La función abs() se usa para encontrar el valor absoluto de un número:

```php
<?php
echo(abs(-6.7));  // retorna 6.7
?>
```

### Función sqrt()

La función sqrt() se usa para encontrar la raíz cuadrada de un número:

```php
<?php
	echo(sqrt(64));  // retorna 8
?>
```

### Función round()

La función round () redondea un número de decimal a su entero más cercano:

```php
<?php
	echo(round(0.60));  // retorna 1
	echo(round(0.49));  // retorna 0
?>
```

### Función rand()

Genera un número aleatorio:

```php
<?php
	echo(rand());
?>
```

Podemos agregar un rango de valores para poder obtener un numero aleatorio dentro de ese rango:

```php
<?php
	echo(rand(10,100)); // retorna un número aleatorio entre 10 y 100
?>
```

## Constantes

Una constante es un identificador (nombre) de un valor simple. El valor no se puede cambiar durante el script. Un nombre de constante válido comienza con una letra o un guión bajo (sin signo $ antes del nombre de la constante).

> Nota: A diferencia de las variables, las constantes automáticamente son globales en el script.

### Definiendo una constante

Para crear una constante usamos la función define()

### Sintaxis

> define(*name*, *value*, *case-insensitive*)

Parámetros:

- nombre: especifica el nombre de la constante.
- value: especifica el valor de la constante no distingue entre mayúsculas y minúsculas
- case-insensitive: especifica si el nombre de la constante no debe distinguir entre mayúsculas y minúsculas. El valor predeterminado es falso

Veamos un ejemplo donde creamos una constante que es case-sensitive:

```php
<?php
	define("GREETING", "Welcome to W3Schools.com!");
	echo GREETING;
?>
```

recordemos que dentro de la función define el parametro de case-insensitive por defecto es falso, si nosotros colocamos un true en ese parametro hacemos que nuestra constante sea case-insensitive

```php
<?php
	define("GREETING", "Welcome to W3Schools.com!", true);
	echo greeting;
?>
```

## Arreglos (arrays)

Los arreglos nos permiten almacenar multiples valores en una sola variable.

```php
    <?php
        $Mascota = array ("Gato","Perro","Tortuga");
        echo "Mis mascotas preferidas son $Mascota[0], $Mascota[1] y $Mascota[2]";
    ?>
```

### Arreglos Asociativos

Los arreglos asociativas son arreglos que utilizan claves con nombre que les asigna.

Hay dos formas de crear un arreglo asociativo:

```php
<?php
	$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
?>
```

y

```php
<?php	
	$age['Peter'] = "35";
	$age['Ben'] = "37";
	$age['Joe'] = "43";
?>
```

### Arreglos Multidimensionales

Una matriz multidimensional es una matriz que contiene una o más matrices.

PHP admite matrices multidimensionales que tienen dos, tres, cuatro, cinco o más niveles de profundidad. Sin embargo, las matrices de más de tres niveles de profundidad son difíciles de administrar para la mayoría de las personas.

> Nota: La dimensión de una matriz indica el número de índices que necesita para seleccionar un elemento.
>
> - Para una matriz bidimensional, necesita dos índices para seleccionar un elemento
> - Para una matriz tridimensional, necesita tres índices para seleccionar un elemento

Un pequeño ejemplo de como se crea un arreglo bidimensional con php:

```php
<?php
	$cars = array (
	array("Volvo",22,18),
	array("BMW",15,13),
	array("Saab",5,2),
	array("Land Rover",17,15)
	);
?>
```

### Sort (Funciones de ordenación)

- sort(): Ordena el arreglo en forma ascendente.
- rsort(): Ordena el arreglo en forma descendente.
- asort(): Ordena el arreglo asociativo en forma ascendente de acuerdo con el valor.
- ksort(): Ordena el arreglo asociativo en forma ascendente de acuerdo con la llave.
- arsort(): Ordena el arreglo asociativo en forma descendente de acuerdo con el valor.
- krsort(): Ordena el arreglo asociativo en forma descendente de acuerdo con la llave.

Un pequeño ejemplo de como se usan estas funciones:

```php
<?php
	$numbers = array(4, 6, 2, 22, 11);
	sort($numbers);
?>
```

## Variables Superglobales

Algunas variables predefinidas en PHP son "superglobales", lo que significa que siempre son accesibles, independientemente del alcance, y puede acceder a ellas desde cualquier función, clase o archivo sin tener que hacer nada especial.

Las variables superglobales son:

- $GLOBALS
- $_SERVER
- $_REQUEST
- $_POST
- $_GET
- $_FILES
- $_ENV
- $_COOKIE
- $_SESSION