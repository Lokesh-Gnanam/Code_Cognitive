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

## C1.Problem Statement:



Sameera is collecting drawings from her N students sitting around a circular table. Each student i needs Ti extra minutes to finish their drawing. Sameera collects drawings clockwise, starting from student S, spending exactly 1 minute per student.

Student S gets 0 extra minutes, S+1 gets 1 extra minute, and so on. Students can finish their drawings if their extra time requirement Ti is less than or equal to the extra minutes they get.

Find the starting student ID S (1 ≤ S ≤ N) that allows the maximum number of students to finish their drawings. If there are ties, choose the smallest S.

Input format :
The first line contains an integer N, the number of students sitting around the circular table.

The second line contains N integers, T1,T2,…,TN​, where Ti represents the extra minutes needed by the ith student to finish their drawing.

Output format :
A single integer S, representing the starting student ID from which Sameera should start collecting the drawings to allow the maximum number of students to finish their drawings. If there are multiple valid values of S, choose the smallest S.



Refer to the sample output for formatting specifications.

Code constraints :
1 < N < 105

0 < Ti < N


