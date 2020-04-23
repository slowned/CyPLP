**A. Enuncie y compare distintas caracteristicas (o criterios de evaluación) de cada uno
de los lenguajes asignados funcamentando cada uno con ejemplos de código.**

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

**Indentación:**
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




**Declaración de variables:**
Python no aplica esta característica al ser un lenguaje dinámicamente tipado,
es decir, que una variable puede cambiar su tipo de dato almacenado sin restricción.
No hay una sintaxis definida para tal característica.
Si podemos destacar que al cambiar el tipo de valor almacenado en ejecución sucede
una modificación a nivel puntero de la zona de memoria que contendrá este valor.

En Processing es fuertemente tipado, demás, el tipado es estático,
una vez que se le asigna un tipo a una variable no puede ser cambiado
en subsiguientes líneas de código.

**Tratamiento de excepciones:**
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


**Comentarios**
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

**Expresiones condicionales (IF)**
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
