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
| Case | Total Numbers ($N$) | Input Elements | Missing Positive Integer | Output |
| :--- | :--- | :--- | :--- | :--- |
| **1** | `3` | 1, 2, 0 | 3 | `3` |

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int N;
    cin >> N;

    vector<int> T(N);
    for(int i = 0; i < N; i++) {
        cin >> T[i];
    }

    int bestStart = 1;
    int maxCount = -1;

    // Try every starting position S
    for(int S = 0; S < N; S++) {
        int count = 0;

        for(int i = 0; i < N; i++) {
            int studentIndex = (S + i) % N;

            if(i >= T[studentIndex]) {
                count++;
            }
        }

        if(count > maxCount) {
            maxCount = count;
            bestStart = S + 1; // convert to 1-based
        }
    }

    cout << bestStart;
    return 0;
}
```

------------------------
------------------------

## C2. Samir has the ability to identify the number of perfect squares present in a two-dimensional array by examining its elements. Help him by writing a computer program that performs this operation efficiently.

Input format :
The input consists of two integers r and c separated by a space, representing the number of rows and columns of the matrix.

This is followed by r lines, each containing c space-separated integers representing the elements of the matrix.

Output format :
The output consists of "Invalid Rows or columns" if either r or c is less than or equal to 0.

Otherwise, a message that indicates the number of perfect squares in the format:

"No Perfect Squares." if the count is 0

"1 Perfect Square." if the count is 1

"<count> Perfect Squares." if the count is more than 1



Refer to the sample output for formatting specifications.

Code constraints :
1 ≤ r, c ≤ 10 (maximum size of the matrix is 10×10).

| Case | Dimensions | Matrix Elements | Output |
| :--- | :--- | :--- | :--- |
| **1** | `3 3` | 56, -8, 5, -6, 8, 9, 7, 4, 19 | `2 Perfect Squares.` |
| **2** | `-8 -6` | — | `Invalid Rows or columns` |
| **3** | `1 6` | 8, 5, 19, 24, 53, 78 | `No Perfect Squares.` |

```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    int r, c;
    cin >> r >> c;

    // Invalid check
    if (r <= 0 || c <= 0) {
        cout << "Invalid Rows or columns";
        return 0;
    }

    int arr[10][10];
    int count = 0;

    // Input matrix
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            cin >> arr[i][j];
        }
    }

    // Check perfect squares
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {

            int num = arr[i][j];

            if (num >= 0) {
                int root = sqrt(num);

                if (root * root == num) {
                    count++;
                }
            }
        }
    }

    // Output format
    if (count == 0) {
        cout << "No Perfect Squares.";
    }
    else if (count == 1) {
        cout << "1 Perfect Square.";
    }
    else {
        cout << count << " Perfect Squares.";
    }

    return 0;
}
```

---------------------
---------------------

## C3. Arjun is curious about number theory and wants to analyze how many distinct prime factors each number has from 1 to N. He decides to write a program to count them for each number up to N, but needs help implementing the logic.



If Arjun accidentally enters a value of N that is less than or equal to 0 or greater than or equal to 50, the program should output -1. Help him to implement the task.



Example:

Sample Input 1:

5

Sample Output 1:

0 1 1 1 1



Explanation:

1 has 0 prime factors

2, 3, 4, 5 all have exactly 1 distinct prime factor

For example, 4 = 2×2 → only one distinct prime (2)

Input format :
The input contains an integer N representing the upper limit of the range.

Output format :
If N is less than or equal to 0 or greater than or equal to 50, print -1.

Otherwise, print the number of distinct prime factors for each number from 1 to N, separated by spaces, in a single line.



Refer to the sample output for formatting specifications.

Code constraints :
-100 ≤ N < 100


Code Size : 1024 kb




