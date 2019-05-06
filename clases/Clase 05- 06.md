# Clase 06 de Mayo
### Ejercicios

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados que tienen el salario máximo de la empresa.
```sql
SELECT *
FROM emp
WHERE sal = (
	SELECT MAX(sal) 
	FROM emp
);
```
- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados más antiguos de la empresa.
```sql
SELECT *
FROM emp
WHERE hiredate = (
	SELECT MIN(hiredate) 
	FROM emp
);
```
## SELECT ANINIDADO SINCRONIZADO

- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados que ganan el máximo salario en cada uno de sus departamentos.
```sql
SELECT e.*
FROM emp e
WHERE e.sal = (
	SELECT MAX(sal) 
	FROM emp
	WHERE deptno = e.deptno
);
```
- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados más antiguos en cada departamento.
```sql
SELECT e.*
FROM emp e
WHERE e.hiredate = (
	SELECT MIN(hiredate) 
	FROM emp
	WHERE deptno = e.deptno
);
```
- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados de más reciente contratación en cada departamento.
```sql
SELECT e.*
FROM emp e
WHERE e.hiredate = (
	SELECT MAX(hiredate) 
	FROM emp
	WHERE deptno = e.deptno
);
```
- Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados de aquel departamento que tenga el máximo número de empleados
```sql
SELECT e.* FROM emp e
WHERE e.deptno = (
	SELECT a.deptno 
	FROM (
		SELECT deptno, count(*) emps
		FROM emp
		GROUP BY deptno
	) a
	WHERE a.emps = (
		SELECT MAX(b.emps) 
		FROM (
			SELECT deptno, count(*) emps
			FROM emp
			GROUP BY deptno
		) b
	)
);
```