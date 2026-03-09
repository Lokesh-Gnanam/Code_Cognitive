# DailyCodes
## 1. Viswas wants to spend his weekend watching some short films. He has a list of short films with ratings and prefers to watch the highest-rated films first. To plan his viewing, he wants to see how the selection sort algorithm would organize the films in descending order, step by step.



You are required to implement Selection Sort in descending order and print the array after each step, showing how the list evolves until fully sorted.

Input format :
The first line contains an integer n, representing the number of films.

The second line contains n space separated integers, representing the ratings of the films.

Output format :
After each iteration (step) of the selection sort, print

"After his step : i"

where i is the step number (starting from 1), followed by the current array state.

After sorting is complete, print

"Finally, he got it..."

followed by the sorted array in descending order.



Refer to the sample output for the formatting specifications

Code constraints :
1 ≤ n ≤ 10

0 ≤ rating ≤ 100
## Sample Test Cases


| Input | Output |
| :--- | :--- |
| **5**<br>`3 4 5 1 2` | `After his step : 1`<br>`5 4 3 1 2`<br>`After his step : 2`<br>`5 4 3 1 2`<br>`After his step : 3`<br>`5 4 3 1 2`<br>`After his step : 4`<br>`5 4 3 2 1`<br>**Finally, he got it...**<br>`5 4 3 2 1` |
| **5**<br>`34 54 2 3 1` | `After his step : 1`<br>`54 34 2 3 1`<br>`After his step : 2`<br>`54 34 2 3 1`<br>`After his step : 3`<br>`54 34 3 2 1`<br>`After his step : 4`<br>`54 34 3 2 1`<br>**Finally, he got it...**<br>`54 34 3 2 1` |

---
Solution:
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int a[10];

    for(int i = 0; i < n; i++)
        cin >> a[i];

    for(int i = 0; i < n - 1; i++)
    {
        int maxIndex = i;

        // find maximum element in remaining array
        for(int j = i + 1; j < n; j++)
        {
            if(a[j] > a[maxIndex])
            {
                maxIndex = j;
            }
        }

        // swap
        int temp = a[i];
        a[i] = a[maxIndex];
        a[maxIndex] = temp;

        cout << "After his step : " << i + 1 << endl;

        for(int k = 0; k < n; k++)
            cout << a[k] << " ";

        cout << endl;
    }

    cout << "Finally, he got it..." << endl;

    for(int i = 0; i < n; i++)
        cout << a[i] << " ";

    return 0;
} 
```
-------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------




## 2.In modern operating systems, multiple applications run concurrently and are managed efficiently. A Circular Linked List (CLL) is an effective data structure that can be used to organize and iterate over these running applications in a cyclic manner.



Write a program to implement a Circular Linked List that stores the names of currently running applications. The program should accept application names as input and allow iteration over them. If no applications are provided, it should indicate that there are no running applications.

Input format :
The input consists of multiple lines, each containing the name of an application.

The input continues until the user enters "exit", which signals the end of input.



Refer to the sample input for a better understanding.

Output format :
The first line of output prints "Circular Linked List - Running Applications"

If applications were added:

The next line prints "Running Applications:"
Followed by each application name on a new line in the order they were added.
If no applications were added before typing exit:

It directly prints "No applications to iterate."


Refer to the sample output for formatting specifications.

Code constraints :
The given test cases fall under the following constraints:

Each application name is a string with a maximum length of 100 characters.

## Sample Test Cases


| Case | Input | Output |
| :--- | :--- | :--- |
| **1** | `Microsoft Office Suite`<br>`Adobe Creative Cloud`<br>`Google Chrome`<br>`Mozilla Firefox`<br>`VLC Media Player`<br>`Skype`<br>`exit` | **Circular Linked List - Running Applications**<br>Running Applications:<br>`Microsoft Office Suite`<br>`Adobe Creative Cloud`<br>`Google Chrome`<br>`Mozilla Firefox`<br>`VLC Media Player`<br>`Skype` |
| **2** | `exit` | **Circular Linked List - Running Applications**<br>No applications to iterate. |

----

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Node
{
    string data;
    Node* next;
};

int main()
{
    Node* head = NULL;
    Node* temp = NULL;

    string app;

    while(true)
    {
        getline(cin, app);

        if(app == "exit")
            break;

        Node* newNode = new Node;
        newNode->data = app;

        if(head == NULL)
        {
            head = newNode;
            newNode->next = head;
            temp = head;
        }
        else
        {
            temp->next = newNode;
            newNode->next = head;
            temp = newNode;
        }
    }

    cout << "Circular Linked List - Running Applications" << endl;

    if(head == NULL)
    {
        cout << "No applications to iterate." << endl;
    }
    else
    {
        cout << "Running Applications:" << endl;

        Node* current = head;

        do
        {
            cout << current->data << endl;
            current = current->next;
        }
        while(current != head);
    }

    return 0;
}
```
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------

## 3.Ashok is learning about doubly linked lists. He wants to write a program to insert a node in the middle of a doubly linked list.

As his friend, you have to guide Ashok in the program.

Input format :
The first line of input consists of an integer n, indicating the number of elements to be added to the doubly linked list.

The second line consists of n integers to be added to the doubly linked list.

The third line consists of an integer m, indicating the integer to be added in the middle of the doubly linked list.

Output format :
The output prints the updated linked list after inserting the element in the middle of the list.



Refer to the sample output for formatting specifications.

Code constraints :
1 ≤ n ≤ 30 (The value of n will be even)

1 ≤ list elements ≤ 105

## Sample Test Cases


| Input | Output |
| :--- | :--- |
| **4**<br>`1 2 3 4`<br>**7** | `1 2 7 3 4` |
| **6**<br>`1 2 3 4 5 6`<br>**9** | `1 2 3 9 4 5 6` |

------

```cpp
#include <iostream>
using namespace std;

struct Node
{
    int data;
    Node* prev;
    Node* next;
};

int main()
{
    int n;
    cin >> n;

    Node* head = NULL;
    Node* temp = NULL;

    for(int i = 0; i < n; i++)
    {
        int x;
        cin >> x;

        Node* newNode = new Node;
        newNode->data = x;
        newNode->prev = NULL;
        newNode->next = NULL;

        if(head == NULL)
        {
            head = newNode;
            temp = head;
        }
        else
        {
            temp->next = newNode;
            newNode->prev = temp;
            temp = newNode;
        }
    }

    int m;
    cin >> m;

    int pos = n / 2;

    Node* current = head;

    for(int i = 1; i < pos; i++)
    {
        current = current->next;
    }

    Node* newNode = new Node;
    newNode->data = m;

    newNode->next = current->next;
    newNode->prev = current;

    current->next->prev = newNode;
    current->next = newNode;

    Node* display = head;

    while(display != NULL)
    {
        cout << display->data << " ";
        display = display->next;
    }

    return 0;
}
```
-------------------------------------------------
--------------------------------------------------------
## 4. Imagine you are working as a librarian in a large library. The library uses an automated system to keep track of book positions on the shelves. Each book is assigned a unique ID, but some IDs are more common than others due to the popularity of certain editions.



The system logs the positions of books in a sorted list based on their IDs. You need to find the first and last positions of a specific book ID in this sorted list using recursive binary search.



Example

Input:

10 

1 2 2 2 2 3 4 8 8 8 

8



Output:

7 9



Explanation:

The first and last positions of book ID 8 are [7, 9] since the index is 0-based.

Input format :
The first line of input consists of an integer n, representing the total number of book IDs.

The second line consists of a sorted list of n integers representing the book IDs.

The third line consists of an integer x, representing the specific book ID to find.

Output format :
The output displays indexes of the first and last occurrence of x, as space-separated integers.

If book ID x is not present in the shelves, print "NO OCCURRENCES".



Refer to the sample output for formatting specifications.

Code constraints :
The given test cases fall under the following specifications:

1 ≤ n ≤ 20

1 ≤ book ID, x ≤ 100
## Sample Test Cases


| Input | Output |
| :--- | :--- |
| **10**<br>`1 2 2 2 2 3 4 8 8 8`<br>**8** | `7 9` |
| **10**<br>`1 2 2 2 2 3 4 8 8 8`<br>**5** | `NO OCCURRENCES` |

----

```cpp
#include <iostream>
using namespace std;

int firstOcc(int arr[], int low, int high, int x)
{
    if(low > high)
        return -1;

    int mid = (low + high) / 2;

    if(arr[mid] == x)
    {
        if(mid == 0 || arr[mid-1] != x)
            return mid;
        else
            return firstOcc(arr, low, mid-1, x);
    }
    else if(arr[mid] > x)
        return firstOcc(arr, low, mid-1, x);
    else
        return firstOcc(arr, mid+1, high, x);
}

int lastOcc(int arr[], int low, int high, int x, int n)
{
    if(low > high)
        return -1;

    int mid = (low + high) / 2;

    if(arr[mid] == x)
    {
        if(mid == n-1 || arr[mid+1] != x)
            return mid;
        else
            return lastOcc(arr, mid+1, high, x, n);
    }
    else if(arr[mid] > x)
        return lastOcc(arr, low, mid-1, x, n);
    else
        return lastOcc(arr, mid+1, high, x, n);
}

int main()
{
    int n;
    cin >> n;

    int arr[20];

    for(int i=0;i<n;i++)
        cin >> arr[i];

    int x;
    cin >> x;

    int first = firstOcc(arr,0,n-1,x);
    int last = lastOcc(arr,0,n-1,x,n);

    if(first == -1)
        cout<<"NO OCCURRENCES";
    else
        cout<<first<<" "<<last;

    return 0;
}
```
--------------------------------------------------------------------------------------
---------------------------------------------------
## 5.Tom is working in a warehouse inventory system, where the item IDs are assigned sequentially in ascending order. 



He wants to develop a program using recursive binary search to efficiently determine the closest item ID that is less than or equal to a given target ID. 



The program takes the total number of items and their sorted IDs as input, assisting warehouse staff in quickly identifying the closest available item less than or equal to the target ID. Help Tom in this program.

Input format :
The first line of input consists of an integer N, representing the number of items in the warehouse.

The second line consists of N space-separated integers, representing the sorted list of item IDs.

The third line consists of an integer representing the target item ID.

Output format :
The output prints "The closest item ID less than or equal to X is Y", where X is the target ID and Y is the closest item ID less than or equal to X.

If no such element exists, print "No closest item with an ID less than or equal to X exists in the warehouse", where X is the target ID.



Refer to the sample output for formatting specifications.

Code constraints :
In this scenario, the test cases fall under the following constraints:

1 ≤ N ≤ 10

1 ≤ item ID ≤ 100

## Sample Test Cases


| Case | Input | Output |
| :--- | :--- | :--- |
| **1** | **7**<br>`17 25 38 47 51 62 79`<br>**50** | The closest item ID less than or equal to 50 is **47** |
| **2** | **6**<br>`41 52 58 61 65 72`<br>**65** | The closest item ID less than or equal to 65 is **65** |
| **3** | **5**<br>`12 15 24 25 35`<br>**10** | No closest item with an ID less than or equal to 10 exists in the warehouse |

----

```cpp
#include <iostream>
using namespace std;

int findClosest(int arr[], int low, int high, int x)
{
    if(low > high)
        return -1;

    int mid = (low + high) / 2;

    if(arr[mid] == x)
        return arr[mid];

    if(arr[mid] > x)
        return findClosest(arr, low, mid - 1, x);

    int temp = findClosest(arr, mid + 1, high, x);

    if(temp <= x && temp != -1)
        return temp;
    else
        return arr[mid];
}

int main()
{
    int n;
    cin >> n;

    int arr[10];

    for(int i = 0; i < n; i++)
        cin >> arr[i];

    int target;
    cin >> target;

    int result = findClosest(arr, 0, n - 1, target);

    if(result == -1)
        cout << "No closest item with an ID less than or equal to " << target << " exists in the warehouse";
    else
        cout << "The closest item ID less than or equal to " << target << " is " << result;

    return 0;
}
```
---------------------------------------
-----------------------------------------

## 6.On the first day of school, students randomly take seats in class. Since taller students are sitting in front of shorter ones, some students can't see the board properly.



To fix this, the teacher asks the students to stand in a line and arranges them in increasing order of height using the Selection Sort technique.



She follows this method:



From the current position to the end of the line, she finds the shortest student.
Then she swaps that student with the one currently at the position.
She repeats this process for all students.


Write a program that sorts the heights of students using Selection Sort.

Input format :
The first line of input contains an integer n, the number of students.

The second line of input contains n space-separated integers representing the heights of the students.

Output format :
The first line of the output prints "Students' height order before sorting:"

The second line prints the heights of the students as they were input, separated by spaces.

For each iteration of the sorting process (from 1 to n-1), the following two lines are printed:

A line those prints "At the end of iteration X:" where X is the current iteration number.

The next line prints the current state of the array (heights after that iteration), space separated.

After all sorting iterations, the next line prints "After sorting, the height order is:"

The final line prints the sorted list of student heights in ascending order, space separated.



Refer to the sample output for formatting specifications.

Code constraints :
The given testcases fall under the following constraints:

1 ≤ elements of array ≤ 104

## Sample Test Cases


| Case | Input | Output |
| :--- | :--- | :--- |
| **1** | **5**<br>`170 168 154 178 166` | **Students' height order before sorting:**<br>`170 168 154 178 166`<br>**At the end of iteration 1:**<br>`154 168 170 178 166`<br>**At the end of iteration 2:**<br>`154 166 170 178 168`<br>**At the end of iteration 3:**<br>`154 166 168 178 170`<br>**At the end of iteration 4:**<br>`154 166 168 170 178`<br>**After sorting, the height order is:**<br>`154 166 168 170 178` |
| **2** | **10**<br>`132 129 144 177 148 134 157 133 183 155` | **Students' height order before sorting:**<br>`132 129 144 177 148 134 157 133 183 155`<br>**...** (iterations 1-9) ...<br>**After sorting, the height order is:**<br>`129 132 133 134 144 148 155 157 177 183` |

----------

```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int arr[100];

    for(int i = 0; i < n; i++)
        cin >> arr[i];

    cout << "Students' height order before sorting:" << endl;

    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    for(int i = 0; i < n-1; i++)
    {
        int minIndex = i;

        for(int j = i+1; j < n; j++)
        {
            if(arr[j] < arr[minIndex])
                minIndex = j;
        }

        // swap
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;

        cout << "At the end of iteration " << i+1 << ":" << endl;

        for(int k = 0; k < n; k++)
            cout << arr[k] << " ";
        cout << endl;
    }

    cout << "After sorting, the height order is:" << endl;

    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";

    return 0;
}
```
------------------------------------------------------------------------
------------------------------------------------------------------------

## 7.You are given an array nums of positive integers representing the quantities of items available in a store. Each index i in the array represents a different item, and the value nums[i] represents the quantity of that item.



You need to serve customers who arrive at your store one by one. Each customer demands a specific quantity of items. If you have enough quantity of the requested item, you will serve the customer and reduce the quantity of that item by the requested amount. If you don't have enough quantity of the requested item, you will skip that customer and move on to the next one.



Your goal is to determine the total number of customers you can serve while optimizing the remaining items in the store.



Write a function that takes the array nums representing the initial quantities of items and an array of customers representing the quantities of items each customer demands. The function should return the maximum number of customers that can be served while ensuring that the remaining quantities of items in the store are minimized.



Example

Sample Input1 

4

5 10 8 6

3

7 5 12

Sample Output 1

Maximum number of customers served: 2

Explanation

Customer 1 demands 7, and an item with quantity 6 can be served.

Customer 2 demands 5, and an item with quantity 5 can be served.

Customer 3 demands 12, but no item can be served, so skipped.

Only 2 customers can be served.



Sample Input 2

6

10 15 20 5 8 18

3

8 12 5

Output

Maximum number of customers served: 3

Explanation

Customer 1 demands 8, and an item with quantity 8 can be served.

Customer 2 demands 12, and items with quantities 10 and 5 can be served.

Customer 3 demands 5, and an item with quantity 5 can be served.

All 3 customers can be served.

Input format :
The first line contains an integer n representing the number of items in the store.

The second line contains n space-separated integers representing the initial quantities of items.

The third line contains an integer m represents the number of customers.

The fourth line contains m space-separated integers representing the quantities of items each customer demands.

Output format :
The output returns the maximum number of customers that can be served while optimizing the remaining quantities of items in the store.



Refer to the sample output for formatting specifications.

Code constraints :
The quantities of items in both arrays are positive integers.

2 ≤ n, m ≤ 10
1 ≤ nums[i], customers[i] ≤ 30


Hidden Test Case Design (Extreme Value Coverage)

Hidden test cases include boundary values from the given constraint range to ensure robustness and full validation.

Minimum number of items and customers: n = 2, m = 2
Maximum number of items and customers: n = 10, m = 10
Minimum quantity value: 1
Maximum quantity value: 30

### **Sample Test Cases**

| Test Case | Input Data | Output |
| :--- | :--- | :--- |
| **Case 1** | **Inventory Size:** 4<br>**Inventory:** `5 10 8 6`<br>**Requests Size:** 3<br>**Requests:** `7 5 12` | `Maximum number of customers served: 2` |
| **Case 2** | **Inventory Size:** 6<br>**Inventory:** `10 15 20 5 8 18`<br>**Requests Size:** 3<br>**Requests:** `8 12 5` | `Maximum number of customers served: 3` |

---

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> nums(n);
    for(int i=0;i<n;i++)
        cin >> nums[i];

    int m;
    cin >> m;

    vector<int> customers(m);
    for(int i=0;i<m;i++)
        cin >> customers[i];

    int served = 0;

    for(int i=0;i<m;i++) {

        int idx = -1;
        int best = 1e9;

        for(int j=0;j<n;j++) {

            if(nums[j] >= customers[i] && nums[j] < best) {
                best = nums[j];
                idx = j;
            }
        }

        if(idx != -1) {
            nums[idx] -= customers[i]; // quantity reduce
            served++;
        }
    }

    cout << "Maximum number of customers served: " << served;

    return 0;
}
```
--------------------------------------
--------------------------------------

## 8.Shreya has an array of integers and needs to perform a series of operations to maximize the value of the array after merging its elements. The merging process is defined as follows:



If i and j are two indices of the array (i ≠ j), merging the jth element into the ith element makes a[i] become a[i] - a[j] and remove a[j] from the array.



Depending on the nature of the array (positive, negative, or mixed), specific rules apply to maximize the resulting value:

If the array contains both positive and negative elements, then add absolute value to all elements of the array.
If the array contains only positive elements, subtract the smallest element from the sum of all elements.
If the array contains only negative elements, replace all elements with their absolute values and subtract the smallest element from the sum of all elements.


Write a program to calculate the maximum possible value of the array after applying these operations.



Example

Sample Input 1

4

2 1 2 1

Sample Output 1 

4

Explanation

Merge the 3rd element into the 2nd element, then the array becomes {2, -1, 1}.

Merge the 3rd element into the 2nd element, then the array becomes {2, -2}.

Merge the 2nd element into the 1st element, then the array becomes {4}.

The maximum possible value after merging is 4.





Sample Input 2 

5

1 3 5 -2 -6

Sample Output 2

17

Explanation

Merge the 4th element into the 3rd element, then the array becomes {1, 3, -7, -6}.

Merge the 2nd element into the 3rd element, then the array becomes {1, -10, -6}.

Merge the 2nd element into the 1st element, then the array becomes {11, -6}.

Merge the 2nd element into the 1st element, then the array becomes {17}.

The maximum possible value after merging is 17.

Input format :
The first line of input consists of an integer N, representing the size of the array.

The second line consists of N space-separated integers, representing the elements of the array.

Output format :
The output prints the maximum possible value after merging elements in the array.



Refer to the sample output for the formatting specifications.

Code constraints :
1 ≤ N ≤ 10

-20 ≤ array elements ≤ 21

### Sample Test Cases

| Test Case | Input | Output |
| :--- | :--- | :--- |
| **Case 1** | `4`<br>`2 1 2 1` | `4` |
| **Case 2** | `5`<br>`1 3 5 -2 -6` | `17` |
| **Case 3** | `3`<br>`-5 0 5` | `10` |

---

```cpp
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> a(n);

    bool hasPos = false, hasNeg = false;

    for(int i=0;i<n;i++) {
        cin >> a[i];

        if(a[i] > 0) hasPos = true;
        if(a[i] < 0) hasNeg = true;
    }

    int sum = 0;
    int mn = 1e9;

    for(int i=0;i<n;i++) {
        sum += abs(a[i]);
        mn = min(mn, abs(a[i]));
    }

    int ans;

    if(hasPos && hasNeg) {
        ans = sum;
    }
    else {
        ans = sum - 2*mn;
    }

    cout << ans;

    return 0;
}
```

---------------------------
---------------------------

## 9.Sheldon Cooper has a square-shaped puzzle made up of small square pieces containing numbers on them. He wants to rearrange the puzzle by changing the elements of a row into a column element and the column element into a row element without altering the shape of the puzzle. Help Sheldon solves this puzzle. Write a program to find the transpose of the given 2D matrix.

Input format :
Refer to the sample input and output for specifications.

Output format :
The output prints the given matrix and transposed matrix.

Refer to the sample input and output for specifications.

| Case | Input | Original Matrix | Transposed Matrix |
| :--- | :--- | :--- | :--- |
| **1** | `3` (Size)<br>`1, 2, 3`<br>`4, 5, 6`<br>`7, 8, 9` | 1 2 3<br>4 5 6<br>7 8 9 | 1 4 7<br>2 5 8<br>3 6 9 |
| **2** | `2` (Size)<br>`1, 5`<br>`9, 8` | 1 5<br>9 8 | 1 9<br>5 8 |
-------------
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    int a[n][n];

    // Input matrix
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cin >> a[i][j];
        }
    }

    // Print original matrix
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cout << a[i][j] << " ";
        }
        cout << endl;
    }

    cout << "Transpose matrix is:" << endl;

    // Print transpose
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cout << a[j][i] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
------------------------------------
------------------------------------
## 10.Problem Statement :



Sum of 2 arrays



Ramu has some number of Apples and he arranges that in a matrix format. Raju has another number of Apples. He also wants to arrange that in a matrix format. Ragul wants to calculate the total number of apples. Help him to find out the total number of apples.

Input format :
Input consists of 2n+1 integers.

The first integer corresponds to ‘n’, the size of the array.

The next ‘n’ integers correspond to the elements in the first array.

The last 'n' integers correspond to the elements in the second array. Assume that the maximum value of n is 15.

Output format :
The output consists of the sum of 2 arrays.

Refer sample output for details.

| Case | Size ($N$) | Vector A | Vector B | Output (A + B) |
| :--- | :--- | :--- | :--- | :--- |
| **1** | `5` | `2, 3, 6, 8, 1` | `1, 1, 1, 1, 1` | 3, 4, 7, 9, 2 |
| **2** | `3` | `1, 2, 3` | `1, 2, 3` | 2, 4, 6 |
-----------------

```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int a[15], b[15];

    // first array input
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    // second array input
    for(int i = 0; i < n; i++)
    {
        cin >> b[i];
    }

    // sum of arrays
    for(int i = 0; i < n; i++)
    {
        cout << a[i] + b[i] << endl;
    }

    return 0;
}
```
----------------------------------------------------------------------------------
----------------------------------------------------------------------------------

## 11.



