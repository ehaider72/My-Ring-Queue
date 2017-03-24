# My-Ring-Queue

Emily Haider 
Pic 10C 
Assig. 3: Ring Queue

GOAL: Write a home-made iterator that doesn't involve delegation (via ring-queue).

Some further info...

Just like a regular queue, elements can be pushed [on the back of the queue] and popped [off the front]. However, unlike a regular queue:

    A ring queue keeps only the N most recently pushed elements.
    push_back()and pop_front() are used instead of push() and pop() to support using generic algorithms and back_inserter.
    push_front() on a full ring queue adds the new element and removes the oldest (i.e., the one at the front).
    Iterator access to the queue is supported with begin() and end().


A common way to implement ring queues is as a simple array with two numbers:

    buffer: the array with capacity for N elements (ring capacity), 
    begin_index: an integer that indicates where in the buffer the first element of the ring queue is located, and
    ring_size: an integer that indicates the number of meaningful elements in the ring queue.

When the ring queue is created, begin_index is set to 0. The end of the ring queue is calculate as needed via the formula:

end_index=(begin_index+ring_size)%ring_capacity.

Assuming ring_size is not zero, we can then define the accessor member functions front(), back(), that return buffer[begin_index], and buffer[end_index], respectively.


The rules for changing begin_index and ring_size (and hence end_index) are given by:

    pop_front() increments begin_index and decrements ring_size.
    push_back() stores the value in buffer[end_index] and increments ring_size up to the capacity of the ring queue. After capacity is reached, the value is stored in the same place, but  begin_index is increased.
    Whenever begin_index reaches the capacity of the ring, it is reset back to 0. On the other hand, ring_size is never incremented past the capacity of the ring, nor decremented below 0.
