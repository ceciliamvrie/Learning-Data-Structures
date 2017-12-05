# Stacks and Queues

### Introduction
Stacks are almost like the pile of plates you see at a cafeteria, hence why they are named "stacks".
One might ask, "How does a data structure exactly behave just like a pile of plates?", well let's get into 
it and find out!

Stacks are ment to retain their order inside them, keeping the most recent additions at the top and the 
oldest at the bottom. 

### Making Methods
The stack has two operations: 
- **push(data)** which adds its data
- **pop()** which removes the most recently added data 

For writing our *first* stack, we shall create a constructor named `Stack`. Each instance of Stack will have two 
properties: size and storage. 

	function Stack() {
		this._size = 0; // initial size is kept to 0 and increments and decrements by 1 depending on the method
		this._storage = {}; // storage is an object that will hold the data into properties 
	}

The next step is to make methods for pushing and poping the stored data either into or out of the stack. We shall put
this into the prototype since all instances of stack should have these same properties. 

	Stack.prototype.push = function(data) {
		// increases the size of your storage
		var size = this._size++;

		// assigns the size as the key of storage
		// assigns the data as the value of this key
		this._storage[size] = data; 
	}

	Stack.prototype.pop = function() {
		// delcare var size to be size of storage
		var size = this.size;

		var deletedData = this._storage[size];

		// removes the most recent key of data
        	delete this._storage[size];
       		// now decrement the size by one;
        	size--;

        	return deletedData;
	}
### Any Revisions?
Okay so let's consider a scenario where we first pop() and then push(data), wouldn't the size be equal to 0? Well shouldn't 
it be equal to 1?!
So lets impliment an if statement inside there to change that!
	
	Stack.prototype.pop = function() {
		var size = this.size;
		var deletedData = this._storage[size];

        	if (size) {
        		delete this._storage[size];
        		size--;
        	
        		return deletedData;
        }
	}
## What is a Queue?
You can think of a queue as a line of people -the last ones in are the last ones out. Unlike a stack, a queue is constantly putting things in on one end and spitting things out on the other. To ingest something, you **enqueue** it; to spit something  out, you **dequeue** it.

So let's consider building our first queue: 
    Since we know that a queue is the same thing as a line, we need to start figuring out a way to enqueue things at the 'end' of the queue.
    
    `// First we consider how the queue will store its things	
       function Queue() {
         this.storage = [];
	 this.head = 0;
	 this.tail = 0;
       }
       
       Queue.prototype.enqueue = function(data) {
         var tail = this.tail;
         this.storage[tail++] = data; // the data will get enqueued at the end of the line
       }
       
       Queue.prototype.dequeue = function() {
         if (this.tail <= this.head) {
           return 
         }
	 var dequeued = this.storage[this.head]
	 this.storage.shift()
	 this.head++
	 
	 return dequeued
       }
    `
    
    
