###**B.Defina y compare diferentes aspectos de la sintaxis que Ud. considere. Ejemplifique.**

A continuacion vamos a comparar los tipos de sintaxis entre 
__Python__ y __processing__ utilizando de ejmeplo una iteracion, donde
se almacena el el resultado de la suma entre los 10 primeros numeros,
empezando de 1.

```python3.7
suma = 0
for numero in range(1, 10+1):
  suma += numero
```

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



