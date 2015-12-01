---
layout: post
title:  "C++とPythonでのアルゴリズムコードのメモ"
date:   2015-12-01 22:00:00
categories: algorithm
---

競技プログラミングや練習問題むけに。

## stack, queue

### C++
std::stack, std::queueを使う
{% highlight c++ %}
#include <stack>
#include <queue>
#include <iostream>
int main() {
  std::stack<int> stack;
  stack.push(0);
  stack.push(1);
  std::cout << stack.top() <<std::endl; // 1
  stack.pop();
  std::cout << stack.top() <<std::endl; // 0
  stack.pop();

  std::queue<int> queue;
  queue.push(0);
  queue.push(1);
  std::cout << queue.front() <<std::endl; // 0
  queue.pop();
  std::cout << queue.front() <<std::endl; // 1
  queue.pop();
}
{% endhighlight %}

### Python
listをstack, queueとして使える。
{% highlight python %}
stack = []
stack.append(1)
stack.append(2)
print(stack.pop()) # 2
print(stack.pop()) # 1

queue = []
queue.append(1)
queue.append(2)
print(queue.pop(0)) # 1
print(queue.pop(0)) # 2
{% endhighlight %}

## priority queue

### C++
{% highlight c++ %}
#include <vector>
#include <queue>
#include <functional>
#include <iostream>
int main() {
  std::priority_queue<int> max_heap; // by default max heap
  max_heap.push(1);
  max_heap.push(0);
  std::cout << max_heap.top() <<std::endl; // 1
  max_heap.pop();
  std::cout << max_heap.top() <<std::endl; // 0
  max_heap.pop();

  std::priority_queue<int, std::vector<int>, std::greater<int>> min_heap;
  min_heap.push(1);
  min_heap.push(0);
  std::cout << min_heap.top() <<std::endl; // 0
  min_heap.pop();
  std::cout << min_heap.top() <<std::endl; // 1
  min_heap.pop();
}
{% endhighlight %}

### Python
{% highlight python %}
import heapq

pq = [2, 0, 1]
heapq.heapify(pq) # Create min heap. Note that this is O(n).
print(heapq.heappop(pq)) # 0
print(heapq.heappop(pq)) # 1
heapq.heappush(pq, 3)
heapq.heappush(pq, 0)
print(heapq.heappop(pq)) # 0
print(heapq.heappop(pq)) # 2
print(heapq.heappop(pq)) # 3
{% endhighlight %}