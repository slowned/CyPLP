
# CONCEPTOS Y PARADIGMAS DE LENGUAJES DE PROGRAMACION
## trabajo integrador 2020


## Integrantes del grupo

* Franceschi Luis, legajo 4343/2
* Murguia Imanol Matias, legajo 10770/6
* Otero Llambay Mariano, legajo 11335/5
* Solar Jonatan Matias, legajo 8396/0

## Lenguajes asignados

* Python
* Processing

### Bibliografía utilizada

* https://docs.python.org/3.9/reference/index.html
* https://entrenamiento-python-basico.readthedocs.io/es/latest/
* https://nedbatchelder.com/text/names.html
* https://processing.org/reference/
* Processing: a programming handbook for visual designers and artists, de Casey Reas y Ben Fry - The MIT Press
* Programming 101: The How and Why of Programming Revealed Using the Processing Programming Language, de Jeanine Meyer - Apress

<div style="page-break-after: always;"></div>

**A. Enuncie y compare distintas caracteristicas (o criterios de evaluación) de cada uno
de los lenguajes asignados funcamentando cada uno con ejemplos de código.**

* **Processing** es un Framework basado en Java, orientado a diseño grafico,
asi mismo brinda la posibilidad de crear código basado en otros lenguajes como javascript, python y ruby.
Sin embargo es importante mencionar que en la misma documentación del framework se hace hincapié a tratar
de no usar librerías externas al Framework puesto a la posibilidad de romper funcionalidades en el mismo.
* **Python** es un lenguaje de programación de alto nivel, interpretado, de propósito general.

#### Simplicidad y legibilidad.
  Python hace hincapié en la legibilidad del código, se siguen reglas de PEP8 para que todos escribamos de la misma manera.
  El equivalente en processing al "Hello World" es dibujar una línea simple:
```processing
line(15, 25, 70, 90);
```

En python un “Hello World” se vería de esta forma:
```python
print(“Hello World”)
```

Podemos nombrar a Processing como un lenguaje menos simple que Python, al tratarse de un 
lenguaje con mayor cantidad de palabras reservadas, así como reglas sintácticas a seguir,
como puede ser el uso de ; para finalizar la línea, llaves de apertura y cierre de bloques,
la definición del tipo retornado por una función (void en caso de no retornar nada), entre otros.

Processing.
```processing
float y = 100;
void setup() {
  size(640, 360);  // Size should be the first statement
  stroke(255);     // Set stroke color to white
  noLoop();
  
  y = height * 0.5;
}

void draw() { 
  background(0);   // Set the background to black
  line(0, y, width, y);  
  
  y = y - 1; 
  if (y < 0) { 
    y = height; 
  } 
} 

void mousePressed() {
  loop();
}
```

Python.
```python
y = 100

def setup()
  size(640, 360)
  stroke(255)
  noLoop()
  y = height * 0.5

def draw()
  background(0)
  line(0, y, width, y)
  y = y - 1 

  if y < 0:
    y = height

def mousePressed()
  loop()
```


#### Claridad en los bindings
* **Python**
Acorde a lo mencionado en el punto anterior acerca de las reglas sobre las que se basa el lenguaje,
en su definición no hay complejidad operativa que conlleve al programador a cometer errores en la escritura de sus programas.
Dando como ejemplo las operaciones aritméticas la escritura del programa es aún clara
para los casos donde se construyen operaciones complejas. En este mismo sentido,
la interpretación de los programas se realizan de forma sencilla procesando de izquierda a derecha
teniendo en cuenta la prioridad de operadores.
Además de esto para distintos “tipos” de datos pueden utilizarse los mismos símbolos del lenguaje pero
con diferente fin, siendo de fácil entendimiento, como lo es el uso de “+” en operaciones aritméticas,
concatenación de cadenas de texto o incremento de valores

```python
suma = (2 + num5) * (2/(num1 * num2 * num3))
```
* **Processing**
Siendo Processing un framework para desarrollo visual o gráfico es claro que la mayor parte de las operaciones realizadas en él son a través de métodos, es decir, haciendo el llamado a funciones con un propósito específico. Pueden como cualquier otra función recibir parámetros en caso que el método lo permita y de esta forma tener sobrecarga de métodos.
Al resumirse mayormente en la utilización de métodos o funciones la complejidad simplemente es reducida y la curva de aprendizaje de la herramienta es cómoda para quien este interesado.
Ahora bien, no todo se realiza mediante funciones sino que es posible utilizar comparadores (mayor que, mayor o igual que, menor, igual, etc) y los mismos símbolos no son utilizados para realizar otras operaciones. Esto está acotado dado que el propósito del framework no es general sino para un ambiente de desarrollo de artes visuales.

#### Confiabilidad
* **Python**
Siendo un lenguaje interpretado, la detección de los errores es detectada al momento de la ejecución de las sentencias,
el compilador se encarga de interpretar instrucción a instrucción y en caso de por ejemplo querer sumar a un valor
numérico el valor almacenado en otra variable sin esta haber sido inicializada producirá un error. 
Por tanto, la detección de los errores y el soporte de confiabilidad que provee el lenguaje están estrictamente
ligados a la ejecución del programa y su correción por parte del desarrollador
. El lenguaje provee mecanismos para poder evitar ciertos errores basando en la utilización de lo que llamamos excepciones.
De esta forma, podríamos evitar la interrupción del programa o al menos poder realizar acciones adicionales antes de que esto suceda.
Este soporte también debe ser implicitamente agregado por el desarrollador en cada lugar que considere podría sucederse algún inconveniente.
Por ej: intentar abrir archivos en un directorio que el usuario ingresa para copiarlo a otra ubicación,
podría sucederse que el archivo de origen no exista o aún el path no exista.
Entonces en estás situaciones el desarrollador puede agregar implicitamente la “validación” de si existe el directorio/archivo,
caso contrario informa el error y la ejecución del programa continua sin interrumpirse.

* **Processing**
Al igual que Python es posible realizar de forma implícita el tratamiento de errores.

```processing
// Ejemplo
BufferedReader reader;
String line;
 
void setup() {
  // Open the file from the createWriter() example
  reader = createReader("positions.txt");    
}
 
void draw() {
  try {
    line = reader.readLine();
  } catch (IOException e) {
    e.printStackTrace();
    line = null;
  }
  if (line == null) {
    // Stop reading because of an error or file is empty
    noLoop();  
  } else {
    String[] pieces = split(line, TAB);
    int x = int(pieces[0]);
    int y = int(pieces[1]);
    point(x, y);
  }
}
```
Se presenta aquí el tratamiento de recuperación del programa por error de lectura de archivo. Similar a lo que realiza Python, se tiene un bloque de código encerrado en una sección “try” y en “catch” la/s posible/s solución/es según el error ocurrido. Esto nos permite continuar la ejecución del programa sin detenerlo abruptamente.
En cuanto a los tipos y su declaración, es necesario realizar esto antes de darles uso, en este aspecto el lenguaje se apoya en el soporte que brinda el lenguaje Java donde el programa al compilarse es puesto a prueba en su sintaxis y semántica para de esta forma poder descubrir los errores antes que el mismo sea ejecutado.

#### Soporte
* **Python**
Es administrado por la Python Software Foundation. Posee una licencia de código abierto,
denominada Python Software Foundation License,3 que es compatible con la Licencia pública general de GNU.
En el sitio oficial de python se encuentra disponible el codigo fuente asi como "releases" para la gran mayoría
de los sistemas operativos: Linux, Windows, Mac OS X, y diversas versiones de UNIX.
Alli tambien esta disponible la documentación oficial, clasificada según varios criterios:
nivel, idioma, tipo (escrito o audiovisual)
Además de la implementación oficial en C, que es la más ampliamente usada,
existen otras implementaciones en otros lenguajes por ejemplo: .NET (IronPython), java (Jython), python (PyPy)


* **Processing**
Es administrado por la Processing Foundation, que desarrolla y distribuye bajo una licencia LGPL,
varias implementaciones de Processing en distintos lenguajes: Processing (Java), p5.js (JavaScript) y Processing.py (Python)
El código fuente se encuentra disponible en Github y en el sitio oficial de Processing podemos descargar el ejecutable y
al estar desarrollado en Java es multiplataforma.
El sitio cuenta con documentación oficial y referencias a libros que ahondan en distintos aspectos del lenguaje.

> **Si bien hasta aquí el soporte de ambos lenguajes es similar, Python con una comunidad de usuarios mucho más grande que Processing.**

#### Abstracción 
Tanto Python como Processing tiene soporte para abstracción mediante el uso de clases abstractas,
las cuales tienen uno o más métodos abstractos, es decir sin implementación.
Subclases de la clase abstracta proveen la implementación de los métodos abstractos.
#### Ortogonalidad 
Se refiere al significado de las palabras reservadas o simbolos.
Si una palabra reservada siempre tiene el mismo significado independientemente del
contexto en que se use el lenguaje tiene una mayor ortogonalidad.
Un ejemplo es el signicado de "+" si siempre representa la suma aritimetica es ortogonal,
pero si representa a la suma para variables numéricas y concatenación para strings entonces
es menos ortogonal.
Un lenguaje con caracteristicas ortogonales, nos da la facilidad de aprenderlo mas rapido, ya que existen menos excepciones y casos
especiales para tener en cuenta
* Ortogonalidad en Python.
**Python** y **Processing** provee una gran cantidad de palabras reservadas que nos permite utilizarlas en cualquier momento
y siempre tener el mismo resultado, aunque posee algunas excepciones como en caso mencionado con el caracter "+"


**B. Defina y compare diferentes aspectos de la sintaxis que Ud. considere. Ejemplifique.**

A continuacion vamos a comparar los tipos de sintaxis entre 
__Python__ y __processing__ utilizando de ejmeplo una iteracion, donde
se almacena el el resultado de la suma entre los 10 primeros numeros,
empezando de 1.

Ejemplo de for en python
```python
suma = 0
for numero in range(1, 10+1):
  suma += numero
```

Ejemplo de for en processing
```processing
int suma = 0;
for(int numero = 1; numero <= 10; numero++) {
  suma += numero
}
```
En python se utiliza las palabras reservada **for** al igual que en processing,
las diferencias estan en como se contruye la condicion y de la forma en
estos lenguajes identifican el bloque de iteracion.

En el ejemplo de python vemos que el for se construye de la forma
"**para cada** elemento **dentro** de una coleccion" repetir boque, los 
dos puntos (**:**) despues de la condicion marcan el comienzo del bloque
a ejecutar, si cuenta con mas de una linea, esté se escribe 
indentado por 4 espacios una abajo de la otra. Mientras que en el
ejemplo de processing la condicion la podemos dividir en 3 pasos
en el primero se declara una variable de inicio al loop, en el segundo
paso se encuentra la verificacion de la condicion, si nuestra variable
de inicio cumple con el valor de corte y por ultimo se incrementa la 
variable de inicio. La condicion siempre se encuentra entre parentesis
y el bloque de codigo entre llaves **{ bloque }**
al loop 



**Tipos de sintaxis:**
* Abstracta: Mismas estructuras, ambos lenguajes tienen la misma
estructura **for** condicion bloque.
* Concreata: Diferencias lexicas. la condicion en python se define entre
la palabra reservada for y los dos puntos mientras que en processing la
condicion debe estar dentro de los parentesis, la suma y asignacion se
escribe de la misma manera y por ultimo se puede observar que en processing
es necesario definirle el tipo de la variable mientras que en python no
* Pracmatica: dentro del contexto de estos ejemplos planteados se comprende
mas el primer ejemplo donde vemos que el bloque for se itera dentro de un rango,
mientras que en el segundo se depende de una condicion de corte, incremento del indice.


**C. Enuncie y compare distintos aspectos semánticos (tanto de la semántica estática y dinámica)
de cada uno de los lenguajes asignados.**

Analizaremos los siguientes puntos desde la perspectiva semántica estática y dinámica,
recurriendo a ejemplos para brindar mayor entendimiento de lo evaluado.
*  Indentación
*  Declaración de variables
*  Tratamiento de excepciones
*  Comentarios
*  Expresiones condicionales (IF)

Teniendo presente el siguiente ejemplo escrito en Python explicaremos los puntos antes mencionados. 

```python
# INICIO PROGRAMA
pares = 0  # linea 1
impares = 0  # linea 2
lista_numeros = [1, 2, 4, 8, 15]  # linea 3
for num in lista_numeros:  # linea 4
  if num % 2 == 0:  # linea 5
    print("Es par")  # linea 6
    pares += 1  # linea 7
  else:  # linea 8
    print("Es Impar")  # linea 9
    impares += 1  # linea 10
print(f"Cantidad de numeros pares: {pares}")  # linea 11
print(f"Cantidad de numeros impares: {impares}")  # linea 12
# FIN PROGRAMA
```

#### Indentación
Dentro del lenguaje Python deben agregarse espacios en blanco (4) al
comienzo de una línea lógica (línea 6), agrupando así un conjunto
de sentencias (líneas 7 y 8 o líneas 9 y 10). 
De esta forma al asociarlas se ejecutarán conjuntamente por ejemplo si
fuesen agrupadas dentro de una sentencia if (línea 5) teniendo 
un significado durante ejecución diferente si no estuviesen indentadas;
caso donde se produciría un error al interpretar el código.
La escritura incorrecta de una indentación (línea 10) podría cambiar el sentido
lógico de un programa definido dando como resultado números impares tantos como
hayan definidos en la variable "lis", por lo tanto en este sentido la 
característica de indentación en el lenguaje puede tener
efecto tanto en semántica estática como dinámica. 
Estática ya que como bien mencionamos el significado no es el mismo
y dinámico porque el resultado en ejecución en caso del ejemplo presentado,
no produciría una correcta salida de la intención propuesta en la lógica del programa.

En Processing la indentación y los espacios en blanco en general no tiene ningun
efecto sintactico ni semantico, los siguientes dos ejemplos de código
producen exactamente el mismo resultado:

```processing
// ejemplo a:
int x = 50;
if (x > 100) {
    line(20, 20, 80, 80);
} else {
    line(80, 20, 20, 80);
}

// ejemplo b:
int x = 50;
if (x > 100) {
line(20, 20, 80, 80);
} else {                    
line(80, 20, 20, 80);
}
```


Python no aplica esta característica al ser un lenguaje dinámicamente tipado,
es decir, que una variable puede cambiar su tipo de dato almacenado sin restricción.
No hay una sintaxis definida para tal característica.
Si podemos destacar que al cambiar el tipo de valor almacenado en ejecución sucede
una modificación a nivel puntero de la zona de memoria que contendrá este valor.

En Processing es fuertemente tipado, demás, el tipado es estático,
una vez que se le asigna un tipo a una variable no puede ser cambiado
en subsiguientes líneas de código.

#### Tratamiento de excepciones
* Manejo de excepciones en python.
```python
try:
  numero1 = input("Numero 1")
  numero2 = input("Numero 2")
  division = numero1 % numero2
  print(f"Resultado de dividir {numero1} % {numero2} es {division}")
except ZeroDivisionError:
  print("Division por cero erronea")
finally:
  print("finalizó el programa")
```
	
En Python son construidas en base a la característica de la indentación tratada anteriormente.
Su implicancia en la semántica estática se produce por la generación de indentaciones construidas
correctamente para dar sentido lógico al programa.
En otro caso en tiempos de ejecución se obtendría el resultado o efecto (semántica dinámica) no deseado,
como ser una operación matemática no necesaria.

En Processing también utiliza try para definir el bloque de código dentro del
cual se quiere manejar la excepción, y catch para definir el código que debe
ejecutarse si la excepción se ocurre.


* Manejo de excepciones en processing
```processing
BufferedReader reader;
String line;
 
void setup() {
  // Open the file from the createWriter() example
  reader = createReader("positions.txt");    
}
 
void draw() {
  try {
    line = reader.readLine();
  } catch (IOException e) {
    e.printStackTrace();
    line = null;
  }
  if (line == null) {
    // Stop reading because of an error or file is empty
    noLoop();  
  } else {
    String[] pieces = split(line, TAB);
    int x = int(pieces[0]);
    int y = int(pieces[1]);
    point(x, y);
  }
}
```

#### Comentarios
Dentro del lenguaje Python simplemente tendrán significado semántico pudiendo
ser de ayuda para el lector del código fuente, sin embargo su agregado
no produce ningún impacto a nivel ejecución lógico del programa ya que su
definición misma le indica al intérprete que no debe ser ejecutada como parte del programa.

* Comentarios en python
```python
# Comentario para una sola lina
contador = 0  # inicializa variable contador

"""
Esto es un Comentario de muchas lineas
generalemte se utillizan como docstrings
de las funciones como una minuma ayuda de que parametros recibe y 
que parametros retorna...
"""
```

* COmentarios en processing
En Processing los comentarios funcionan de la misma manera y se pueden incluir de tres formas: 
```processing
// para comentar el resto de la linea.

/* 
 para abrir y cerrar un comentario de varias líneas.
 COMENTARIO
 COMENTARIO
*/
/**
 para abrir y cerrar un comentario de documentación.
*/
```

#### Expresiones condicionales (IF)
En **Python** se evalúan tanto los operadores como operandos involucrados en la sentencia,
tomando un camino u otro según el resultado lógico obtenido.
Su impacto puede apreciarse en ambas semánticas tal como vimos con
el ejemplo anterior de números pares/impares.
Las formas válidas de construir una expresión condicional nos permitirán
tener complejas evaluaciones que en tiempo de ejecución nos permitirán ejecutar
ciertas porciones de código específico llegando muy posiblemente a un final de
programa diferente según el camino tomado.

En **Processing** el condicional IF funciona de la misma manera,
pero requiere que el valor a evaluar esté entre paréntesis.
