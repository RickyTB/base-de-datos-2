Escribir la instrucción SQL que presente en pantalla todos los datos de los empleados más el nombre del departamento al que pertence cada empleado.

	SELECT e.*, d.dname DEPARTAMENTO
	FROM dept d
	LEFT JOIN emp e
	ON d.deptno = e.deptno
	ORDER BY dname;

Escribir la instrucción SQL que presente en pantalla el nombre del departamento y el número de empleados que tiene cada departamento incluidos aquellos departamentos que no tienen empleados.

	SELECT d.dname DEPARTAMENTO, count(e.empno)
	FROM emp e 
	RIGHT JOIN dept d
	ON e.deptno = d.deptno
	GROUP BY d.dname;

Escribir la instrucción SQL que presente en pantalla el nombre del empleado, el trabajo que desempeña el empleado, el nombre del jefe del empleado, el trabajo que desempeña el jefe del empleado incluidos aquellos empleados que no tienen jefe.

	SELECT e.ename NOMBRE, e.job TRABAJO, j.ename JEFE, j.job JEFE_TRABAJO
	FROM emp e 
	LEFT JOIN emp j
	ON e.mgr = j.empno;

Escribir la instrucción SQL que presente en pantalla el nombre del empleado, el trabajo que desempeña el empleado, el nombre del departamento al que pertenece el empleado, el nombre del jefe del empleado, el trabajo que desempeña el jefe del empleado y el nombre del departamento del jefe del empleado.

	SELECT e.ename NOMBRE, e.job TRABAJO, de.dname DEPARTAMENTO, 
		j.ename JEFE, j.job JEFE_TRABAJO, dj.dname JEFE_DEPARTAMENTO
	FROM emp e, emp j, dept de, dept dj 
	WHERE e.deptno = de.deptno
	AND e.mgr = j.empno
	AND j.deptno = dj.deptno;