# Reto-11 programacion de computadoras
----------------------------------

### 1. Desarrollar un algoritmo que permita la suma/resta de matrices

```python
def generarmatriz(n):
  f = int(input("ingresa el numero de filas "))
  c = int(input("ingresa el numero de columnas (cantidad de items de cada fila)"))
  #indica la cantidad de matrices,filas y columnas que se generaran
  matriz=[] #esta sera nuestra matriz en la que añadiremos los valores que desee el usuario
  for j in range(f): #primer for que representa el recorrido por las filas
    print("estamos/seguimos en nuestra "+ str(n)+ " matriz")
    filat=[] #representa la fila en la que se añadiran los items, se vacia cada vez que se cambia de fila
    for i in range(c): #representa el segundo recorrido, esta vez por las columnas
      v= float(input("ingresa el valor " +str(i+1) +" de la fila"+ str(j+1))) #el usuario indica el valor que quiere añadir, estara en el puesto [j][i]
      filat.append(v) #añade el valor a la fila
      print(filat)
    matriz.append(filat) #añadidos todos los valores de la fila se añade la fila a la matriz, siendo nuestra j fila
    print(matriz)
  return matriz #regrese la matriz generada
if __name__ == "__main__":
  print("recordar que ambas matrices deben ser del mismo tamaño para poder realizar la suma o resta")
  m1=generarmatriz(1)
  print(m1)
  m2=generarmatriz(2)
  print(m2)
  #generamos 2 matrices
  if len(m1)==len(m2): #comparamos su longitud para comprobar si ambas matrices son del mismo tamaño
    print("las matrices son del mismo tamaño, es posible realizar la suma y resta")
    d=int(input("ingresa 1 para realizar una suma y 2 para realizar una resta")) #le pedimos al usuario indicar que desea hacer
    if d==1: #caso 1, suma
      mt:list=[] #declaramos la lista que daremos como resultado
      for i in range(len(m1)): #recorremos las filas
        for j in range(len(m1[0])): #recorremos las columnas
          mt.append(m1[i][j]+m2[i][j]) #añadimos a la lista que sera nuestro resultado la suma de los valores [i][j] de ambas matrices
      print(mt) #imprimimos el resultado
    if d==2: #caso 2, resta
      mk:list=[] #declaramos la lista que daremos como resultados
      for i in range(len(m1)): #recorremos las filas
        for j in range(len(m1[0])): #recorremos las columnas
          mk.append(m1[i][j]-m2[i][j]) #añadimos a la lista que sera nuestro resultado la resta de los valores [i][j] de ambas matrices
      print(mk) #imprimimos el resultado
  else: #resultado para indicar que las listas no son del mismo tamaño
    print("las matrices no son del mismo tamaño, no es posible realizar la suma")

```
#### explicacion:
- Definimos una funcion para añadir elementos a una matriz, esta se usara en los siguientes puntos
- Dentro del codigo declaramos una lista vacia que sera el resultado de la operacion
- Aplicamos la funcion en 2 variables que permitan realizar la operacion
- añadimos un condicional que lo unico que haga sea cambiar si se suma o resta, sin realizar un ningun otro cambio en el codigo
- usamos 2 ciclos for para recorrer tanto las filas como columnas
- añadimos a la matriz de resultado la suma de los valores [i][j] de la matriz, de esta forma sabemso que estan en las mismas "coordenadas"
- Imprimimos nuestro resultado de manera que sea comprensible
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
