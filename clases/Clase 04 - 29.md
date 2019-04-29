# Clase Abril 29
### Ejercicios

- Escribir la instrucción SQL que presente en pantalla el nombre del empleado, el trabajo que desempeña el empleado, el nombre del departamento al que pertenece el empleado, el nombre del jefe del empleado, el trabajo que desempeña el jefe del empleado y el nombre del departamento al que pertenece el jefe del empleado.

```sql
SELECT e.ename NOMBRE, e.job TRABAJO, de.dname DEPARTAMENTO, 
j.ename JEFE, j.job JEFE_TRABAJO, dj.dname JEFE_DEPARTAMENTO 
FROM emp e, emp j, dept de, dept dj 
WHERE e.deptno = de.deptno 
AND e.mgr = j.empno 
AND j.deptno = dj.deptno;
```
```sql
SELECT e.ename NOMBRE, e.job TRABAJO, de.dname DEPARTAMENTO, 
j.ename JEFE, j.job JEFE_TRABAJO, dj.dname JEFE_DEPARTAMENTO 
FROM emp e
JOIN emp j ON e.mgr = j.empno
JOIN dept de ON e.deptno = de.deptno 
JOIN dept dj ON j.deptno = dj.deptno;
```

## NO EQUI JOIN
### Ejercicios
- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados más el grado salarial que le corresponde a cada empleado en función de su salario.

```sql
SELECT emp.*, salgrade.grade 
FROM emp, salgrade
WHERE sal >= losal
AND sal <= hisal;
```