# Clase 03 de Junio

### Ejercicios

- Escribir la instrucción SQL que presente en pantalla el nombre del departamento y el número de empleados que tiene cada departamento incluídos aquellos departamentos que no tienen empleados.

```sql
SELECT d.dname, count(e.empno)
FROM emp e
RIGHT JOIN dept d ON e.deptno = d.deptno
GROUP BY d.dname;
```

```
Deber 
Revisar vistas
```

- Escribir la instrucción SQL que presente en pantalla el nombre del departamento y el valor total que se paga en salarios y comisiones en cada departamento de todos aquellos departamentos en los que se paga más de 10000 dólares.

```sql
SELECT d.dname, SUM(e.sal + COALESCE(e.comm, 0)) total
FROM emp e, dept d
WHERE e.deptno = d.deptno
GROUP BY d.dname
HAVING total > 10000;
```

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados que ganan el máximo salario de la empresa.

```sql
SELECT *
FROM emp
WHERE sal = (
    SELECT MAX(sal)
    FROM emp
);
```

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados que tienen el salario más alto en cada uno de sus departamentos.

```sql
SELECT e.*
FROM emp e
WHERE sal = (
    SELECT MAX(em.sal)
    FROM emp em
    WHERE em.deptno = e.deptno
);
```

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados más antiguos en cada uno de sus departamentos.

```sql
SELECT e.*
FROM emp e
WHERE hiredate = (
    SELECT MIN(em.hiredate)
    FROM emp em
    WHERE em.deptno = e.deptno
);
```

- Escribir la instrucción SQL que presente en pantalla el nombre del empleado, el trabajo que desempeña, el nombre del departamento al que pertenece el empleado, el nombre del jefe del empleado, el trabajo que desempeña el jefe del empleado y el nombre del departamento al que pertenece el jefe del empleado.

```sql
SELECT e.ename, e.job, de.dname, j.ename, j.job, dj.dname
FROM emp e, dept de, emp j, dept dj
WHERE e.mgr = j.empno
AND e.deptno = de.deptno
AND j.deptno = dj.deptno;
```

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados que realizan la función de jefes.

```sql
SELECT *
FROM emp
WHERE empno IN (
    SELECT mgr
    FROM emp
);
```

- Escribir la instrucción SQL que presente en pantalla el nombre del jefe y el número de empleados que le reportan.

```sql
SELECT j.ename, COUNT(e.empno)
FROM emp j, emp e
WHERE e.mgr = j.empno
GROUP BY j.ename;
```
