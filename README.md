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
- Imprimimos nuestro resultado
-----------------------------------
### 2. Desarrollar un algoritmo que permita realizar el producto de matrices.

```python
from Reto11_1 import *
if __name__=="__main__":
    m1=generarmatriz(1)
    m2=generarmatriz(2)
    #generamos ambas matrices
    if len(m1)==1: #caso 1, m1 es una escalar
     mt:list=[]
     for i in range(len(m2)): #recorremos las filas
        lt:list=[] #generamos la lista que alamacenara las variables para despues añadirlas como fila en la matriz, se ira reiniciando por cada ciclo
        for j in range(len(m2[0])): #recorremos las columnas
          lt.append(m2[i][j]*m1[0][0]) #añadimos el producto del valor de m2[i][j] por nuestro escalar a la fila
        mt.append(lt) #añadimos la fila a la matriz
    if len(m2)==1: #mismo caso pero si m2 es escalar, no veo necesario explicar aqui
       mt:list=[]
       for i in range(len(m1)):
        lt:list=[]
        for j in range(len(m1[0])):
          lt.append(m2[i][j]*m1[0][0])
        mt.append(lt)
    if len(m1)==len(m2): #caso 2, ambos son matrices con el mismo tamaño
      mt:list=[] #declaramos la matriz
      for i in range(len(m1)): #recorremos las filas
        lt:list=[] #"fila"
        for j in range(len(m1[0])): #recorremos los valores de la fila
            o=0 #declaramos una variable de iteracion
            while o<len(m1): #ciclo while para poder realizar la suma, es una sumatoria hasta len(m1)
                if o==0: #caso inicial
                    R= m1[i][0]*m2[0][j]
                else: #caso posterior
                 R=R+m1[i][o]*m2[o][j]
                o=o+1 #se añade 1 por cada iteracion
            lt.append(R) #se añade nuestro resultado R a la fila
        mt.append(lt) #se añade la fila a la matriz
    print(mt)      #se imprime la matriz resultante
```
#### explicacion:
- Importamos la funcion del punto 1
- En el primer caso se recorre la matriz y se multiplican sus valores por el escalar, similar al punto 1
- Dentro del codigo declaramos 2 matrices, estas seran las que usaremos para realizar el producto
- En el primer caso se recorre la matriz y se multiplican sus valores por el escalar, similar al punto 1
- Para el caso 2 El producto punto de 2 matrices esta compuesta por items que son el resultado de la siguiente sumatoria
- ![image](https://github.com/user-attachments/assets/8f774ff3-e3b9-4842-93b9-0ee9d7aacd0c)
- Para esto se logro llegar al siguiente proceso para emular la sumatoria
- ![image](https://github.com/user-attachments/assets/0b01cac7-c803-4373-a48e-1435a5c8fe04)
- recorremos la matriz con los 2 for, es importante prestar atencion a que i es la fila y j es la columna
- dentro del segundo for realizamos un ciclo while que vaya a representar nuestra sumatoria
- en este ciclo while o representara el valor de iteraicon con un caso base y un caso de iteracion, generando la sumatoria mostrada con anterioridad
- el resultado de esta sumatoria sera el item que añadiremos a la fila, este proceso se repetira j veces y la lista resultante se añadira a la matriz
- Se imrprime nuestro resultado
-----------------------------------
### 3. Desarrollar un algoritmo que permita obtener una matriz transpuesta.
```python
from Reto11_1 import *
if __name__=="__main__":
    m1=generarmatriz(1) #generamos la matriz
    mt:list=[] #declaramos la lista en donde pondremos el resultado
    y=len(m1) #declaramos y como la cantidad de filas
    x=len(m1[0]) #declaramos x como la cantidad de valores en la fila (columnas)
    for i in range (x): #usamos el for que recorrera las filas, pero esta estara limitado a la cantidad de columnas
        lt:list=[] #creamos la lista en donde añadiremos valores para la fila i
        for j in range (y): #recorremos las columnas, esta vez limitado a la cantidad de filas de la matriz original
            lt.append(m1[j][i]) #añadimos a la matriz resultante el valor, pero esta vez con los valores de indexacion invertidos
        mt.append(lt) #añadimos la lista a la matriz
    print(mt) #imprimimos nuestra matriz resultante
```
#### explicacion:
- Importamos la funcion del punto 1
- Dentro del codigo declaramos una lista, esta sera nuestra matriz resultante
- La matriz transpuesta es el resultado de invertir los valores de indexacion de una lista
- ![image](https://github.com/user-attachments/assets/492f5c9e-678b-42b0-a424-4d65f9fa19bd)
- ![image](https://github.com/user-attachments/assets/53ef3faa-9dbe-43ca-a383-4b9b913a06c8)
- Para generar una matriz asi es necesario que esten invertidos los valores de filas y columnas
- declramos 2 variables (x e y) para identificar x (horizontal) como la cantidad de valores por filas (columnas) e y (vertical) como la cantidad de filas
- Realizamos el usual recorrido por 2 ciclos for, pero esta vez el rango estara invertido entre columnas y filas para que la matriz se genere con los valores inversos de x e y en realcion con la original
- dentro del segundo for añadimos a la lista el valor [j][i] de la matriz original, asi tendremos en el lugar original el valor de index invertido
- añadidos todos los valores a la lista i se añade a la matriz
- Finalizado el proceso se imrprime la matriz
-----------------------------------

### 4. Desarrollar un programa que sume los elementos de una columna dada de una matriz.
```python
from Reto11_1 import *
if __name__=="__main__":
    m1=generarmatriz(1) #generamos matriz
    v:float=float(input("cual columna desea sumar?")) #preguntamos al usuario que columna desea sumar
    lt:list=[] #esta vez solo creamos la lista
    o=0 #declaramos una variable de iteraicon
    y=len(m1) 
    x=len(m1[0])
    #x e y que representen la cantidad de columnas y filas respectivamente
    if v>x or v<1: #caso en que la columna que se desea sumar no exista
        print("no se puede sumar esa columna porquen o existe")
    else: 
        for i in range (y): #recorremos las filas normalmente
            for j in range (x): #recorremos las columnas
                if j==(v-1): #condicional a la que solo entraran los valores dentro de la columna que deseamos sumar
                    lt.append(m1[i][j]) #añadimos el valor a la lista resultante
        #completado el proceso pasamos a un ciclo
        while o<len(lt): #ciclo while que se mantendra hasta la longitud de la lista
            if o==0: #caso inicial
                s=lt[o] #una variable s sera igual al primer valor de la lista
            else: #caso de iteracion
                s=s+lt[o] #se le sumara a s el valor o de la lista hasta que se complete
            o=o+1 #aumento de la variable de la iteracion
        print("el resultado de la suma es " + str(s)) #se escribe de manera comprensible
```
### explicacion:
- Importamos la funcion del punto 1
- generamos una matriz con la funcion importada
- declaramos v como una variable que el usuario decidira cual es su valor, de esta dependera el numero de la columna que se sumara
- creamos de una vez la lista resultante, esto porque para este punto no se necesita generar otra matriz
- declaramos o como una variable de iteracion y a x e y como la cantidad de columnas y filas (como en el punto anterior)
- usando un condicional declaramos el posible caso donde el numero ingresado no sea el de una columna, en este caso avisamos al usuario y acabamos el codigo
- caso contrario realizamos el recorrido comun de 2 for por filas y columnas
- dentro del for de las columnas añadimos otro condicional, en el cual se evaluara si j es igual al numero de columna indicado, si es asi se añadira el valor y si no se pasara al siguiente
- completada la lista nos adentraremos a una ciclo while que durara hasta que o llege al valor de la longitud de la lista
- con un if realizamos un caso inicial y un caso de iteracion, esto para emular una sumatoria (la suma de las columnas)
- aumentamos la variable de iteracion por cada ciclo
- completada la sumatoria la imrpimimos de forma comprensible para el usuario
-----------------------------------

### 5. Desarrollar un programa que sume los elementos de una fila dada de una matriz.
```python
from Reto11_1 import *
if __name__=="__main__":
    m1=generarmatriz(1) #generamos la matriz
    v:float=float(input("cual fila desea sumar?")) #declaramos una variable para que el usuario indique la fila a sumar
    lt:list=[] #declaramos la lista en donde añadiremos los valores de la fila
    o=0 #variable de iteracion
    y=len(m1) #cantidad de filas
    x=len(m1[0]) #cantidad de columnas
    if v>y or v<1: #caso en que la fila que se desea sumar no exista
        print("no se puede sumar esa columna porquen o existe")
    else: #caso en que la fila si exista
        for i in range (y): #recorremos las filas
            if i==(v-1): #condicional que solo entrara en la fila que deseamos sumar
                for j in range (x): #recorremos las columnas
                    lt.append(m1[i][j]) #añadimos los valores de la fila a la lista
        while o<len(lt): #ciclo while que se mantendra hasta la longitud de la lista, representa una sumatoria
            if o==0: #caso inicial
                s=lt[o] #variable s sera igual al primer valor de la lista
            else: #caso de iteracion
                s=s+lt[o]   #se le sumara a s el valor o de la lista hasta que se complete
            o=o+1 #aumento de la variable de la iteracion
        print("el resultado de la suma es " + str(s)) #se escribe de manera comprensible
```
### explicacion:
- Importamos la funcion del punto 1
- generamos una matriz con la funcion importada
- declaramos v como una variable que el usuario decidira cual es su valor, de esta dependera el numero de la fila que se sumara
- creamos de una vez la lista resultante, esto porque para este punto no se necesita generar otra matriz
- declaramos o como una variable de iteracion y a x e y como la cantidad de columnas y filas (como en el punto anterior)
- usando un condicional declaramos el posible caso donde el numero ingresado no sea el de una fila, en este caso avisamos al usuario y acabamos el codigo
- caso contrario realizamos el recorrido comun de 2 for por filas y columnas
- dentro del for de las filas añadimos otro condicional, en el cual se evaluara si i es igual al numero de fila indicado, si es asi se añadira el valor y si no se pasara al siguiente
- completada la lista nos adentraremos a una ciclo while que durara hasta que o llege al valor de la longitud de la lista
- con un if realizamos un caso inicial y un caso de iteracion, esto para emular una sumatoria (la suma de las columnas)
- aumentamos la variable de iteracion por cada ciclo
- completada la sumatoria la imrpimimos de forma comprensible para el usuario
  
