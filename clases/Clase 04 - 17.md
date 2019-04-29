Escribir SQL que presente todos los datos de los empleados que ganan el máximo salario de la empresa.
	SELECT * 
	FROM emp
	WHERE sal in (
		SELECT max(sal)
		FROM emp
	);

Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados más antiguos de la empresa.
	SELECT * 
	FROM emp
	WHERE hiredate in (
		SELECT min(hiredate)
		FROM emp
	);

Escirbir la isntrucción SQL que presente en pantalla todos los datos de los empleados que ganan un salario superior al salario promedio de la empresa.
	SELECT * 
	FROM emp
	WHERE sal > (
		SELECT AVG(sal)
		FROM emp
	);

	O

	SELECT * 
	FROM emp
	WHERE sal > (
		SELECT SUM(sal)/COUNT(*)
		FROM emp
	);

Escribir la instrucción SQL que presente en pantalla el código del departamento y el número de empleados que tiene cada departamento.
	SELECT deptno CODIGO, COUNT(*)
	FROM emp
	GROUP BY deptno;

Escribir la instrucción SQL que presente en pantalla el código del departamento, el número de empleados que tiene cada departamento de aquellos departamentos que tengan más de 3 empleados.
	SELECT deptno CODIGO, COUNT(*) EMPLEADOS
	FROM emp
	GROUP BY deptno
	HAVING COUNT(*) > 3;

Escribir la instrucción SQL que presente en pantalla el código del departamento y el número de empleados por departamento que ganan más de $1000. 
	SELECT deptno CODIGO, COUNT(*) EMPLEADOS
	FROM emp
	WHERE sal > 1000
	GROUP BY deptno;

Escribir la instrucción SQL que presente en pantalla el código del departamento y el número de empleados que ganan más de $1000 por departamento de aquellos departamentos en los que exista más de 3 empleados que ganan más de $1000
	SELECT deptno CODIGO, COUNT(*) EMPLEADOS
	FROM emp
	WHERE sal > 1000
	GROUP BY deptno
	HAVING COUNT(*) > 3;

Escribir la instrucción SQL que presente en pantalla el nombre del departamento y el salario total que se paga por departamento de aquellos departamentos en los que se paga más de $10000 como salario.
	SELECT dname DEPARTAMENTO, SUM(sal) SALARIO
	FROM dept, emp
	WHERE dept.deptno = emp.deptno
	GROUP BY dname
	HAVING SUM(sal) > 10000;

Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados que ganan un salario superior al salario individual de todos los empleados del departamento 20.
	SELECT *
	FROM emp
	WHERE sal > (
		SELECT MAX(sal)
		FROM emp
		WHERE deptno = 20
	);

Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados que ganen un salario superior a cualquiera de los salarios individuales de los empleados del departamento 20.
	SELECT *
	FROM emp
	WHERE sal > (
		SELECT MIN(sal)
		FROM emp
		WHERE deptno = 20
	);



















