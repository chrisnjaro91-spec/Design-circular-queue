#include <bits/stdc++.h>
using namespace std;
class MyCircularQueue {
private:
    vector<int> q;
    int size, front, rear, count;
public:
    MyCircularQueue(int k) {
        q.resize(k);
        size = k;
        front = 0;
        rear = -1;
        count = 0;
    }
    bool enQueue(int value) {
        if (isFull()) return false;
        rear = (rear + 1) % size;
        q[rear] = value;
        count++;
        return true;
    }
    bool deQueue() {
        if (isEmpty()) return false;
        front = (front + 1) % size;
        count--;
        return true;
    }
    int Front() {
        return isEmpty() ? -1 : q[front];
    }
    int Rear() {
        return isEmpty() ? -1 : q[rear];
    }
    bool isEmpty() {
        return count == 0;
    }
    bool isFull() {
        return count == size;
    }
};
