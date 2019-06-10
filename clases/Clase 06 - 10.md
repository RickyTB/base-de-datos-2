# Vistas

### Ejercicios

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados más el nombre del departamento al que pertenece cada empleado de los departamentos 10 y 30.

```sql
CREATE VIEW EMPLEADOS_DEP_10_30 AS
SELECT e.*, d.dname DEPARTAMENTO
FROM emp e, dept d
WHERE e.deptno = d.deptno
AND (e.deptno = 30 OR e.deptno = 30);
```

- Escribir la instrucción SQL que presente en pantalla el código del empleado, el nombre del empleado, el trabajo que desempeña el empleado, el salario y el código de departamento al cual pertenece el empleado, de los empleados de los departamentos 10 y 30.

```sql
SELECT empno, ename, job, sal, deptno
FROM EMPLEADOS_DEP_10_30
```