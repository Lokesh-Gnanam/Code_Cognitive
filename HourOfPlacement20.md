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
```cpp
#include <iostream>
using namespace std;

int main() {
    int n, x;
    cin >> n;

    int arr[10];
    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    cin >> x;

    int count = 0;
    int pos = -1;

    for(int i = 0; i < n; i++) {
        if(arr[i] == x) {
            count++;
            if(count == 2) {
                pos = i;
                break;
            }
        }
    }

    if(count == 0) {
        cout << x << " Score not found.";
    }
    else if(count == 1) {
        cout << x << " Score found only once.";
    }
    else {
        cout << pos;
    }

    return 0;
}
```
------------------
------------------

## C3. 
In a warehouse, inventory management requires checking the availability of specific items in stock. Each item in the inventory is identified by a unique numerical ID. Given a list of items currently in the warehouse and a set of item IDs that need to be checked, determine if each item ID from the set is present in the warehouse inventory and identify its position if it is available.



Implement a tool that reads the inventory IDs, followed by a list of item IDs to be checked, and then performs a search to determine if each item ID is present in the inventory. For each item ID, output its position in the inventory if found, or indicate that the item is not available.

Input format :
The first line contains an integer n1, representing the number of items in the warehouse inventory.

The second line contains n1 space-separated integers, representing the IDs of the items in the warehouse inventory.

The third line contains an integer n2, representing the number of item IDs to be checked.

The fourth line contains n2 space-separated integers, representing the item IDs that need to be checked.

Output format :
The output displays for each item ID in the checklist, separated by a line:



If the item ID is found in the inventory, output the item ID followed by its position (1-based index) in the inventory.

If the item ID is not found in the inventory, output the item ID followed by "not found in the inventory".



Refer to the sample outputs for format specifications.

Code constraints :
1 ≤ n1 n2 ≤ 10

The index starts at 1.

| Case | Inventory Size | Inventory Items | Search Count | Items to Search | Output |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1** | `5` | `10, 20, 30, 40, 50` | `4` | `20, 30, 40, 60` | **20** found at position 2<br>**30** found at position 3<br>**40** found at position 4<br>**60** not found in the inventory |
| **2** | `4` | `11, 22, 33, 44` | `2` | `22, 55` | **22** found at position 2<br>**55** not found in the inventory |

----------
```cpp
#include <iostream>
using namespace std;

int main() {
    int n1, n2;
    cin >> n1;

    int inventory[10];

    // Read inventory IDs
    for(int i = 0; i < n1; i++) {
        cin >> inventory[i];
    }

    cin >> n2;

    int check[10];

    // Read IDs to check
    for(int i = 0; i < n2; i++) {
        cin >> check[i];
    }

    // Linear search for each ID
    for(int i = 0; i < n2; i++) {
        bool found = false;

        for(int j = 0; j < n1; j++) {
            if(check[i] == inventory[j]) {
                cout << check[i] << " found at position " << j + 1 << endl;
                found = true;
                break;
            }
        }

        if(!found) {
            cout << check[i] << " not found in the inventory" << endl;
        }
    }

    return 0;
}
```

----------------------
----------------------

## HD CODE 
## 
