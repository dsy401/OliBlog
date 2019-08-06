---
layout: post_layout
title: Linked List
date: 2019-06-04 23:56:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

Today, i wanna talk about the one of most important algorithm 'Linked List'. When we store a large amount of data, we often use arrays, but when we perform the insert operation, it is very troublesome. See the example below, there is a bunch of data 1, 2, 3, 5, 6, 7 - we are going to Insert between 3 and 5 as shown in Figure 4. If we use arrays, what do we do? Of course, the data after 5 is backed up by one, and then inserted as shown in Figure 4. This is very troublesome, but if I use a linked list, I will insert 4 directly between 3 and 5, which is very convenient.

So what is the structure of the linked list? As the name implies, the linked list is of course like a chain, connected by a node node to form a data link.

The structure of the linked list is that the head saves the address of the first node:

![](/assets/img/linked_list_img.png){: width="960" height="207"}

Further more, let's implement the linked list with Python.

Firstly, we need to define the node class:

```python
class Node:
    '''
    data: data in this node
    _next: the next node connecting to this node
    '''
    def __init__(self, data, pnext=None):
        self.data = data
        self._next = pnext

    def __repr__(self):
        '''
        define output: node data
        '''
        return str(self.data)
```
```python
def print_list(node):
    while node:
        print(node.data)
        node = node._next
        
def main():
    node1 = Node("car")
    node2 = Node("bus")
    node3 = Node("lorry")
    node1.next = node2
    node2.next = node3
    print_list(node1)

```
