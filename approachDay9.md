
💡 C++ Code Explanation with Diagrams
🚀 Problem 1: Nth Digit
🔍 Problem Statement
You are given an integer n. Return the n-th digit of the infinite integer sequence: 1234567891011121314...

✅ Approach

Start by identifying the length of the digit group the n-th digit belongs to.

Use a loop to subtract the count of digits in 1-digit, 2-digit, 3-digit numbers, etc., from n until we find the correct group.

Calculate the actual number in which the digit lies.

Convert that number to a string and fetch the required digit.

🧾 Code

cpp
Copy
Edit
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
Time Complexity: O(log₁₀n)
Space Complexity: O(log₁₀n) (due to number-to-string conversion)

🧠 Insight
This approach calculates the digit without generating the entire sequence. It’s a smart trick of skipping large chunks and narrowing down.

🔁 Flowchart (Mermaid)

mermaid
Copy
Edit
flowchart TD
    A[Start with n] --> B{n > digits in current group?}
    B -- Yes --> C[Subtract digits, increase digit length]
    C --> B
    B -- No --> D[Find number = start + (n-1)/digitLength]
    D --> E[Convert number to string]
    E --> F[Return (n-1) % digitLength char as int]
🚀 Problem 2: Swapping Nodes in a Linked List
🔍 Problem Statement
You are given the head of a linked list and an integer k. Swap the values of the k-th node from the beginning and the k-th node from the end.

✅ Approach

Traverse the list and store node pointers in a vector.

Access the k-th node and (n-k+1)-th node from the vector.

Swap their values.

Return the head.

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
Time Complexity: O(n)
Space Complexity: O(n) (due to the extra vector for storing nodes)

🧠 Insight
While this approach is simple and easy to implement, a more optimized solution can achieve the same in O(1) space using two pointers.

🔁 Flowchart (Mermaid)

mermaid
Copy
Edit
flowchart TD
    A[Start] --> B[Traverse and store all nodes in vector]
    B --> C[Identify k-th and (n-k+1)-th nodes]
    C --> D[Swap their values]
    D --> E[Return modified head]
