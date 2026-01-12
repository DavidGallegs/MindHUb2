# SUBCONSULTAS

Se ejecuta antes que la consulta  

~~~sql
-- Primero selecciona los salarios mayor a la media
SELECT nombre, salario
FROM empleados
WHERE salario > (
    SELECT AVG(salario)
    FROM empleados
);

~~~

Hay 2 grupos:

~~~sql
-- Monoregistro
-- Devuelve un valor, un solo empleado
SELECT nombre, salario
FROM empleados
WHERE salario = (
    SELECT MAX(salario)
    FROM empleados
);


-- Multiregistro
-- Devuelve empleados que pertenecen a departamentos en Madrid.
SELECT nombre
FROM empleados
WHERE departamento_id IN (
    SELECT departamento_id
    FROM departamentos
    WHERE ubicacion = 'Madrid'
);

-- > ANY: salario mayor que al menos un salario del departamento 10.
-- > ALL: salario mayor que todos los salarios del departamento 10.
SELECT nombre, salario
FROM empleados
WHERE salario > ANY (
    SELECT salario
    FROM empleados
    WHERE departamento_id = 10
);

~~~

Luego las subconsultas en `FROM`

~~~sql
-- La subconsulta actúa como una tabla temporal para agrupar y calcular.
SELECT dep_id, AVG(salario)
FROM (
    SELECT departamento_id AS dep_id, salario
    FROM empleados
)
GROUP BY dep_id;s

~~~

Y por último aquellas que usan el operador `EXIST`
No devuelven datos, solo comprueban que exista.

~~~sql

-- Devuelve empleados que lideran al menos un proyecto.
-- La subconsulta puede poner cualquier cosa (SELECT 1 es común).
-- Muy útil para consultas condicionales con relaciones.

SELECT nombre
FROM empleados e
WHERE EXISTS (
    SELECT 1
    FROM proyectos p
    WHERE p.lider_id = e.empleado_id
);

~~~
