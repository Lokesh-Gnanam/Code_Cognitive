# HOUR OF PLACEMENT 2026

## SQL Problem Statement



Write an SQL Query to display the Male employees and their Departments.



Table: Employee

+----+--------+--------+-------+--------------+-----------------+----+

| Id | Name | Age |Gender|Date_of_Join|Department|City|

+----+--------+--------+-------+------------+-------+

| 101 | Mary |35|F|2018-05-12|Sales|New York

| 102 | Mike |28 |M|2018-05-25|IT|Chicago

| 103 | Martin |30|M|2018-06-02|IT|San Diego

| 104 | Sanjay | 28 |M|2018-06-12|HR|Dallas

|105 |Sofia|25|F|2018-07-19|IT|Portland

|106|Maria|F|28|2018-08-24|Sales|Fresno

|107|Elizabeth|24|F|2018-08-24|Sales|Chicago

|108|Emily|26|F|2018-08-24|HR|New York

|109|Donald|27|M|2018-10-17|IT|San Jose

|110| Steven|26|M|2018-10-19|IT|San Francisco

+----+--------+--------------------------

Input format :
The input records are already prepopulated

Output format :
The output should display the male employee's Name and Department as shown below.

Name	Department
Mike	IT
Martin	IT
Sanjay	HR
Donald	IT
Steven	IT
--------------------
```sql
SELECT Name, Department
FROM Employee
WHERE Gender = 'M';
```

-----------------------
-----------------------

## C1. Lena, a financial analyst, needs to sort daily profit and loss values for a stock portfolio, which can be either positive or negative. Using a bubble sorting technique, she must arrange these values in ascending order. 



Help Lena ensure the profit and loss values are sorted accurately.

Input format :
The first line of input consists of an integer n, representing the number of daily values.

The second line consists of n space-separated integers, representing the profit(positive) and loss(negative) values.

Output format :
The output prints the sorted profit and loss values in ascending order.



Refer to the sample output for formatting specifications.

Code constraints :
1 ≤ n ≤ 10

-100 ≤ profit/loss values ≤ 100

| Case | Size ($N$) | Input Array | Sorted Output (Ascending) |
| :--- | :--- | :--- | :--- |
| **1** | `6` | `23, -45, 67, 12, 57, 13` | `-45 12 13 23 57 67` |
| **2** | `7` | `45, 35, 75, 15, -78, 65, -34` | `-78 -34 15 35 45 65 75` |

----------
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    int arr[10];

    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    // Bubble Sort
    for(int i = 0; i < n-1; i++) {
        for(int j = 0; j < n-i-1; j++) {
            if(arr[j] > arr[j+1]) {
                int temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
        }
    }

    // Print sorted array
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```
----------------
----------------

## C2.  You are working as a data analyst for a company that collects user feedback scores for their products. The feedback scores are recorded sequentially, and sometimes you need to identify specific feedback points for analysis.



Given a list of feedback scores and a particular feedback score, your task is to find the position of the second occurrence of this feedback score in the list. If the feedback score appears less than twice, you need to handle that as well:



If the feedback score does not appear at all, print a message indicating that the score was not found.
If the feedback score appears only once, print a message indicating that the score was found only once.
If the feedback score appears more than once, print the position (index) of the second occurrence.
Input format :
The first input line contains an integer n, the number of feedback scores.

The second input line contains n space-separated integers, each representing a feedback score.

The third input line contains an integer X, which is the feedback score you need to find the second occurrence of.

Output format :
The output displays the following format:

The position of the second occurrence of the key in the list, or:
"X Score not found." if the score is not present in the list, or:
"X Score found only once." if the score appears only once.


Refer to the sample output for formatting specifications.

| Case | Size ($N$) | Score List | Target Score | Output |
| :--- | :--- | :--- | :--- | :--- |
| **1** | `5` | 45, 56, 98, 56, 32 | `56` | `3` |
| **2** | `4` | 71, 52, 63, 94 | `89` | `89 Score not found.` |
| **3** | `4` | 85, 96, 32, 45 | `45` | `4` |

---------------------


