# HOUR OF PLACEMENT 2026

## MYSQL
## Write a query to change the datatype of the column departmentId in the table 'department' to int(30).
Note: The required table is already populated in the back end.

Input format :
The input records are already prepopulated, as given in the problem statement.

Output format :
The output displays the table details after changing the datatype of the column departmentId in the table department in the below format:

Field	Type	Null	Key	Default	Extra
departmentId	int	NO	PRI	NULL	
departmentName	varchar(30)	NO		NULL	
details	varchar(50)	NO		NULL	
userId	int	NO	MUL	NULL	

Refer to the sample output for the formatting specifications.

Note :

```mysql
ALTER TABLE department
MODIFY departmentId INT(30) NOT NULL;
```

------------------------
------------------------

##
