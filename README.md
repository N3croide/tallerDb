# CONSULTAS 



**Consultas sobre una tabla**

1. Lista el primer apellido de todos los empleados.

   ```mysql
   select apellido1 from empleado;
   ```

   ```html
   +-----------+
   | apellido1 |
   +-----------+
   | Rivero    |
   | Salas     |
   | Rubio     |
   | Su�rez    |
   | Loyola    |
   | Santana   |
   | Ruiz      |
   | Ruiz      |
   | G�mez     |
   | Flores    |
   | Herrera   |
   | Salas     |
   | S�ez      |
   +-----------+
   ```

2. Lista el primer apellido de los empleados eliminando los apellidos que estén
  repetidos.

  ```mysql
  select distinct apellido1 from empleado;
  ```

  ```html
  +-----------+
  | apellido1 |
  +-----------+
  | Rivero    |
  | Salas     |
  | Rubio     |
  | Su�rez    |
  | Loyola    |
  | Santana   |
  | Ruiz      |
  | G�mez     |
  | Flores    |
  | Herrera   |
  | S�ez      |
  +-----------+
  11 rows in set (0,00 sec)
  ```

3. Lista todas las columnas de la tabla empleado.

   ```mysql
   select codigo,nit,nombre,apellido1,apellido2,codigo_depto from empleado;
   ```

   ```
   +--------+-----------+--------------+-----------+-----------+--------------+
   | codigo | nit       | nombre       | apellido1 | apellido2 | codigo_depto |
   +--------+-----------+--------------+-----------+-----------+--------------+
   |      1 | 32481596F | Aar�n        | Rivero    | G�mez     |            1 |
   |      2 | Y5575632D | Adela        | Salas     | D�az      |            2 |
   |      3 | R6970642B | Adolfo       | Rubio     | Flores    |            3 |
   |      4 | 77705545E | Adri�n       | Su�rez    | NULL      |            4 |
   |      5 | 17087203C | Marcos       | Loyola    | M�ndez    |            5 |
   |      6 | 38382980M | Mar�a        | Santana   | Moreno    |            1 |
   |      7 | 80576669X | Pilar        | Ruiz      | NULL      |            2 |
   |      8 | 71651431Z | Pepe         | Ruiz      | Santana   |            3 |
   |      9 | 56399183D | Juan         | G�mez     | L�pez     |            2 |
   |     10 | 46384486H | Diego        | Flores    | Salas     |            5 |
   |     11 | 67389283A | Marta        | Herrera   | Gil       |            1 |
   |     12 | 41234836R | Irene        | Salas     | Flores    |         NULL |
   |     13 | 82635162B | Juan Antonio | S�ez      | Guerrero  |         NULL |
   +--------+-----------+--------------+-----------+-----------+--------------+
   13 rows in set (0,00 sec)
   ```

4. Lista el nombre y los apellidos de todos los empleados.

   ```mysql
   select nombre, apellido1, apellido2 from empleado;
   ```

   ```
   +--------------+-----------+-----------+
   | nombre       | apellido1 | apellido2 |
   +--------------+-----------+-----------+
   | Aar�n        | Rivero    | G�mez     |
   | Adela        | Salas     | D�az      |
   | Adolfo       | Rubio     | Flores    |
   | Adri�n       | Su�rez    | NULL      |
   | Marcos       | Loyola    | M�ndez    |
   | Mar�a        | Santana   | Moreno    |
   | Pilar        | Ruiz      | NULL      |
   | Pepe         | Ruiz      | Santana   |
   | Juan         | G�mez     | L�pez     |
   | Diego        | Flores    | Salas     |
   | Marta        | Herrera   | Gil       |
   | Irene        | Salas     | Flores    |
   | Juan Antonio | S�ez      | Guerrero  |
   +--------------+-----------+-----------+
   13 rows in set (0,00 sec)
   ```

5. Lista el identificador de los departamentos de los empleados que aparecen
  en la tabla empleado.

  ```mysql
  select codigo from departamento where codigo in (select codigo_depto from empleado);
  ```

  ```
  +--------+
  | codigo |
  +--------+
  |      1 |
  |      2 |
  |      3 |
  |      4 |
  |      5 |
  +--------+
  5 rows in set (0,00 sec)
  ```

6. Lista el identificador de los departamentos de los empleados que aparecen
  en la tabla empleado, eliminando los identificadores que aparecen repetidos.

  ```mysql
  select codigo from departamento where codigo in (select codigo_depto from empleado);
  ```

  ```
  +--------------+
  | codigo_depto |
  +--------------+
  |         NULL |
  |            1 |
  |            2 |
  |            3 |
  |            4 |
  |            5 |
  +--------------+
  6 rows in set (0,00 sec)
  ```

7. Lista el nombre y apellidos de los empleados en una única columna.

   ```mysql
   select concat(nombre,' ',concat(apellido1,' ',ifnull(apellido2,''))) as nombreCompleto from empleado;
   ```

   ```
   +-----------------------------+
   | nombreCompleto              |
   +-----------------------------+
   | Aar�n Rivero G�mez          |
   | Adela Salas D�az            |
   | Adolfo Rubio Flores         |
   | Adri�n Su�rez               |
   | Marcos Loyola M�ndez        |
   | Mar�a Santana Moreno        |
   | Pilar Ruiz                  |
   | Pepe Ruiz Santana           |
   | Juan G�mez L�pez            |
   | Diego Flores Salas          |
   | Marta Herrera Gil           |
   | Irene Salas Flores          |
   | Juan Antonio S�ez Guerrero  |
   +-----------------------------+
   13 rows in set (0,00 sec)
   ```

8. Lista el nombre y apellidos de los empleados en una única columna,
  convirtiendo todos los caracteres en mayúscula.

  ```mysql
  select upper(concat(nombre,' ',concat(apellido1,' ',ifnull(apellido2,'')))) as nombreCompleto from empleado;
  ```

  ```
  +-----------------------------+
  | nombreCompleto              |
  +-----------------------------+
  | AAR�N RIVERO G�MEZ          |
  | ADELA SALAS D�AZ            |
  | ADOLFO RUBIO FLORES         |
  | ADRI�N SU�REZ               |
  | MARCOS LOYOLA M�NDEZ        |
  | MAR�A SANTANA MORENO        |
  | PILAR RUIZ                  |
  | PEPE RUIZ SANTANA           |
  | JUAN G�MEZ L�PEZ            |
  | DIEGO FLORES SALAS          |
  | MARTA HERRERA GIL           |
  | IRENE SALAS FLORES          |
  | JUAN ANTONIO S�EZ GUERRERO  |
  +-----------------------------+
  13 rows in set (0,00 sec)
  ```

9. Lista el nombre y apellidos de los empleados en una única columna,
  convirtiendo todos los caracteres en minúscula.

  ```mysql
  select lower(concat(nombre,' ',concat(apellido1,' ',ifnull(apellido2,'')))) as nombreCompleto from empleado;
  ```

  ```
  +-----------------------------+
  | nombreCompleto              |
  +-----------------------------+
  | aar�n rivero g�mez          |
  | adela salas d�az            |
  | adolfo rubio flores         |
  | adri�n su�rez               |
  | marcos loyola m�ndez        |
  | mar�a santana moreno        |
  | pilar ruiz                  |
  | pepe ruiz santana           |
  | juan g�mez l�pez            |
  | diego flores salas          |
  | marta herrera gil           |
  | irene salas flores          |
  | juan antonio s�ez guerrero  |
  +-----------------------------+
  13 rows in set (0,00 sec)
  ```

10. Lista el identificador de los empleados junto al nif, pero el nif deberá
    aparecer en dos columnas, una mostrará únicamente los dígitos del nif y la
    otra la letra.

    ```mysql
    select substring(nif,1,8) as digitos, substring(nif,9,9) as letra from empleado;
    ```

    ```
    +----------+-------+
    | digitos  | letra |
    +----------+-------+
    | 32481596 | F     |
    | Y5575632 | D     |
    | R6970642 | B     |
    | 77705545 | E     |
    | 17087203 | C     |
    | 38382980 | M     |
    | 80576669 | X     |
    | 71651431 | Z     |
    | 56399183 | D     |
    | 46384486 | H     |
    | 67389283 | A     |
    | 41234836 | R     |
    | 82635162 | B     |
    +----------+-------+
    
    ```

11. Lista el nombre de cada departamento y el valor del presupuesto actual del
    que dispone. Para calcular este dato tendrá que restar al valor del
    presupuesto inicial (columna presupuesto) los gastos que se han generado
    (columna gastos). Tenga en cuenta que en algunos casos pueden existir
    valores negativos. Utilice un alias apropiado para la nueva columna columna
    que está calculando.

    ```mysql
    select (presupuesto - gastos) as ComparaciónPresupuestaria from departamento;
    ```

    ```
    +----------------------------+
    | Comparaci�nPresupuestaria  |
    +----------------------------+
    |                     114000 |
    |                     129000 |
    |                     255000 |
    |                     107000 |
    |                      -5000 |
    |                          0 |
    |                      -1000 |
    +----------------------------+
    7 rows in set (0,00 sec)
    ```

12. Lista el nombre de los departamentos y el valor del presupuesto actual
    ordenado de forma ascendente.

    ```mysql
    select nombre, presupuesto from departamento order by presupuesto asc
    ```

    ```
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | Proyectos        |           0 |
    | Publicidad       |           0 |
    | Contabilidad     |      110000 |
    | Desarrollo       |      120000 |
    | Sistemas         |      150000 |
    | Recursos Humanos |      280000 |
    | I+D              |      375000 |
    +------------------+-------------+
    7 rows in set (0,00 sec)
    ```

13. Lista el nombre de todos los departamentos ordenados de forma
    ascendente.

    ```mysql
    select nombre from departamento order by nombre asc
    ```

    

14. Lista el nombre de todos los departamentos ordenados de forma
    descendente.

15. Lista los apellidos y el nombre de todos los empleados, ordenados de forma
    alfabética tendiendo en cuenta en primer lugar sus apellidos y luego su
    nombre.

16. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
    que tienen mayor presupuesto.

17. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
    que tienen menor presupuesto.

18. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
    tienen mayor gasto.

19. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
    tienen menor gasto.

20. Devuelve una lista con 5 filas a partir de la tercera fila de la tabla empleado. La
    tercera fila se debe incluir en la respuesta. La respuesta debe incluir todas las
    columnas de la tabla empleado.

21. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
    aquellos que tienen un presupuesto mayor o igual a 150000 euros.

22. Devuelve una lista con el nombre de los departamentos y el gasto, de
    aquellos que tienen menos de 5000 euros de gastos.

23. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
    aquellos que tienen un presupuesto entre 100000 y 200000 euros. Sin
    utilizar el operador BETWEEN.

24. Devuelve una lista con el nombre de los departamentos que no tienen un
    presupuesto entre 100000 y 200000 euros. Sin utilizar el operador BETWEEN.

25. Devuelve una lista con el nombre de los departamentos que tienen un
    presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

26. Devuelve una lista con el nombre de los departamentos que no tienen un
    presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

27. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean mayores
    que el presupuesto del que disponen.

28. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean menores
    que el presupuesto del que disponen.

29. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean iguales al
    presupuesto del que disponen.

30. Lista todos los datos de los empleados cuyo segundo apellido sea NULL.

31. Lista todos los datos de los empleados cuyo segundo apellido no sea NULL.

32. Lista todos los datos de los empleados cuyo segundo apellido sea López.

33. Lista todos los datos de los empleados cuyo segundo apellido
    sea Díaz o Moreno. Sin utilizar el operador IN.

34. Lista todos los datos de los empleados cuyo segundo apellido
    sea Díaz o Moreno. Utilizando el operador IN.

35. Lista los nombres, apellidos y nif de los empleados que trabajan en el
    departamento 3.

36. Lista los nombres, apellidos y nif de los empleados que trabajan en los
    departamentos 2, 4 o 5.

**Consultas multitabla (Composición interna)**
**Resuelva todas las consultas utilizando la sintaxis de SQL1 y SQL2.**

1. Devuelve un listado con los empleados y los datos de los departamentos
donde trabaja cada uno.
2. Devuelve un listado con los empleados y los datos de los departamentos
donde trabaja cada uno. Ordena el resultado, en primer lugar por el nombre
del departamento (en orden alfabético) y en segundo lugar por los apellidos
y el nombre de los empleados.
3. Devuelve un listado con el identificador y el nombre del departamento,
solamente de aquellos departamentos que tienen empleados.
4. Devuelve un listado con el identificador, el nombre del departamento y el
valor del presupuesto actual del que dispone, solamente de aquellos
departamentos que tienen empleados. El valor del presupuesto actual lo
puede calcular restando al valor del presupuesto inicial
(columna presupuesto) el valor de los gastos que ha generado
(columna gastos).
5. Devuelve el nombre del departamento donde trabaja el empleado que tiene
el nif 38382980M.

6. Devuelve el nombre del departamento donde trabaja el empleado Pepe Ruiz
Santana.
7. Devuelve un listado con los datos de los empleados que trabajan en el
departamento de I+D. Ordena el resultado alfabéticamente.
8. Devuelve un listado con los datos de los empleados que trabajan en el
departamento de Sistemas, Contabilidad o I+D. Ordena el resultado
alfabéticamente.
9. Devuelve una lista con el nombre de los empleados que tienen los
departamentos que no tienen un presupuesto entre 100000 y 200000 euros.
10. Devuelve un listado con el nombre de los departamentos donde existe
algún empleado cuyo segundo apellido sea NULL. Tenga en cuenta que no
debe mostrar nombres de departamentos que estén repetidos.

**Consultas multitabla (Composición externa)**
**Resuelva todas las consultas utilizando las cláusulas LEFT JOIN y RIGHT JOIN.**

1. Devuelve un listado con todos los empleados junto con los datos de los
departamentos donde trabajan. Este listado también debe incluir los
empleados que no tienen ningún departamento asociado.
2. Devuelve un listado donde sólo aparezcan aquellos empleados que no
tienen ningún departamento asociado.
3. Devuelve un listado donde sólo aparezcan aquellos departamentos que no
tienen ningún empleado asociado.
4. Devuelve un listado con todos los empleados junto con los datos de los
departamentos donde trabajan. El listado debe incluir los empleados que no
tienen ningún departamento asociado y los departamentos que no tienen
ningún empleado asociado. Ordene el listado alfabéticamente por el
nombre del departamento.
5. Devuelve un listado con los empleados que no tienen ningún departamento
asociado y los departamentos que no tienen ningún empleado asociado.
Ordene el listado alfabéticamente por el nombre del departamento.

**Consultas resumen**

1. Calcula la suma del presupuesto de todos los departamentos.
2. Calcula la media del presupuesto de todos los departamentos.
3. Calcula el valor mínimo del presupuesto de todos los departamentos.
4. Calcula el nombre del departamento y el presupuesto que tiene asignado,
del departamento con menor presupuesto.
5. Calcula el valor máximo del presupuesto de todos los departamentos.
6. Calcula el nombre del departamento y el presupuesto que tiene asignado,
del departamento con mayor presupuesto.
7. Calcula el número total de empleados que hay en la tabla empleado.
8. Calcula el número de empleados que no tienen NULL en su segundo
apellido.
9. Calcula el número de empleados que hay en cada departamento. Tienes que
devolver dos columnas, una con el nombre del departamento y otra con el
número de empleados que tiene asignados.
10. Calcula el nombre de los departamentos que tienen más de 2 empleados. El
resultado debe tener dos columnas, una con el nombre del departamento y
otra con el número de empleados que tiene asignados.
11. Calcula el número de empleados que trabajan en cada uno de los
departamentos. El resultado de esta consulta también tiene que incluir
aquellos departamentos que no tienen ningún empleado asociado.
12. Calcula el número de empleados que trabajan en cada unos de los
departamentos que tienen un presupuesto mayor a 200000 euros.

**Subconsultas con operadores básicos de comparación**

1. Devuelve un listado con todos los empleados que tiene el departamento
de Sistemas. (Sin utilizar INNER JOIN).
2. Devuelve el nombre del departamento con mayor presupuesto y la cantidad
que tiene asignada.
3. Devuelve el nombre del departamento con menor presupuesto y la cantidad
que tiene asignada.
Subconsultas con ALL y ANY
4. Devuelve el nombre del departamento con mayor presupuesto y la cantidad
que tiene asignada. Sin hacer uso de MAX, ORDER BY ni LIMIT.
5. Devuelve el nombre del departamento con menor presupuesto y la cantidad
que tiene asignada. Sin hacer uso de MIN, ORDER BY ni LIMIT.
6. Devuelve los nombres de los departamentos que tienen empleados
asociados. (Utilizando ALL o ANY).
7. Devuelve los nombres de los departamentos que no tienen empleados
asociados. (Utilizando ALL o ANY).
Subconsultas con IN y NOT IN
8. Devuelve los nombres de los departamentos que tienen empleados
asociados. (Utilizando IN o NOT IN).
9. Devuelve los nombres de los departamentos que no tienen empleados
asociados. (Utilizando IN o NOT IN).
Subconsultas con EXISTS y NOT EXISTS
10. Devuelve los nombres de los departamentos que tienen empleados
asociados. (Utilizando EXISTS o NOT EXISTS).
11. Devuelve los nombres de los departamentos que tienen empleados
asociados. (Utilizando EXISTS o NOT EXISTS).