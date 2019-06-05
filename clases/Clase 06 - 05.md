# Clase 05 de Junio

### Ejercicios 

- Escribir la instrucción SQL que presente en pantalla el nombre del empleado, el trabajo que desempeña el empleado, el nombre del jefe del empleado y el trabajo que desempeña el jefe del empleado de todos los empleados incluídos aquellos que no tienen jefe.

```sql
SELECT e.ename EMPLEADO, e.job TRABAJO, j.ename JEFE, j.job TRABAJO_JEFE
FROM emp e 
LEFT JOIN emp j ON e.mgr = j.empno;
```

- Escribir la instrucción SQL que presente en pantalla el nombre del departamento, el trabajo y el número de empleados que realizan dicho trabajo en cada departamento.

```sql
SELECT d.dname DEPARTAMENTO, e.job TRABAJO, count(e.empno) EMPLEADOS
FROM emp e, dept d
WHERE e.deptno = d.deptno
GROUP BY d.dname, e.job;
```

- Escribir la instrucción SQL que presente en pantalla el nombre del departamento y el número de empleados por departamento que ganan más de 1000 dólares de todos aquellos departamentos en los que exista más de dos empleados que ganan más de 1000 dólares.

```sql
SELECT d.dname DEPARTAMENTO, COUNT(e.empno) EMPLEADOS
FROM emp e, dept d
WHERE e.deptno = d.deptno
AND (e.sal + COALESCE(e.comm, 0)) > 1000
GROUP BY d.dname
HAVING COUNT(e.empno) > 2;
```

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados que ganan un salario superior al salario promedio de cada departamento.

```sql
SELECT e.*, (
    SELECT AVG(em.sal)
    FROM emp em
    WHERE em.deptno = e.deptno
) Promedio
FROM emp e 
WHERE e.sal > (
    SELECT AVG(em.sal)
    FROM emp em
    WHERE em.deptno = e.deptno
);
```

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados más el grado salarial que le corresponde a cada empleado en función del salario que percibe y más el nombre del departamento al que pertenece cada empleado.

```sql
SELECT emp.*, salgrade.grade, dept.dname
FROM emp, salgrade, dept
WHERE emp.deptno = dept.deptno
AND sal BETWEEN losal AND hisal;
``