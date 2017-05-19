Stacks and Queques: 
Stacks are almost like the pile of plates you see at a cafeteria, hence why they are named "stacks".
One might ask, "How does a data structure exactly behave just like a pile of plates?", well let's get into 
it and find out!

Stacks are ment to retain their order inside them, keeping the most recent additions at the top and the 
oldest at the bottom. 

The stack has two operations: 
	- push(data); which adds its data
	- pop(); removes the most recently added data 

For writing our first stack, we shall create a constructor named `Stack`. Each instance of Stack will have two 
properties: size and storage. 

	`function Stack() {
		this._size = 0; // initial size is kept to 0 and increments and decrements by 1 depending on the method
		this._storage = {}; // storage is an object that will hold the data into properties 
	}`

The next step is to make methods for pushing and poping the stored data either into or outof the stack. We shall put
this into the prototype since all instances of stack should have these same properties. 

	`Stack.prototype.push = function(data) {
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
	}`

Okay so let's consider a scenario where we first pop() and then push(data), wouldn't the size be equal to 0? Well shouldn't 
it be equal to 1?!
So lets impliment an if statement inside there to change that!
	
	`Stack.prototype.pop = function() {
		var size = this.size;
		var deletedData = this._storage[size];

        if (size) {
        	delete this._storage[size];
        	size--;
        	
        	return deletedData;
        }
	}`


