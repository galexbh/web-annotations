 

# CSS

Para dominar CCS debes entender: selectores, especificidad, herencia y cascada.

## Comentarios

```css
/* De esta manera se colocan comentarios en CSS */
```

Ejemplo de una regla css

```css
body/*Este es el selector*/{
    background: red; /*Todo lo que coloquemos dentro de las llaves es el bloque*/
    margin: 10px; /*Cada uno de estos elementos es una propiedad y valor*/
}
```

## Variables

```css
/*declaracion de variables*/
:root{
    --color: red;
}

/*como aplicarlas*/
body{
    background: var(--color);
}

h1{
    color: var(--color);
}
```

## Selectores de etiqueta

### selector de tipo unico o sencillo

```css
h1 /*etiqueta*/{
    /*propiedades*/
}
```

## Estilos del navegador

El navegador tiene su propia hoja de estilos o css por lo tanto si tu no le das ninguna estilo a tu html el navegador aplica sus propias reglas para resetear estos estilos que el navegador aplica podemos usar [normalize.css](https://necolas.github.io/normalize.css/).

## Selectores de clases

```css
<h1 class="title">Titulo</h1>
<p class="text"></p>

/* asi usamos los selectores de clases*/
.title{
    /*propiedades*/
}

.text{
    text-align: center;
}
```

## Selectores de ID

los selectores de id se recomiendan mas para JavaScript porque son identificadores unicos, es mala practica usarlos en CSS por este motivo de ser unicos.

```html
<p id="nombre">texto</p>
```

```css
#nombre{
    /*propiedades*/
}
```

## Selector Universal

Este tipo de selector afecta todo, no es muy recomendable usarlo debido a que puede tener comportamientos extraños.

```css
*{
    /*propiedades*/
}
```

## Selectores case sensitive y case insensitive

- **insensitive:** no diferencia entre mayusculas y minusculas div, p y muchas etiquetas mas son case insensitive.

- **sensitive:** diferencia entre mayusculas y minusculas los atributos todos son case sensitive.

## Selectores agrupados

```html
<h1 class="title">titulo</h1>
<p class="parrafo">texto</p>
```

```css
/*Asi se agrupan selectores*/
.title,
.parrafo{
    /*propiedades*/
}
```

## Selectores descendientes

Es recomendable no usar este tipo de selectores por la ESPECIFICIDAD salvo que no tuvieramos opcion.

```html
<ul class="list">
    <li class="item"></li>
    <li class="item"></li>
    <li class="item"></li>
    <li class="item"></li>
</ul>
```

```css
.list .item{
    /*propiedades*/
}
/*a todos los item que sean hijos de list aplicale las propiedades*/
/*Aqui el estilo se aplicara a todos los "item" que
sean hijos de "list"*/

.list.item{
    /*propiedades*/
}
```

De esta forma indicamos que las propiedades se aplicaran a las etiquetas que tengan ambas clases.

## Selector hijo directo

```css
ul > li{
    /*propiedades*/
}
```

> Todo li que sea hijo directo de ul tendra las propiedades

## Selector hermano siguiente

Para el elemento que esta justo despues del otro.

```html
<h1 class="title-1">Titulo</h1>
<p class="subtitle">Subtitulo de h1</p>

<h2 class="title-2">Subtitulo</h2>
<p class="subtitle">Subtitulo de h2</p>
```

Tenemos dos elementos con la clase subtitle pero queremos que se comporten de manera diferente.

```css
.title-1{
    color: red
}

.title-2{
    color: blue;
}
```

Aqui vamos a usar el selector hermano siguiente.

```css
.title-1 + .subtitle{
    /*propiedades*/
}

.title-2 + .subtitle{
    /*propiedades*/
}
```

De esta manera podemos hacer que ambos titulos ambas etiquetas p se conformen de manera diferente a pesar de tener la misma clasee esta manera podemos hacer que ambos titulos ambas etiquetas p se conformen de manera diferente a pesar de tener la misma clase.

## Selector Hermanos Siguientes

```css
.title-1 ~ .subtitle{
    /*propiedades*/
}

.title-2 ~ .subtitle{
    /*propiedades*/
}
```

Funciona similar al selector hermano siguiente con la diferencia de que este se aplica no solo al que esta justo despues, sino a todos los que estan despues.

## Selector de atributo

Selecciona por cualquier atributo que no sea una clase o un id este se encierra en [] corchetes.

```html
<input type="text">
```

```css
[type="text"]{
    /*propiedades*/
}
```

## Selector contiene

```html
<article class="article-1"></article>
<article class="article-2"></article>
```

```css
[class^="article"]{
    /*Propiedades*/
}
```

Con este selector se aplicaran las propiedades a todas las clases que tengan "article" en su nombre

## Especificidad, Herencia y Cascada

### Introduccion y Arquitectura

Con Arquitectura nos referimos a la forma en la que estructuramos nuestro CSS, algunas de ellas son SMACSS, OOCSS, ITCSS.

### Especificidad

Cuando un navegador abre una pagina el navegador aplica un estilo
CSS predeterminado, aparte de eso tu aplicas un estilo CSS y si usas algun framework.

Estas traen su estilo CSS, todos estos estilo entran en conflicto y el navegador
necesita un mecanismo para saber cual de esos estilos debe aplicar, eso es la especificidad

```css
tags 1
clases 10
id 100
inline 1000
!important = el poderoso
```

```html
<div id="main">
    <article class="post">
        <p>Hola</p>
    </article>
</div>
```
```css
#main .post p{
    color: red;
}

p{
    color: green;
}

div#main .post .p{
    color: blue;
}
```

Si nos fijamos en esas 3 reglas css ambas aplican un estilo a la etiqueta p pero ¿cuál de todos esos estilos va a aplicarse?, se va a aplicar el ultimo debido a que su nivel de especificidad es mayor.

## Cascada

Lo que viene despues sobreescribe a lo que esta antes

```css

p{
    color: red;
}

p{
    color: blue;
}
```

Aqui se aplica el color azul por ser el ultimo, siempre y cuando tengan la misma especificidad.

## Herencia

Los descendientes heredan las propiedades de sus padres

```html
<p>Hola<span>Mundo</span></p>
```

Los estilos que agreguemos a p se van a heredar a span.

## Initial Inherit

```html
<!--initial 
	inherit -->

<p>Hola<a href="">Mundo</a></p>
```

```css
p{
    color: red;
}

a{
    color: inherit;
}
```

Con esto forzamos a la etiqueta 'a' a heredar el color de la etiqueta 'p'.

```css
a{
    color: initial;
}
```

initial lo que hace es resetear a los valores por defecto en este caso 'a' como es un enlace debe salir subrayado en azul pero con 'initial' aparecera en negro.

# BOX MODEL

## Layout

Es la geometria de cada elemento

Las propiedades width y height son importantes aqui.

## Elementos Inline y de Bloque

- **Inline:**
     - No crean nuevas lineas para cada elemento.
     - Tienen ancho y alto relativo a su contenido, no se le pueden definir.
     - Se ajustan al contenido.

- **Bloque:**
  - Crean una nueva linea para cada elemento.
  - Ocupan todo el espacio horizontal disponible.
  - Tienen ancho y alto que podemos definir.

## Box Model

Es el algoritmo que aplica el navegador para dibujar los elementos

- La propiedades del Box Model son:
     - width
     - height
     - padding
     - margin

- El modelo se basa en:
  - Content Box 
  - Padding Box
  - Border Box
  - Margin Box

Es recomendable siempre en el selector universal usar el box-sizing: border-box; para que de esta manera el width y height no se cobreescriban por el margin y el padding.

## Propiedades de border

- border-width

- border-style

- border-color

  

- border-top-style

- border-right-style

- border-bottom-style

- border-left-style

## Shorthand de border

Se define con width style color.

```css
/*ejemplo:*/
border-top: 100px solid blue;
```

- border-top
- border-right
- border-bottom
- border-left

## Border Radius

El border radius es darle redondeo a cada esquina de un cuadrado.

- border-radius

- border-top-left-radius
- border-top-right-radius
- border-bottom-right-radius
- border-bottom-left-radius

## background

Es el shorthand

Las propiedades completas son:

```css
background-color: /* para definir un color de fondo */

background-image: url(imagen.png); /* para colocar una imagen de fondo */

background-repeat: /* para definir como se repite la imagen de fondo
se pueden definir 4 valores distintos: 
    - repeat: este es el valor por defecto, el fondo se repetira siempre y cuando tenga el espacio para hacerlo
    - no-repeat: el fondo no se repetira
    - repeat-x: el fondo solo se repetira en el eje x
    - repeat-y: el fondo solo se repetira en el eje y */

background-clip: /* nos ayuda a indicar desde que punto va a iniciar la imagen que hemos colocado */

background-origin: /* nos ayuda a indicar desde donde se empieza a dibujar la imagen que hemos colocado */

background-size: /* para definir el tamaño del fondo
se puede definir con los siguientes valores:
    - width=height:
    - width, height:
    - contain: hace que la imagen se abarca lo mas que pueda
    - cover: estira todo lo posible para cubrir todo el fondo
    - auto: le deja su tamaño original a la imagen */

background-position: /* nos ayuda a posicionar el fondo lo podemos definir con: 
un valor en x, un valor con x y, usar palabras clave left,center,right <unit> (para el eje x) y top,center,bottom <unit>(para el eje y) */

background-attachment: /* como se dibuja el fondo respecto al viewport
se puede definir con:
    - fixed: mantiene fijo el fondo
    - scroll: este es el valor por defecto
    - local: hace scroll si el elemento tiene scroll
*/
```

## Unidades em y rem

- em: tamaño de fuente del contexto.

- rem: tamaño de fuente de root.

```html
<h1>Hola<span>Mundo</span></h1>
```

```css
h1{
    font-size: 4em;
}

span{
    font-size: 1em;
}
```

Aunque estamos usando distintas medidas en el font-size de h1 y span en pantalla se van a mostrar del mismo tamaño esto debido a que em es relativo al contexto donde esta, por lo tanto para el span 1em equivale a los 4em de su 'padre' que es el h1 en el caso de rem este no se ve afectado por el contexto por lo cual mantiene una medida normal.

## Texto

```css
direction: /* nos permite definir la direccion del texto
podemos definirlo con dos valores:
    - ltr: de izquierda a derecha
    - rtl: de derecha a izquierda
*/

text-indent: /* nos permite aplicar una sangria al texto */

text-align /* Alinea el texto
lo podemos definir con los siguientes valores
    - start
    - end
    - left
    - center
    - right
    - justify
*/

line-height: /* nos permite definir la altura de los textos
podemos definirlo con unidades exactas, lo recomendable seria em
pero tambien podemos colocar simplemente numeros, por ejemplo:

line-height: 1.1;

*/

vertical-align: /* Para alinear el texto verticalmente
podemos definirlo con los valores de:
    - top
    - middle
    - bottom
    - baseline

    esto puede ser muy util para acomodar iconos que esten alineados con nuestros textos
*/

letter-spacing: /* espaciado entre las letras */

word-spacing: /* espaciado entre las palabras*/

text-decoration: /* nos permite agregar subrayado a nuestros textos */

text-decoration-color: /* underline, overline o line-through*/

text-decoration-style: /* Se pueden agregar los mismos estilos que a los bordes */

text-shadow: /* Nos permite generar sombras 
ejemplo de uso:
text-shadow: 2px 2px 0 red;
*/

white-space: /* nos permiten manejar los espacios en blanco
lo podemos definir con:
    - normal: ignora los espacios en blanco
    - pre: tal como lo escribes asi aparece
    - pre-wrap: salta de linea y conserva espacios
    - pre-line: salta de linea y no conserva espacios
*/

word-break /* parte las palabras para evitar el desbordamiento */

word-wrap /* parte la palabras si la palabra es mas larga que el contenedor para evitar el desbordamiento */

text-overflow /* nos da opciones para cuando los textos no entran */

writing-mode: vertical-lr /* para colocar el texto de manera vertical */

text-orientation: upright /* funciona con la propiedad anterior, nos permite voltear las letras */

text-transform: /* para transformar el texto ya sea a minusculas o mayusculas
lo podemos definir con los siguientes valores:
    - uppercase: todo el texto se transforma a mayuscula
    - lowercase: todo el texto se transforma a minuscula
    - capitalize: la primera letra de cada palabra se transforma a mayusucula
*/
```

## Propiedades de fuentes

Los textos y las fuentes son distintos, el texto es el contenido, la fuente es el tipo de letra.

```css
font-family: /* Esta es la familia de fuentes */
font-size: /* Tamaño de las fuentes */
font-style: /* el estilo de las letras, pero no todas las tipografias pueden tener estas variaciones */
font-weight: /* El grosor de las letras, pero no todas las tipografias pueden tener estas variaciones */
font-variant: /* permite crear versalitas */
font: /* Este es el shorthand se define con (font-size font-family / line-height) */
font-face: /* Esa una @rule que te permite usar la fuente que nosotros queramos */
```

## PseudoElementos

Elemento: hablando en terminos de web, un elemento es una etiqueta html los tenemos de dos tipos:

- ::first-line | ::first-letter
- ::before | ::after

```css
::first-line
/* Ejemplo de uso:
<p>Este es un texto de ejemplo, el cual debe ser un poco largo para que se divida en mas de una linea</p>

P::first-line{
    color: red;
}
```

Esto va a hacer que la primera linea del texto aparezca en rojo, si estiramos o achicamos la ventana del navegador veremos el efecto mejor aplicado ya que a medida la ventana del navegador se vaya encogiendo el texto va a irse acomodando y este pseudolemento hara que solo la primera linea de todo el texto este en rojo a pesar de que el texto se vaya acomodando.

```css
::first-letter
/* aplica igual que firstline pero solo para la primera letra */

::before
/* define un hijo al inicio de un elemento */

::after
/* define un hijo al final de un elemento */
```

Un ejemplo de como se usan estos dos pseudoelementos:

```html
<h1>Cual es tu nombre</h1>
```

```css
h1::before{
    content: '¿'
}

h1::after{
    content: '?'
}
```

Esto hara que cuando el texto de h1 se muestre se inserten los signos de interrogacion que hemos definido.

## Como mantenerse actualizado

> Aprende más con el [Vocabulario CSS](http://apps.workflower.fi/vocabs/css/es)
>
> Documentación de [MDN](https://developer.mozilla.org/es/docs/Web/CSS/Syntax) (Mozilla Developer Network) es el sitio web oficial de Mozilla para la documentación de estándares web y de los proyectos de Mozilla.