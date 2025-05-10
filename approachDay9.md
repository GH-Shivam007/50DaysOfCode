# 💡 C++ Code Explanation with Diagrams

## 🚀 Problem 1: Nth Digit
### 🔍 Problem Statement
Given an integer `n`, return the nth digit of the infinite integer sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, ... (1-based indexing).

### ✅ Approach
- Start with a variable `digitInNum` initialized to 1, and variables `start` and `end` initialized to 1 and 9, respectively.
- Check if the number `n` is greater than `digitInNum * end`. If so, adjust `n` and update the values for `digitInNum`, `start`, and `end`.
- Calculate the number that contains the nth digit and convert it to a string.
- Return the digit from the string representation of the number.

### 🧾 Code
```cpp
class Solution {
public:
    int findNthDigit(int n) {
        long digitInNum = 1, start = 1, end = 9;

        while (n > digitInNum * end) {
            n -= digitInNum * end;
            digitInNum++;
            start *= 10;
            end *= 10;
        }

        long num = start + (n - 1) / digitInNum;
        string numStr = to_string(num);
        return numStr[(n - 1) % digitInNum] - '0';
    }
};
📈 Time & Space Complexity
Time Complexity: O(log n), where n is the value of the input integer.

Space Complexity: O(1) (constant space as no additional space is used except for variables).

🧠 Insight
This approach cleverly breaks down the problem into segments based on the number of digits in each group (1-digit numbers, 2-digit numbers, etc.). The nth digit is then determined by identifying which number contains it.

🔁 Flowchart (Mermaid)
mermaid
Copy
Edit
graph TD;
    A[Start] --> B{Is n > digitInNum * end?};
    B -->|Yes| C[Update n, digitInNum, start, end];
    C --> B;
    B -->|No| D[Calculate the number containing nth digit];
    D --> E[Convert to string and return nth digit];
    E --> F[End];
🚀 Problem 2: Swapping Nodes in a Linked List
🔍 Problem Statement
Given the head of a singly linked list and an integer k, swap the k-th node from the beginning with the k-th node from the end.

✅ Approach
Traverse the linked list and store the nodes in a vector.

Swap the values of the k-th node from the beginning and the k-th node from the end.

Return the head of the modified list.

🧾 Code
cpp
Copy
Edit
class Solution {
public:
    ListNode* swapNodes(ListNode* head, int k) {
        vector<ListNode*> nodes;
        ListNode* current = head;

        while (current) {
            nodes.push_back(current);
            current = current->next;
        }

        int n = nodes.size();
        swap(nodes[k - 1]->val, nodes[n - k]->val);

        return head;
    }
};
📈 Time & Space Complexity
Time Complexity: O(n), where n is the length of the linked list. We traverse the entire list to store nodes.

Space Complexity: O(n), due to the storage of all nodes in the vector.

🧠 Insight
The approach uses a vector to store the nodes, which simplifies accessing the k-th nodes. However, this can be space-inefficient for large linked lists. An optimized approach would avoid extra space.

🔁 Flowchart (Mermaid)
mermaid
Copy
Edit
graph TD;
    A[Start] --> B[Traverse linked list and store nodes];
    B --> C[Swap k-th node from start with k-th node from end];
    C --> D[Return modified head];
    D --> F[End];
