# CODE AND COGNITIVE MARCH 2026

## 1. In a classroom with assigned seat numbers ranging from 1 to N, students enter the room and occupy their seats. The seating arrangement is initially in sequential order, but due to a mix-up, one student's seat is left unoccupied. 



Create a program that utilizes binary search to identify and print the seat number that is missing, helping the teacher quickly resolve the seating discrepancy.

Input format :
The first line of input consists of an integer N, representing the total number of seats in the classroom.

The second line consists of N distinct space-separated integers, representing the occupied seat numbers.

Output format :
The output prints a single integer, representing the missing seat number.

If no seat is found missing, print "No missing seat number found in the classroom."



Refer to the sample output for formatting specifications.

Code constraints :
1 ≤ N ≤ 10

| Case | Total Seats ($N$) | Seat Numbers Present | Output |
| :--- | :--- | :--- | :--- |
| **1** | `7` | 1 2 3 4 6 7 8 | `5` |
| **2** | `6` | 2 3 4 5 6 7 | `1` |
| **3** | `3` | 1 2 3 | `No missing seat number found in the classroom.` |

------------------
```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int arr[10];

    for(int i = 0; i < n; i++)
        cin >> arr[i];

    sort(arr, arr + n);

    int left = 0, right = n - 1;
    int missing = -1;

    while(left <= right)
    {
        int mid = (left + right) / 2;

        if(arr[mid] != mid + 1)
        {
            missing = mid + 1;
            right = mid - 1;
        }
        else
        {
            left = mid + 1;
        }
    }

    if(missing == -1)
        cout << "No missing seat number found in the classroom.";
    else
        cout << missing;

    return 0;
}
```

----------------
----------------

## 2.In a local election, each candidate is assigned a unique numeric ID. After collecting the votes, you need to determine if any candidate received more than n−2 votes, where n is the total number of votes cast. This will help in identifying if there is a clear winner with significant support.



Your task is to write a program that determines if there is a candidate ID that received more than n−2 votes. If such a candidate exists, return their ID. Otherwise, return "No majority candidate found."

Input format :
The first line contains an integer n - the total number of votes cast.

The second line contains n space-separated integers, each representing the candidate ID for each vote.

Output format :
The output displays the following format:

If a candidate received more than n−2 votes, output their ID.

If no candidate meets this criterion, output "No majority candidate found."



Refer to the sample output for formatting specifications.

Code constraints :
1 ≤ n ≤ 10

1 ≤ candidate ID ≤ 100

| Case | Total Votes ($N$) | Candidate IDs | Output |
| :--- | :--- | :--- | :--- |
| **1** | `5` | 1, 4, 1, 1, 1 | `1` |
| **2** | `8` | 12, 12, 12, 12, 13, 12, 12, 12 | `12` |
| **3** | `5` | 56, 58, 45, 54, 55 | `No majority candidate found.` |



-----------
```cpp
#include <iostream>
#include <map>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int arr[10];
    map<int,int> freq;

    for(int i = 0; i < n; i++)
    {
        cin >> arr[i];
        freq[arr[i]]++;
    }

    for(auto it : freq)
    {
        if(it.second > n - 2)
        {
            cout << it.first;
            return 0;
        }
    }

    cout << "No majority candidate found.";

    return 0;
}

```

-------------------
-------------------

## 3.Lalit and his friends are playing cards sitting around a circular table. Each player is represented by a node in a circular linked list, where the data in the node represents the player's unique identifier. After the first game, the first player and the last player exchange their positions. Pranav, who is watching the game, wants to simulate this scenario using a circular linked list.



Help Pranav write a program to manage this scenario by implementing the following operations:



Insert nodes (players) into the circular linked list.
Traverse the circular linked list to display the players.
Exchange the first and last nodes (players) in the circular linked list.
Input format :
The first line of input contains an integer m, the number of players.

The second line contains m space-separated integers representing the unique identifiers of the players.

Output format :
The output displays the list of players before and after the exchange of the first and last nodes in separate lines.



Refer to the sample output for the formatting specifications.

Code constraints :
In this scenario, the test cases fall under the following constraints:

2 ≤ m ≤ 20

1 ≤ unique idenitifiers ≤ 100

| Case | Size ($N$) | Input Array | Before Swap | After Swap |
| :--- | :--- | :--- | :--- | :--- |
| **1** | `10` | `3, 4, 5, 6, 7, 8, 1, 2, 3, 9` | 3 4 5 6 7 8 1 2 3 9 | **9** 4 5 6 7 8 1 2 3 **3** |
| **2** | `3` | `10, 20, 30` | 10 20 30 | **30** 20 **10** |

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

Node* head = NULL;

// Insert node into circular linked list
void insert(int value) {
    Node* newNode = new Node();
    newNode->data = value;

    if (head == NULL) {
        head = newNode;
        newNode->next = head;
    } 
    else {
        Node* temp = head;
        while (temp->next != head) {
            temp = temp->next;
        }

        temp->next = newNode;
        newNode->next = head;
    }
}

// Traverse and display
void display() {
    if (head == NULL) return;

    Node* temp = head;

    do {
        cout << temp->data << " ";
        temp = temp->next;
    } while (temp != head);
}

// Swap first and last node data
void swapFirstLast() {
    if (head == NULL || head->next == head) return;

    Node* temp = head;

    while (temp->next != head) {
        temp = temp->next;
    }

    // temp is last node
    int t = head->data;
    head->data = temp->data;
    temp->data = t;
}

int main() {

    int m;
    cin >> m;

    for(int i=0;i<m;i++) {
        int x;
        cin >> x;
        insert(x);
    }

    cout << "Before Swap: ";
    display();

    swapFirstLast();

    cout << "\nAfter Swap: ";
    display();

    return 0;
}
```

---------------------
----------------------

## 4. David, an HR manager, maintains a dynamic list of employee IDs using a linked list. Occasionally, he needs to remove a specific employee from the list based on their position in the sequence. Implement a function using circular linked list that deletes the k-th employee from the list and returns the updated list.

Input format :
The first line of input consists of an integer (n), representing the number of employees in the linked list.

The second line consists of n space-separated integers, representing the employee IDs in the linked list.

The third line consists of an integer (k), representing the 1-based position of the employee to remove.

Output format :
The program outputs the updated list of employee IDs after deleting the employee at position k, printed as space-separated integers in a single line.



Refer to the sample output for the formatting specifications.

| Case | Total Employees ($n$) | Employee IDs | Position to Remove ($k$) | Output |
| :--- | :--- | :--- | :--- | :--- |
| **1** | `5` | 10, 20, 30, 40, 50 | `4` | `10 20 30 50` |
| **2** | `7` | 7270, 5318, 2964, 4237, 7388, 7010, 2468 | `4` | `7270 5318 2964 7388 7010 2468` |

```cpp

```

---------------------
---------------------

## 5.
---------------------
