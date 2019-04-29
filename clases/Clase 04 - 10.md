- SQL que presente en pantalla todos los datos de los empleados más el ingreso total que gana cada empleado.
```sql
SELECT *, sal + COALESCE(comm, 0) TOTAL
FROM emp;
```

- Escribir SQL que presente en pantalla el nombre del empleado, el trabajo que realiza y el ingreso total anual que gana cada empleado.
```sql
SELECT ename NOMBRE, job TRABAJO, (sal + COALESCE(comm, 0)) * 12 "TOTAL ANUAL"
FROM emp;
```

- Escribir SQL que presente en pantalla el número de empleados que tiene la empresa.
```sql 
SELECT COUNT(*)
FROM emp;
& Salario máximo, mínimo, promedio, total
SELECT COUNT(*) TOTAL_EMPLEADOS, SUM(sal) TOTAL_SALARIO, MAX(sal) MAYOR_SALARIO, MIN(sal) MENOR_SALARIO, AVG(sal) PROMEDIO_SALARIO
FROM emp;
```

- Escribir SQL que presente el número de empleados que ganan comisión en la empresa.
```sql
SELECT COUNT(comm) EMPLEADOS_COM
FROM emp;
```
