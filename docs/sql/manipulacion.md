# SQL MANIPULACIÓN

## INSERT INTO

Para insertar registros usamos la siguiente estructura.  
Podemos insertar más de un registro.  
En caso de no rellenar un campo, el valor por defeto será `NULL`  

~~~sql
INSERT INTO empleados(campo1,campo2)
VALUES ("valor1","valor2"), ("valor1","valor2");
~~~

## UPDATE

Podemos modificar una o varias columnas usando `UPDATE`, `SET` y `WHERE`

~~~sql
UPDATE empleado
SET salario = 2000
WHERE dni = '48949040N';
~~~

~~~sql
UPDATE empleado
SET salario = 2000, cod_dpto = 'D002'
WHERE nombre = 'Sara';
~~~

### LIMIT

Para modificar un número especifico de columnaso filas podemos usar `LIMIT`  

- En este caso solo va a afectar a los 2 primeros registros que aparezcan tras ordenarlos por fecha.  

~~~sql
UPDATE empleado
SET salario = salario * 1.10
WHERE cod_dpto = 'D003' AND salario < 2000
ORDER BY fecha_nac ASC
LIMIT 2;
~~~

## DELETE

Para eliminar registros usamos el `DELETE FROM` y el `WHERE` para las condiciones  

~~~sql
DELETE FROM empleado
WHERE dni IN ('11111111A','22222222B','33333333C');

DELETE FROM empleado
WHERE dni = '98030259J';
~~~
