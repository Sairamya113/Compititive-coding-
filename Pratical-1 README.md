//partical -1 to implemention stack of min stack,push,pop,top, display operations.
#include <iostream>
#include <stack>
#include <climits> 

class MinStack {
private:
    std::stack<int> mainStack; 
    std::stack<int> minStack;  

public:
    void push(int x) {
        mainStack.push(x);
        if (minStack.empty() || x <= minStack.top()) {
            minStack.push(x);
        }
    }

    void pop() {
        if (mainStack.empty()) {
            std::cout << "Stack is empty!" << std::endl;
            return;
        }

        if (mainStack.top() == minStack.top()) {
            minStack.pop();
        }

        mainStack.pop();
    }
    int top() {
        if (mainStack.empty()) {
            std::cout << "Stack is empty!" << std::endl;
            return INT_MIN; 
        }
        return mainStack.top();
    }
    int peek() {
        return top();
    }

    int getMin() {
        if (minStack.empty()) {
            std::cout << "Stack is empty!" << std::endl;
            return INT_MIN;
        }
        return minStack.top();
    }
};

int main() {
    MinStack stack;

    stack.push(10);
    stack.push(20);
    stack.push(5);
    stack.push(30);

    std::cout << "Top element: " << stack.top() << std::endl;      
    std::cout << "Minimum element: " << stack.getMin() << std::endl; 

    stack.pop();
    std::cout << "Top element after pop: " << stack.top() << std::endl; 
    std::cout << "Minimum element after pop: " << stack.getMin() << std::endl; 

    stack.pop();
    std::cout << "Top element after pop: " << stack.top() << std::endl; 
    std::cout << "Minimum element after pop: " << stack.getMin() << std::endl; 

    return 0;
}
