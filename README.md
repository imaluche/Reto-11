# Reto-10 programacion de computadoras
----------------------------------

### 1. Desarrollar un algoritmo que calcule el promedio de un arreglo de reales.

```python
def adicionlista(l:list,k:bool):
    # Definimos una funcion para añadir elementos a una lista
    i=1
    while i==1:
        e= float(input("ingresa un numero, si no ingresas un numero entero o decimal el programa no funcionara correctamente:"))
        l.append(e)
        i=int(input("deseas ingresar otro numero? (1, cualquier otro numero para no)"))
    if k==True: print("nuestra primera lista fue: "+ str(l)+ ", la siguiente lista no debe tener mas de "+ str(len(l))+" elementos")
    else: print("nuestra segunda lista fue: "+ str(l)+ ", tiene "+ str(len(l))+" elementos.")
    #por medio de un booleano damos diferentes opciones de salida

#declaramos la lista a analizar

if __name__ == "__main__":
    p:list=[]
    adicionlista(p,False) 
    #aplicamos la funcion para añadir elementos a la lista
    print(p)
    D=sum(p)
    #sumamos los valores de la lista con sum(), de manera alternativa podriamos usar un for y almacenar la suma en una variable
    print(D)
    d=len(p)
    #almacenamos en una variable la longitud de la lista, esto se hara para obtener la media
    ac:float= D/d
    # Dividimos la suma de los valores entre la cantidad, obteniendo la media
    print("el promedio de la lista "+ str(p)+" es "+ str(ac))
    #la imprimimos de manera comprensible

```
#### explicacion:
- Definimos una funcion para añadir elementos a una lista, esta se usara en los siguientes puntos
- Dentro del codigo declaramos una lista vacia
- Aplicamos la funcion en la lista de la cual obtendremos su media
- Usando la funcion "sum" para que los valores de la lista se sumen, de manera alternativa se puede usar un bucle for y almacenar la suma en una variable
- Usamos la funcion len para almacenar en otra variable la longitud de la lista, esto es importante para realizar la media
- declaramos una ultima variable que sera nuestra media, esta es el resultado de la division entre la suma de los valores de la lista (D) y la cantidad de valores (d)
- Imprimimos nuestro resultado de manera que se entienda que es
-----------------------------------
### 2. Desarrollar un algoritmo que calcule el producto punto de dos arreglos de números enteros (reales) de igual tamaño.

```python
from Reto10_1 import adicionlista
#importamos la funcion de Reto10_1
if __name__ == "__main__":
    l1=[]
    l2=[]
    #Declaramos 2 listas las cuales seran en las que realizaremos la operacion
    adicionlista(l1,True)
    adicionlista(l2,False)
    #aplicamos la funcion en ambas listas
    i:int=0
    c:float=0
    #Declaramos 2 variables necesarias para realizar la operacion, inicializadas en 0

    if len(l1)!=len(l2):
        #para evitar errores al realizar la operacion prevenimos el caso en el que las listas no tengan el mismo tamaño acabando el codigo inmediatamente
        print("Las listas deben ser del mismo tamaño")
        exit()
    while i <= ((len(l1))-1):
        #aplicamos un while con i la cual teniamos inicializada en 0 el cual continuara hasta la longitud-1 de las listas
        c=c+(l1[i]*l2[i])
        #operamos para obtener el producto punto de las listas, este es el resultado de multiplicar 2 competentes y sumarlos con el producto de los siguientes 2 componentes.
        i+=1
        #Aumentamos por 1 i, asi avanzara hasta la longitud deseada
    print("El producto punto de las listas es: "+ str(c))
    #imprimimos el resultado del producto punto de manera comprensible
```
#### explicacion:
- Importamos la funcion del punto 1 del reto 10
- Dentro del codigo declaramos 2 listas, estas seran las que usaremos para realizar el producto punto
- El producto punto es el resultado de la suma del producto de los componentes de n listas tal que
- Aplicamos las funcion en ambas listas, usamos True y false para informar sobre cual lista es cada una
- Declaramos 2 variables flotantes iniciadas en 0, estas seran nuestra variable de iteracion y el resultado del producto punto
- Antes de empezar la operacion evaluamos la longitud de ambas listas para evitar errores
- Si no son iguales se cerrara el codigo, esto se advierte desde las funciones para añadir valores.
- En caso de que si sean iguales se continuara el codigo
- Se aplica un ciclo while usando de referencia i, este ciclo se repetira hasta que i deje de ser menor o igual a la longitud de las listas-1
- Dentro del ciclo le sumaremos a la variable c el resultado del producto del valor de la lista que representa i segun la indexacion, esto se guardara en c y se repetira hasta que i pase la longitud de las listas
- Para que i avance se le suma 1 por cada iteracion
- Al salir del bucle tendremos como resultado el producto punto, los imprimos de manera que sea entendible
-----------------------------------
### 3. Hacer un algoritmo que deje al final de un arreglo de números todos los ceros que aparezcan en dicho arreglo.
```python
from Reto10_1 import adicionlista
#Importamos la funcion de Reto10_1
if __name__ == "__main__":
    p:list=[]
    #Declaramos la lista en la cual se realizara el ejercicio
    adicionlista(p,False)
    #Aplicamos la funcion para añadir elementos a la lista
    for i in p:
        #aplicamos un ciclo for para recorrer la lista
        if i/10==i//10:
            #si la division del valor es igual a su divisor exacta podermos decir que es multiplo entero de 10 y por tanto tiene un 0 al final
            p.pop(p.index(i)) 
            #En caso de entrar en la condicional se eliminara el valor de la lista
            p.append(i)
            #y se reañadira al final de la lista
    print(p)
    #se imprime la lista con los valores reorganizados
```
#### explicacion:
- Importamos la funcion del punto 1 del reto 10
- Dentro del codigo declaramos una lista, esta sera en la cual realizaremos el ejercicio
- Aplicamos la funcion en la lista para añadir valores
- Aplicamos un ciclo for para recorrer los datos de la lista
- Dentro del ciclo for aplicamos un condicional if el cual evaluara la igualdad de la division normal y exacta del valor entre 10, esto nos servira para comprobar que el numero tiene un 0 al final.
- En caso de que no sea igual el valor pasara, en caso contrario se quitara el valor de la lista con un pop
- Para despues reañadirlo con un .append, de esta forma aparecera al final de la lista
- Finalizado el proceso se reimprimira la lista reorganizada
-----------------------------------

### 4. Revisar que son los algoritmos de sorting, entender bubble-sort (enlace a implementación).
### explicacion:
- En palabras simple un algoritmo de sorting nos permite organizar una lista/arreglo segun ciertas metricas
- El bubble-sort es uno de estos, es la manera mas simple de organizar elementos de una lista en relacion con su valor numerico.
- En este se comparan los valores en orden con sus adayacentes dentro del contexto de la lista, en caso de ser el primero mayor que el segundo estos intercambian de lugar en la indexacion mientras que si esto no sucede se mantendra en su lugar
- Independientemente de lo que pase se evaluara el siguiente valor de index, repitiendo el proceso hasta que el primer valor mas grande llegue al final de la lista en terminos de index
- Este proceso se repetira con el segundo valor mas grande, el tercero hasta llegar al n valor mas grande
- Este metodo al ser tan simple es facil de entender y es estable, pero suele ser algo lento en comparacion con otros algoritmos y al basarse en comparaciones puede limitar la funcionalidad del algoritmos en ciertos casos
