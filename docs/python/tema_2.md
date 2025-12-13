# ESTRUCTURAS DE CONTROL

## IF ELSE

Usamos para crear condiciones `if` y para continuarlas o finalizarlas usamos `else` aunque este es opcional.

~~~~python
n = 20
if n > 0:
    print(n," es mayor a 0")
elif n == 0:
    print("El número es 0")
else:
    print("El número es menor a 0")
~~~~

## MATCH

Se declara con un `match` y los casos con un `case`  
Para indicar una condición en función de un valor específico, puede haber más de un valor por caso con `valor1 | valor2:`.  

~~~~python
hora = int(input("Introduce la hora: "))
match hora:
    case 8|9:
        print("Desayuno")
    case 14|13:
        print("Comida")
    case 21|22:
        print("Cena")
    case _:
        print("No toca comer")
~~~~

## WHILE

Se declara con un `while` y se ejecuta hasta cumplir una condición.

~~~~python
contador = 0

while contador < 5:
    print("Contador:", contador)
    contador += 1  
~~~~

## FOR

Usamos `for` junto con `range()` para repetir un bloque de código recorriendo una secuencia de números.

### FOR TIPO 1

Si es `range(n)` entonces indica que el número de repeticiones es `n-1`  

- Ejemplo: Asciende desde 1 hasta 6 de 1 en 1.

~~~~python
for i in range(6):
    print(i) #0, 1, 2, 3, 4, 5
~~~~

### FOR TIPO 2

En este caso `range(inicio, fin, paso)` genera números desde `inicio` hasta `fin`, con un `paso`  
Teniendo en cuenta que `fin` es `fin-1`  

- Ejemplo: Asciende desde 5 hasta 20 de 2 en 2.

~~~~python
for i in range(5, 20, 2):
    print(i) #5,7,9,11,13,15,17,19
~~~~

### FOR TIPO 3

Es lo mismo que el **tipo 2**, la diferencia que este caso es un descenso.  

- Ejemplo: Desciende de 5 a 0.

~~~~python
for i in range (5, 0, -1):
    print(i) #5,4,3,2,1
~~~~

## EXEPCIONES

Tenemos `try`, que contiene el código que puede provocar un error.  
Si ocurre un error, `except` se encarga de manejarlo.  
Si no ocurre ningún error, se ejecuta `else`.  
Por último, independientemente de si hay error o no, `finally` siempre se ejecuta.  

~~~~python
try:
    a=int(input("Introduce un número: "))
    b=int(input("Introduce un número: "))
    print(f"La división {a} / {b} es = {a/b}")
except ZeroDivisionError:
    print('No se puede dividir entre 0')
except ValueError:
    print('Debes introducir números')
else:
    print('Programa finalizado correctamente')
finally:
    print('Adios !')
~~~~
