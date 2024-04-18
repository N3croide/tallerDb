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
   select codigo,nif,nombre,apellido1,apellido2,codigo_depto from empleado;
   ```

   ```
   +--------+-----------+--------------+-----------+-----------+--------------+
   | codigo | nif       | nombre       | apellido1 | apellido2 | codigo_depto |
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
5 rows in set (0.00 sec)
  ```

6. Lista el identificador de los departamentos de los empleados que aparecen
   en la tabla empleado, eliminando los identificadores que aparecen repetidos.

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
5 rows in set (0.00 sec)
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
    select codigo, REGEXP_REPLACE(nif, '[^0-9]+', '') as numeros, REGEXP_REPLACE(nif, '[^A-Za-z]+', '') as letras from empleado;
    ```

    ```
    +--------+----------+--------+
    | codigo | numeros  | letras |
    +--------+----------+--------+
    |      1 | 32481596 | F      |
    |      2 | 5575632  | YD     |
    |      3 | 6970642  | RB     |
    |      4 | 77705545 | E      |
    |      5 | 17087203 | C      |
    |      6 | 38382980 | M      |
    |      7 | 80576669 | X      |
    |      8 | 71651431 | Z      |
    |      9 | 56399183 | D      |
    |     10 | 46384486 | H      |
    |     11 | 67389283 | A      |
    |     12 | 41234836 | R      |
    |     13 | 82635162 | B      |
    +--------+----------+--------+
    ```

11. Lista el nombre de cada departamento y el valor del presupuesto actual del
    que dispone. Para calcular este dato tendrá que restar al valor del
    presupuesto inicial (columna presupuesto) los gastos que se han generado
    (columna gastos). Tenga en cuenta que en algunos casos pueden existir
    valores negativos. Utilice un alias apropiado para la nueva columna columna
    que está calculando.

    ```mysql
    select (presupuesto - gastos) as presupuestoActual from departamento;
    ```

    ```
    +----------------------------+
    | presupuestoActual          |
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
    select nombre,(presupuesto-gastos) presupuestoActual from departamento or
    der by presupuesto asc;
    ```

    ```
    +------------------+-------------------+
    | nombre           | presupuestoActual |
    +------------------+-------------------+
    | Proyectos        |                 0 |
    | Publicidad       |             -1000 |
    | Contabilidad     |            107000 |
    | Desarrollo       |            114000 |
    | Sistemas         |            129000 |
    | Recursos Humanos |            255000 |
    | I+D              |             -5000 |
    +------------------+-------------------+
    7 rows in set (0,00 sec)
    ```

13. Lista el nombre de todos los departamentos ordenados de forma
    ascendente.

    ```mysql
    select nombre from departamento order by nombre asc;
    ```

    ```
    +------------------+
    | nombre           |
    +------------------+
    | Contabilidad     |
    | Desarrollo       |
    | I+D              |
    | Proyectos        |
    | Publicidad       |
    | Recursos Humanos |
    | Sistemas         |
    +------------------+
    7 rows in set (0,00 sec)
    ```

14. Lista el nombre de todos los departamentos ordenados de forma
    descendente.

    ```mysql
    select nombre from departamento order by nombre desc;
    ```

    ```
    +------------------+
    | nombre           |
    +------------------+
    | Sistemas         |
    | Recursos Humanos |
    | Publicidad       |
    | Proyectos        |
    | I+D              |
    | Desarrollo       |
    | Contabilidad     |
    +------------------+
    7 rows in set (0,00 sec)
    ```

15. Lista los apellidos y el nombre de todos los empleados, ordenados de forma
    alfabética tendiendo en cuenta en primer lugar sus apellidos y luego su
    nombre.

    ```mysql
    select concat(apellido1,' ',ifnull(apellido2,'')) as apellidos, nombre from empleado order by apellidos, nombre;
    ```

    ```
    +----------------+--------------+
    | apellidos      | nombre       |
    +----------------+--------------+
    | Flores Salas   | Diego        |
    | G�mez L�pez    | Juan         |
    | Herrera Gil    | Marta        |
    | Loyola M�ndez  | Marcos       |
    | Rivero G�mez   | Aar�n        |
    | Rubio Flores   | Adolfo       |
    | Ruiz           | Pilar        |
    | Ruiz Santana   | Pepe         |
    | S�ez Guerrero  | Juan Antonio |
    | Salas D�az     | Adela        |
    | Salas Flores   | Irene        |
    | Santana Moreno | Mar�a        |
    | Su�rez         | Adri�n       |
    +----------------+--------------+
    13 rows in set (0,00 sec)
    ```

16. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
    que tienen mayor presupuesto.

    ```mysql
    select nombre, presupuesto from departamento order by presupuesto desc limit 3;
    ```

    ```
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | I+D              |      375000 |
    | Recursos Humanos |      280000 |
    | Sistemas         |      150000 |
    +------------------+-------------+
    3 rows in set (0,00 sec)
    ```

17. Devuelve una lista con el nombre y el presupuesto, de los 3 departamentos
    que tienen menor presupuesto.

    ```mysql
    select nombre, presupuesto from departamento order by presupuesto asc limit 3;
    ```

    ```
    +--------------+-------------+
    | nombre       | presupuesto |
    +--------------+-------------+
    | Proyectos    |           0 |
    | Publicidad   |           0 |
    | Contabilidad |      110000 |
    +--------------+-------------+
    3 rows in set (0,00 sec)
    ```

18. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
    tienen mayor gasto.

    ```mysql
    select nombre, gastos from departamento order by gastos desc limit 2;
    ```

    ```
    +------------------+--------+
    | nombre           | gastos |
    +------------------+--------+
    | I+D              | 380000 |
    | Recursos Humanos |  25000 |
    +------------------+--------+
    2 rows in set (0,00 sec)
    ```

19. Devuelve una lista con el nombre y el gasto, de los 2 departamentos que
    tienen menor gasto.

    ```mysql
    select nombre, gastos from departamento order by gastos asc limit 2;
    ```

    ```
    +------------+--------+
    | nombre     | gastos |
    +------------+--------+
    | Proyectos  |      0 |
    | Publicidad |   1000 |
    +------------+--------+
    2 rows in set (0,00 sec)
    ```

20. Devuelve una lista con 5 filas a partir de la tercera fila de la tabla empleado. La
    tercera fila se debe incluir en la respuesta. La respuesta debe incluir todas las
    columnas de la tabla empleado.

    ```mysql
    select codigo,nit,nombre,apellido1,apellido2,codigo_depto from empleado limit 5 offset 2;
    ```

    ```
    +--------+-----------+---------+-----------+-----------+--------------+
    | codigo | nif       | nombre  | apellido1 | apellido2 | codigo_depto |
    +--------+-----------+---------+-----------+-----------+--------------+
    |      3 | R6970642B | Adolfo  | Rubio     | Flores    |            3 |
    |      4 | 77705545E | Adri�n  | Su�rez    | NULL      |            4 |
    |      5 | 17087203C | Marcos  | Loyola    | M�ndez    |            5 |
    |      6 | 38382980M | Mar�a   | Santana   | Moreno    |            1 |
    |      7 | 80576669X | Pilar   | Ruiz      | NULL      |            2 |
    +--------+-----------+---------+-----------+-----------+--------------+
    5 rows in set (0,00 sec)
    ```

21. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
    aquellos que tienen un presupuesto mayor o igual a 150000 euros.

    ```mysql
    select nombre, presupuesto from departamento where presupuesto >= 150000; 
    ```

    ```
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | Sistemas         |      150000 |
    | Recursos Humanos |      280000 |
    | I+D              |      375000 |
    +------------------+-------------+
    3 rows in set (0,00 sec)
    ```

22. Devuelve una lista con el nombre de los departamentos y el gasto, de
    aquellos que tienen menos de 5000 euros de gastos.

    ```mysql
    select nombre, gastos from departamento where gastos < 5000;
    ```

    ```
    +--------------+--------+
    | nombre       | gastos |
    +--------------+--------+
    | Contabilidad |   3000 |
    | Proyectos    |      0 |
    | Publicidad   |   1000 |
    +--------------+--------+
    3 rows in set (0,00 sec)
    ```

23. Devuelve una lista con el nombre de los departamentos y el presupuesto, de
    aquellos que tienen un presupuesto entre 100000 y 200000 euros. Sin
    utilizar el operador BETWEEN.

    ```mysql
    select nombre, presupuesto from departamento where presupuesto <200000 and presupuesto >100000;
    ```

    ```
    +--------------+-------------+
    | nombre       | presupuesto |
    +--------------+-------------+
    | Desarrollo   |      120000 |
    | Sistemas     |      150000 |
    | Contabilidad |      110000 |
    +--------------+-------------+
    3 rows in set (0,00 sec)
    ```

24. Devuelve una lista con el nombre de los departamentos que no tienen un
    presupuesto entre 100000 y 200000 euros. Sin utilizar el operador BETWEEN.

    ```mysql
    select nombre, presupuesto from departamento where presupuesto >200000 or presupuesto <100000;
    ```

    ```
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | Recursos Humanos |      280000 |
    | I+D              |      375000 |
    | Proyectos        |           0 |
    | Publicidad       |           0 |
    +------------------+-------------+
    4 rows in set (0,00 sec)
    
    ```

    

25. Devuelve una lista con el nombre de los departamentos que tienen un
    presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

    ```mysql
    select nombre, presupuesto from departamento where presupuesto between 100000 and 200000;
    ```

    ```
    +--------------+-------------+
    | nombre       | presupuesto |
    +--------------+-------------+
    | Desarrollo   |      120000 |
    | Sistemas     |      150000 |
    | Contabilidad |      110000 |
    +--------------+-------------+
    3 rows in set (0,00 sec)
    ```

26. Devuelve una lista con el nombre de los departamentos que no tienen un
    presupuesto entre 100000 y 200000 euros. Utilizando el operador BETWEEN.

    ```mysql
    select nombre, presupuesto from departamento where presupuesto not betwee
    n 100000 and 200000;
    ```

    ```
    +------------------+-------------+
    | nombre           | presupuesto |
    +------------------+-------------+
    | Recursos Humanos |      280000 |
    | I+D              |      375000 |
    | Proyectos        |           0 |
    | Publicidad       |           0 |
    +------------------+-------------+
    4 rows in set (0,00 sec)
    ```

27. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean mayores
    que el presupuesto del que disponen.

    ```mysql
    select nombre, presupuesto, gastos from departamento where gastos > presu
    puesto;
    ```

    ```
    +------------+-------------+--------+
    | nombre     | presupuesto | gastos |
    +------------+-------------+--------+
    | I+D        |      375000 | 380000 |
    | Publicidad |           0 |   1000 |
    +------------+-------------+--------+
    2 rows in set (0,00 sec)
    ```

28. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean menores
    que el presupuesto del que disponen.

    ```mysql
    select nombre, presupuesto, gastos from departamento where gastos < presupuesto;
    ```

    ```
    +------------------+-------------+--------+
    | nombre           | presupuesto | gastos |
    +------------------+-------------+--------+
    | Desarrollo       |      120000 |   6000 |
    | Sistemas         |      150000 |  21000 |
    | Recursos Humanos |      280000 |  25000 |
    | Contabilidad     |      110000 |   3000 |
    +------------------+-------------+--------+
    4 rows in set (0,00 sec)
    ```

29. Devuelve una lista con el nombre de los departamentos, gastos y
    presupuesto, de aquellos departamentos donde los gastos sean iguales al
    presupuesto del que disponen.

    ```mysql
    select nombre, presupuesto, gastos from departamento where gastos = presupuesto;
    ```

    ```
    +-----------+-------------+--------+
    | nombre    | presupuesto | gastos |
    +-----------+-------------+--------+
    | Proyectos |           0 |      0 |
    +-----------+-------------+--------+
    1 row in set (0,00 sec)
    ```

30. Lista todos los datos de los empleados cuyo segundo apellido sea NULL.

    ```mysql
    select codigo,nif,nombre,apellido1,apellido2,codigo_depto from empleado where isnull(apellido2);
    ```

    ```
    +--------+-----------+---------+-----------+-----------+--------------+
    | codigo | nif       | nombre  | apellido1 | apellido2 | codigo_depto |
    +--------+-----------+---------+-----------+-----------+--------------+
    |      4 | 77705545E | Adrián  | Suárez    | NULL      |            4 |
    |      7 | 80576669X | Pilar   | Ruiz      | NULL      |            2 |
    +--------+-----------+---------+-----------+-----------+--------------+
    2 rows in set (0,00 sec)
    ```

31. Lista todos los datos de los empleados cuyo segundo apellido no sea NULL.

    ```mysql
    select codigo,nif,nombre,apellido1,apellido2,codigo_depto from empleado where apellido2 is not null;
    ```

    ```
    +--------+-----------+--------------+-----------+-----------+--------------+
    | codigo | nif       | nombre       | apellido1 | apellido2 | codigo_depto |
    +--------+-----------+--------------+-----------+-----------+--------------+
    |      1 | 32481596F | Aarón        | Rivero    | Gómez     |            1 |
    |      2 | Y5575632D | Adela        | Salas     | Díaz      |            2 |
    |      3 | R6970642B | Adolfo       | Rubio     | Flores    |            3 |
    |      5 | 17087203C | Marcos       | Loyola    | Méndez    |            5 |
    |      6 | 38382980M | María        | Santana   | Moreno    |            1 |
    |      8 | 71651431Z | Pepe         | Ruiz      | Santana   |            3 |
    |      9 | 56399183D | Juan         | Gómez     | López     |            2 |
    |     10 | 46384486H | Diego        | Flores    | Salas     |            5 |
    |     11 | 67389283A | Marta        | Herrera   | Gil       |            1 |
    |     12 | 41234836R | Irene        | Salas     | Flores    |         NULL |
    |     13 | 82635162B | Juan Antonio | Sáez      | Guerrero  |         NULL |
    +--------+-----------+--------------+-----------+-----------+--------------+
    11 rows in set (0,00 sec)
    ```

    

32. Lista todos los datos de los empleados cuyo segundo apellido sea López.

    ```mysql
    select codigo,nif,nombre,apellido1,apellido2,codigo_depto from empleado where apellido2 = 'López';
    ```

    ```
    +--------+-----------+--------+-----------+-----------+--------------+
    | codigo | nif       | nombre | apellido1 | apellido2 | codigo_depto |
    +--------+-----------+--------+-----------+-----------+--------------+
    |      9 | 56399183D | Juan   | Gómez     | López     |            2 |
    +--------+-----------+--------+-----------+-----------+--------------+
    1 row in set (0,00 sec)
    ```

33. Lista todos los datos de los empleados cuyo segundo apellido
    sea Díaz o Moreno. Sin utilizar el operador IN.

    ```mysql
    select codigo,nif,nombre,apellido1,apellido2,codigo_depto from empleado where apellido2 = 'Díaz' or apellido2 = 'Moreno';
    ```

    ```
    +--------+-----------+--------+-----------+-----------+--------------+
    | codigo | nif       | nombre | apellido1 | apellido2 | codigo_depto |
    +--------+-----------+--------+-----------+-----------+--------------+
    |      2 | Y5575632D | Adela  | Salas     | Díaz      |            2 |
    |      6 | 38382980M | María  | Santana   | Moreno    |            1 |
    +--------+-----------+--------+-----------+-----------+--------------+
    2 rows in set (0,00 sec)
    ```

    

34. Lista todos los datos de los empleados cuyo segundo apellido
    sea Díaz o Moreno. Utilizando el operador IN.

    ```mysql
    select codigo,nif,nombre,apellido1,apellido2,codigo_depto from empleado where apellido2 in ('Díaz','Moreno');
    ```

    ```
    +--------+-----------+--------+-----------+-----------+--------------+
    | codigo | nif       | nombre | apellido1 | apellido2 | codigo_depto |
    +--------+-----------+--------+-----------+-----------+--------------+
    |      2 | Y5575632D | Adela  | Salas     | Díaz      |            2 |
    |      6 | 38382980M | María  | Santana   | Moreno    |            1 |
    +--------+-----------+--------+-----------+-----------+--------------+
    2 rows in set (0,01 sec)
    ```

    

35. Lista los nombres, apellidos y nif de los empleados que trabajan en el
    departamento 3.

    ```mysql
    select codigo,nif,nombre,apellido1,apellido2,codigo_depto from empleado where codigo_depto = 3;
    ```

    ```
    +--------+-----------+--------+-----------+-----------+--------------+
    | codigo | nif       | nombre | apellido1 | apellido2 | codigo_depto |
    +--------+-----------+--------+-----------+-----------+--------------+
    |      3 | R6970642B | Adolfo | Rubio     | Flores    |            3 |
    |      8 | 71651431Z | Pepe   | Ruiz      | Santana   |            3 |
    +--------+-----------+--------+-----------+-----------+--------------+
    2 rows in set (0,00 sec)
    ```

36. Lista los nombres, apellidos y nif de los empleados que trabajan en los
    departamentos 2, 4 o 5.

    ```mysql
    select codigo,nif,nombre,apellido1,apellido2,codigo_depto from empleado where codigo_depto in (3,4,5);
    ```

    ```
    +--------+-----------+---------+-----------+-----------+--------------+
    | codigo | nif       | nombre  | apellido1 | apellido2 | codigo_depto |
    +--------+-----------+---------+-----------+-----------+--------------+
    |      3 | R6970642B | Adolfo  | Rubio     | Flores    |            3 |
    |      8 | 71651431Z | Pepe    | Ruiz      | Santana   |            3 |
    |      4 | 77705545E | Adrián  | Suárez    | NULL      |            4 |
    |      5 | 17087203C | Marcos  | Loyola    | Méndez    |            5 |
    |     10 | 46384486H | Diego   | Flores    | Salas     |            5 |
    +--------+-----------+---------+-----------+-----------+--------------+
    5 rows in set (0,00 sec)
    ```

    

**Consultas multitabla (Composición interna)**
**Resuelva todas las consultas utilizando la sintaxis de SQL1 y SQL2.**

1. Devuelve un listado con los empleados y los datos de los departamentos
   donde trabaja cada uno.

  ```mysql
select d.codigo, d.nombre, d.presupuesto, d.gastos, e.codigo, e.nif, e.nombre, e.apellido1, e.apellido2, e.codigo_depto from empleado e join departamento d on d.codigo = e.codigo_depto;
  ```

  ```
+--------+------------------+-------------+--------+--------+-----------+---------+-----------+-----------+--------------+
| codigo | nombre           | presupuesto | gastos | codigo | nif       | nombre  | apellido1 | apellido2 | codigo_depto |
+--------+------------------+-------------+--------+--------+-----------+---------+-----------+-----------+--------------+
|      1 | Desarrollo       |      120000 |   6000 |      1 | 32481596F | Aarón   | Rivero    | Gómez     |            1 |
|      1 | Desarrollo       |      120000 |   6000 |      6 | 38382980M | María   | Santana   | Moreno    |            1 |
|      1 | Desarrollo       |      120000 |   6000 |     11 | 67389283A | Marta   | Herrera   | Gil       |            1 |
|      2 | Sistemas         |      150000 |  21000 |      2 | Y5575632D | Adela   | Salas     | Díaz      |            2 |
|      2 | Sistemas         |      150000 |  21000 |      7 | 80576669X | Pilar   | Ruiz      | NULL      |            2 |
|      2 | Sistemas         |      150000 |  21000 |      9 | 56399183D | Juan    | Gómez     | López     |            2 |
|      3 | Recursos Humanos |      280000 |  25000 |      3 | R6970642B | Adolfo  | Rubio     | Flores    |            3 |
|      3 | Recursos Humanos |      280000 |  25000 |      8 | 71651431Z | Pepe    | Ruiz      | Santana   |            3 |
|      4 | Contabilidad     |      110000 |   3000 |      4 | 77705545E | Adrián  | Suárez    | NULL      |            4 |
|      5 | I+D              |      375000 | 380000 |      5 | 17087203C | Marcos  | Loyola    | Méndez    |            5 |
|      5 | I+D              |      375000 | 380000 |     10 | 46384486H | Diego   | Flores    | Salas     |            5 |
+--------+------------------+-------------+--------+--------+-----------+---------+-----------+-----------+--------------+

  ```

2. Devuelve un listado con los empleados y los datos de los departamentos
   donde trabaja cada uno. Ordena el resultado, en primer lugar por el nombre
     del departamento (en orden alfabético) y en segundo lugar por los apellidos
     y el nombre de los empleados.

  ```mysql
select d.codigo, d.nombre, d.presupuesto, d.gastos, e.codigo, e.nif,e.nombre, e.apellido1, e.apellido2, e.codigo_depto from empleado e join departamento d on d.codigo = e.codigo_depto order by d.nombre asc, e.apellido1 asc, e.apellido2 asc,e.nombre asc;
  ```

  ```
+--------+------------------+-------------+--------+--------+-----------+---------+-----------+-----------+--------------+
| codigo | nombre           | presupuesto | gastos | codigo | nif       | nombre  | apellido1 | apellido2 | codigo_depto |
+--------+------------------+-------------+--------+--------+-----------+---------+-----------+-----------+--------------+
|      4 | Contabilidad     |      110000 |   3000 |      4 | 77705545E | Adrián  | Suárez    | NULL      |            4 |
|      1 | Desarrollo       |      120000 |   6000 |     11 | 67389283A | Marta   | Herrera   | Gil       |            1 |
|      1 | Desarrollo       |      120000 |   6000 |      1 | 32481596F | Aarón   | Rivero    | Gómez     |            1 |
|      1 | Desarrollo       |      120000 |   6000 |      6 | 38382980M | María   | Santana   | Moreno    |            1 |
|      5 | I+D              |      375000 | 380000 |     10 | 46384486H | Diego   | Flores    | Salas     |            5 |
|      5 | I+D              |      375000 | 380000 |      5 | 17087203C | Marcos  | Loyola    | Méndez    |            5 |
|      3 | Recursos Humanos |      280000 |  25000 |      3 | R6970642B | Adolfo  | Rubio     | Flores    |            3 |
|      3 | Recursos Humanos |      280000 |  25000 |      8 | 71651431Z | Pepe    | Ruiz      | Santana   |            3 |
|      2 | Sistemas         |      150000 |  21000 |      9 | 56399183D | Juan    | Gómez     | López     |            2 |
|      2 | Sistemas         |      150000 |  21000 |      7 | 80576669X | Pilar   | Ruiz      | NULL      |            2 |
|      2 | Sistemas         |      150000 |  21000 |      2 | Y5575632D | Adela   | Salas     | Díaz      |            2 |
+--------+------------------+-------------+--------+--------+-----------+---------+-----------+-----------+--------------+

  ```

  

3. Devuelve un listado con el identificador y el nombre del departamento,
   solamente de aquellos departamentos que tienen empleados.

  ```mysql
select d.codigo, d.nombre from departamento d where d.codigo in (select e.codigo_depto from empleado e);
  ```

  ```
+--------+------------------+
| codigo | nombre           |
+--------+------------------+
|      1 | Desarrollo       |
|      2 | Sistemas         |
|      3 | Recursos Humanos |
|      4 | Contabilidad     |
|      5 | I+D              |
+--------+------------------+
5 rows in set (0,00 sec)
  ```

4. Devuelve un listado con el identificador, el nombre del departamento y el
   valor del presupuesto actual del que dispone, solamente de aquellos
     departamentos que tienen empleados. El valor del presupuesto actual lo
     puede calcular restando al valor del presupuesto inicial
     (columna presupuesto) el valor de los gastos que ha generado
     (columna gastos).

  ```mysql
select d.codigo, d.nombre, (d.presupuesto - d.gastos) as preupuestoActual from departamento d where d.codigo in (select e.codigo_depto from empleado e);
  ```

  ```
+--------+------------------+------------------+
| codigo | nombre           | preupuestoActual |
+--------+------------------+------------------+
|      1 | Desarrollo       |           114000 |
|      2 | Sistemas         |           129000 |
|      3 | Recursos Humanos |           255000 |
|      4 | Contabilidad     |           107000 |
|      5 | I+D              |            -5000 |
+--------+------------------+------------------+
5 rows in set (0,00 sec)
  ```

5. Devuelve el nombre del departamento donde trabaja el empleado que tiene el nif 38382980M.

  ```MYSQL
select d.nombre from departamento d join empleado e where e.nif = "38382980M" and e.codigo_depto = d.codigo;
  ```

```
+------------+
| nombre     |
+------------+
| Desarrollo |
+------------+
1 row in set (0.00 sec)
```



6. Devuelve el nombre del departamento donde trabaja el empleado Pepe Ruiz Santana.

   ```mysql
   select d.nombre from departamento d where d.codigo = (select e.codigo_depto from empleado e where e.nombre = "Pepe" and e.apellido1 = "Ruiz" and e.apellido2 = "Santana");
   ```

   ```
   +------------------+
   | nombre           |
   +------------------+
   | Recursos Humanos |
   +------------------+
   ```

   

7. Devuelve un listado con los datos de los empleados que trabajan en el departamento de I+D. Ordena el resultado alfabéticamente.

   ```mysql
   select e.codigo as IdEmpleado, e.nif as Nif, e.nombre as Nombre, concat(e.apellido1,' ',ifnull(e.apellido2,''))  as Apellidos, e.codigo_depto from empleado e  join departamento d on d.codigo = e.codigo_depto where d.nombre ='I+D' order by e.nombre asc, Apellidos asc;
   ```

   ```
   +------------+-----------+--------+---------------+--------------+
   | IdEmpleado | Nif       | Nombre | Apellidos     | codigo_depto |
   +------------+-----------+--------+---------------+--------------+
   |         10 | 46384486H | Diego  | Flores Salas  |            5 |
   |          5 | 17087203C | Marcos | Loyola Méndez |            5 |
   +------------+-----------+--------+---------------+--------------+
   2 rows in set (0.01 sec)
   ```

   

8. Devuelve un listado con los datos de los empleados que trabajan en el departamento de Sistemas, Contabilidad o I+D. Ordena el resultado alfabéticamente.

   ```mysql
   select e.codigo as IdEmpleado, e.nif as Nif, e.nombre as Nombre, concat(e.apellido1,' ',ifnull(e.apellido2,''))  as Apellidos, e.codigo_depto from empleado e  join departamento d on d.codigo = e.codigo_depto where d.nombre ='I+D' or d.nombre = "Sistemas" or d.nombre = "Contabilidad" order by e.nombre asc, Apellidos asc;
   ```

   ```
   +------------+-----------+--------+---------------+--------------+
   | IdEmpleado | Nif       | Nombre | Apellidos     | codigo_depto |
   +------------+-----------+--------+---------------+--------------+
   |          2 | Y5575632D | Adela  | Salas Díaz    |            2 |
   |          4 | 77705545E | Adrián | Suárez        |            4 |
   |         10 | 46384486H | Diego  | Flores Salas  |            5 |
   |          9 | 56399183D | Juan   | Gómez López   |            2 |
   |          5 | 17087203C | Marcos | Loyola Méndez |            5 |
   |          7 | 80576669X | Pilar  | Ruiz          |            2 |
   +------------+-----------+--------+---------------+--------------+
   6 rows in set (0.00 sec)
   ```

   

9. Devuelve una lista con el nombre de los empleados que tienen los
   departamentos que no tienen un presupuesto entre 100000 y 200000 euros.

   ```mysql
   select e.nombre, concat(e.apellido1,' ',ifnull(e.apellido2,'')) AS Apellidos from empleado e join departamento d on e.codigo_depto = d.codigo where d.presupuesto between 100000 and 200000;
   ```

   ```
   +--------+----------------+
   | nombre | Apellidos      |
   +--------+----------------+
   | Aarón  | Rivero Gómez   |
   | María  | Santana Moreno |
   | Marta  | Herrera Gil    |
   | Adela  | Salas Díaz     |
   | Pilar  | Ruiz           |
   | Juan   | Gómez López    |
   | Adrián | Suárez         |
   +--------+----------------+
   ```

   

10. Devuelve un listado con el nombre de los departamentos donde existe
    algún empleado cuyo segundo apellido sea NULL. Tenga en cuenta que no
    debe mostrar nombres de departamentos que estén repetidos.

    ```mysql
    select d.nombre from departamento d join empleado e on d.codigo = e.codigo_depto where isnull(e.apellido2);
    ```

    ```
    +--------------+
    | nombre       |
    +--------------+
    | Contabilidad |
    | Sistemas     |
    +--------------+
    2 rows in set (0.01 sec)
    ```

**Consultas multitabla (Composición externa)**
**Resuelva todas las consultas utilizando las cláusulas LEFT JOIN y RIGHT JOIN.**

1. Devuelve un listado con todos los empleados junto con los datos de los
   departamentos donde trabajan. Este listado también debe incluir los
   empleados que no tienen ningún departamento asociado.

   ```mysql
   select e.codigo as ID, e.nombre as Nombre, concat(e.apellido1,' ',ifnull(e.apellido2,'')) AS Apellidos, e.codigo_depto as IdDpto, d.nombre as NombreDepto, d.presupuesto as PresupuestoDpto, d.gastos as GastosDpto
   from empleado e
   left join departamento d on d.codigo = e.codigo_depto;
   ```

   ```
   +----+--------------+----------------+--------+------------------+-----------------+-----------+
   | ID | Nombre       | Apellidos      | IdDpto | NombreDepto      | PresupuestoDpto | GastosDpto|
   +----+--------------+----------------+--------+------------------+-----------------+-----------+
   |  1 | Aarón        | Rivero Gómez   |      1 | Desarrollo       |          120000 |      6000 |
   |  2 | Adela        | Salas Díaz     |      2 | Sistemas         |          150000 |     21000 |
   |  3 | Adolfo       | Rubio Flores   |      3 | Recursos Humanos |          280000 |     25000 |
   |  4 | Adrián       | Suárez         |      4 | Contabilidad     |          110000 |      3000 |
   |  5 | Marcos       | Loyola Méndez  |      5 | I+D              |          375000 |    380000 |
   |  6 | María        | Santana Moreno |      1 | Desarrollo       |          120000 |      6000 |
   |  7 | Pilar        | Ruiz           |      2 | Sistemas         |          150000 |     21000 |
   |  8 | Pepe         | Ruiz Santana   |      3 | Recursos Humanos |          280000 |     25000 |
   |  9 | Juan         | Gómez López    |      2 | Sistemas         |          150000 |     21000 |
   | 10 | Diego        | Flores Salas   |      5 | I+D              |          375000 |    380000 |
   | 11 | Marta        | Herrera Gil    |      1 | Desarrollo       |          120000 |      6000 |
   | 12 | Irene        | Salas Flores   |   NULL | NULL             |            NULL |      NULL |
   | 13 | Juan Antonio | Sáez Guerrero  |   NULL | NULL             |            NULL |      NULL |
   +----+--------------+----------------+--------+------------------+-----------------+-----------+
   13 rows in set (0.00 sec)
   
   ```

   

2. Devuelve un listado donde sólo aparezcan aquellos empleados que no
   tienen ningún departamento asociado.

   ```mysql
   select e.codigo as ID, e.nombre as Nombre, concat(e.apellido1,' ',ifnull(e.apellido2,'')) AS Apellidos
   from empleado e
   left join departamento d on e.codigo_depto = d.codigo
   where e.codigo_depto is null;
   ```

   ```
   +----+--------------+---------------+
   | ID | Nombre       | Apellidos     |
   +----+--------------+---------------+
   | 12 | Irene        | Salas Flores  |
   | 13 | Juan Antonio | Sáez Guerrero |
   +----+--------------+---------------+
   2 rows in set (0.00 sec)
   ```

   

3. Devuelve un listado donde sólo aparezcan aquellos departamentos que no
   tienen ningún empleado asociado.

   ```mysql
   select d.codigo as idDpto, d.nombre as Nombre, d.presupuesto as Presupuesto, d.gastos as Gastos
   from departamento d
   left join empleado e on e.codigo_depto = d.codigo
   where e.codigo_depto is null;
   ```

   ```
   +--------+------------+-------------+--------+
   | idDpto | Nombre     | Presupuesto | Gastos |
   +--------+------------+-------------+--------+
   |      6 | Proyectos  |           0 |      0 |
   |      7 | Publicidad |           0 |   1000 |
   +--------+------------+-------------+--------+
   2 rows in set (0.00 sec)
   ```

   

4. Devuelve un listado con todos los empleados junto con los datos de los
   departamentos donde trabajan. El listado debe incluir los empleados que no
   tienen ningún departamento asociado y los departamentos que no tienen
   ningún empleado asociado. Ordene el listado alfabéticamente por el
   nombre del departamento.

   ```mysql
   select e.codigo as ID, e.nombre as Nombre, concat(e.apellido1,' ',ifnull(e.apellido2,'')) AS Apellidos, e.codigo_depto as IdDpto, d.nombre as NombreDepto, d.presupuesto as PresupuestoDpto, d.gastos as GastosDpto
   from empleado e
   right join
       departamento d on e.codigo_depto = d.codigo
   order by
       d.nombre asc;
   ```

   ```
   +----+--------------+----------------+--------+------------------+-----------------+------------+
   | ID | Nombre       | Apellidos      | IdDpto | NombreDepto      | PresupuestoDpto | GastosDpto |
   +----+--------------+----------------+--------+------------------+-----------------+------------+
   | 12 | Irene        | Salas Flores   |   NULL | NULL             |            NULL |       NULL |
   | 13 | Juan Antonio | Sáez Guerrero  |   NULL | NULL             |            NULL |       NULL |
   |  4 | Adrián       | Suárez         |      4 | Contabilidad     |          110000 |       3000 |
   |  1 | Aarón        | Rivero Gómez   |      1 | Desarrollo       |          120000 |       6000 |
   |  6 | María        | Santana Moreno |      1 | Desarrollo       |          120000 |       6000 |
   | 11 | Marta        | Herrera Gil    |      1 | Desarrollo       |          120000 |       6000 |
   |  5 | Marcos       | Loyola Méndez  |      5 | I+D              |          375000 |     380000 |
   | 10 | Diego        | Flores Salas   |      5 | I+D              |          375000 |     380000 |
   |  3 | Adolfo       | Rubio Flores   |      3 | Recursos Humanos |          280000 |      25000 |
   |  8 | Pepe         | Ruiz Santana   |      3 | Recursos Humanos |          280000 |      25000 |
   |  2 | Adela        | Salas Díaz     |      2 | Sistemas         |          150000 |      21000 |
   |  7 | Pilar        | Ruiz           |      2 | Sistemas         |          150000 |      21000 |
   |  9 | Juan         | Gómez López    |      2 | Sistemas         |          150000 |      21000 |
   +----+--------------+----------------+--------+------------------+-----------------+------------+
   13 rows in set (0.00 sec)
   ```

   

5. Devuelve un listado con los empleados que no tienen ningún departamento
   asociado y los departamentos que no tienen ningún empleado asociado.
   Ordene el listado alfabéticamente por el nombre del departamento.

   ```mysql
   SELECT 
       e.codigo AS IdEmpleado, 
       e.nif AS Nif, 
       e.nombre AS NombreEmpleado, 
       CONCAT(e.apellido1, ' ', IFNULL(e.apellido2, '')) AS ApellidosEmpleado,
       e.codigo_depto AS CodigoDepartamentoEmpleado,
       IFNULL(d.nombre, 'Sin departamento') AS NombreDepartamento
   FROM 
       empleado e
   RIGHT JOIN 
       departamento d ON e.codigo_depto = d.codigo
   WHERE 
       e.codigo_depto IS NULL
   ORDER BY 
       NombreDepartamento ASC;
   ```

   ```
   
   ```

   

**Consultas resumen**

1. Calcula la suma del presupuesto de todos los departamentos.

   

   ```mysql
   
   ```

   ```
   
   ```

   

2. Calcula la media del presupuesto de todos los departamentos.

   

   ```mysql
   
   ```

   ```
   
   ```

   

3. Calcula el valor mínimo del presupuesto de todos los departamentos.

   

   ```mysql
   
   ```

   ```
   
   ```

   

4. Calcula el nombre del departamento y el presupuesto que tiene asignado, del departamento con menor presupuesto.

   

   ```mysql
   
   ```

   ```
   
   ```

   

5. Calcula el valor máximo del presupuesto de todos los departamentos.

   

   ```mysql
   
   ```

   ```
   
   ```

   

6. Calcula el nombre del departamento y el presupuesto que tiene asignado,
   del departamento con mayor presupuesto.

   

   ```mysql
   
   ```

   ```
   
   ```

   

7. Calcula el número total de empleados que hay en la tabla empleado.

   

   ```mysql
   
   ```

   ```
   
   ```

   

8. Calcula el número de empleados que no tienen NULL en su segundo
   apellido.

   

   ```mysql
   
   ```

   ```
   
   ```

   

9. Calcula el número de empleados que hay en cada departamento. Tienes que
   devolver dos columnas, una con el nombre del departamento y otra con el
   número de empleados que tiene asignados.

   

   ```mysql
   
   ```

   ```
   
   ```

   

10. Calcula el nombre de los departamentos que tienen más de 2 empleados. El
    resultado debe tener dos columnas, una con el nombre del departamento y
    otra con el número de empleados que tiene asignados.

    

    ```mysql
    
    ```

    ```
    
    ```

    

11. Calcula el número de empleados que trabajan en cada uno de los
    departamentos. El resultado de esta consulta también tiene que incluir
    aquellos departamentos que no tienen ningún empleado asociado.

    

    ```mysql
    
    ```

    ```
    
    ```

    

12. Calcula el número de empleados que trabajan en cada unos de los
    departamentos que tienen un presupuesto mayor a 200000 euros.

    

    ```mysql
    
    ```

    ```
    
    ```

    

**Subconsultas con operadores básicos de comparación**

1. Devuelve un listado con todos los empleados que tiene el departamento
   de Sistemas. (Sin utilizar INNER JOIN).

   

   ```mysql
   
   ```

   ```
   
   ```

   

2. Devuelve el nombre del departamento con mayor presupuesto y la cantidad
   que tiene asignada.

   

   ```mysql
   
   ```

   ```
   
   ```

   

3. Devuelve el nombre del departamento con menor presupuesto y la cantidad
   que tiene asignada.
   Subconsultas con ALL y ANY

   

   ```mysql
   
   ```

   ```
   
   ```

   

4. Devuelve el nombre del departamento con mayor presupuesto y la cantidad
   que tiene asignada. Sin hacer uso de MAX, ORDER BY ni LIMIT.

   

   ```mysql
   
   ```

   ```
   
   ```

   

5. Devuelve el nombre del departamento con menor presupuesto y la cantidad
   que tiene asignada. Sin hacer uso de MIN, ORDER BY ni LIMIT.

   

   ```mysql
   
   ```

   ```
   
   ```

   

6. Devuelve los nombres de los departamentos que tienen empleados
   asociados. (Utilizando ALL o ANY).

   

   ```mysql
   
   ```

   ```
   
   ```

   

7. Devuelve los nombres de los departamentos que no tienen empleados
   asociados. (Utilizando ALL o ANY).
   Subconsultas con IN y NOT IN

   

   ```mysql
   
   ```

   ```
   
   ```

   

8. Devuelve los nombres de los departamentos que tienen empleados
   asociados. (Utilizando IN o NOT IN).

   

   ```mysql
   
   ```

   ```
   
   ```

   

9. Devuelve los nombres de los departamentos que no tienen empleados
   asociados. (Utilizando IN o NOT IN).
   Subconsultas con EXISTS y NOT EXISTS

   

   ```mysql
   
   ```

   ```
   
   ```

   

10. Devuelve los nombres de los departamentos que tienen empleados
    asociados. (Utilizando EXISTS o NOT EXISTS).

    

    ```mysql
    
    ```

    ```
    
    ```

    

11. Devuelve los nombres de los departamentos que tienen empleados
    asociados. (Utilizando EXISTS o NOT EXISTS).

    

    ```mysql
    
    ```

    ```
    
    ```

    
