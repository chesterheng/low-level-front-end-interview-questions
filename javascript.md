
## Javscript questions

  

1.  [Explain how `this` works in Javascript](https://github.com/mirlz/low-level-front-end-interview-questions/blob/master/javascript.md/#explain-how-this-works-in-javascript)

2.  [Explain what is inheritance and how you use inheritance in code](https://github.com/mirlz/low-level-front-end-interview-questions/edit/master/javascript.md/#explain-what-is-inheritance-and-how-you-use-inheritance-in-code)

3.  [What's the difference between .call(), .apply() and .bind()](https://github.com/mirlz/low-level-front-end-interview-questions/blob/master/javascript.md/#whats-the-difference-between-call-apply-and-bind)

4. [Construct a function named Person, and contain the below in ES5:]((https://github.com/mirlz/low-level-front-end-interview-questions/blob/master/javascript.md/#construct-a-function-named-person-and-contain-the-below-in-es5)

5.  [What's the difference between the below:](https://github.com/mirlz/low-level-front-end-interview-questions/blob/master/javascript.md/whats-the-difference-between-the-below)

	1. 
			$('#parent-table .row').on('click', function () {

			})
	2.	
			$('#parent-table').on('click', '.row', function() {
				
			})

------

### 1. Explain how `this` works in Javascript

The overarching rule is that `this` is determined at the time a function is invoked by inspecting where it’s called, its _call site_. **It follows these rules, in order of precedence**.

1.  if `new` is used to initialize the function, `this` inside the function is a brand new object
    
	    function ConstructorExample() {  
		    console.log(this);  
		    this.value = 10;  
		    console.log(this);  
	    }
	    new ConstructorExample();  
	    // -> {} 
	    // -> { value: 10 }
    
2.  If `apply()`, `bind()`, or `call()` is used to call a function, `this` inside the function is the object that was passed into the function.
    
	    function fn() {  
		    console.log(this);  
	    } 
	    
	    var obj = {  
		    value: 5  
	    };
	    
	    var boundFn = fn.bind(obj);  
	    boundFn(); // -> { value: 5 }  
	    fn.call(obj); // -> { value: 5 }  
	    fn.apply(obj); // -> { value: 5 }
    
3.  If a function is called as a method — that is, if dot notation is used to invoke the function — `this` is the object that the function is a property of. (ƒ symbolizes function in the code blocks)
    
	    var obj = {  
		    value: 5,  
		    printThis: function() {  
			    console.log(this);  
		    }  
	    };  

		obj.printThis(); // -> { value: 5, printThis: ƒ }
    
4.  If a function is invoked as a _free function invocation_, meaning it was invoked without any of the conditions present above, `this` is the global object. In a browser, it’s `window`.
    
	    function fn() {  
		    console.log(this);  
	    }  
		
		// If called in browser:  
		fn(); // -> Window {stop: ƒ, open: ƒ, alert: ƒ, ...}
	    
5.  If multiple of the above rules exist, the rule that is higher wins and will determine the `this` value.
    
_Sources_

-   [Front-end Interview handbook (Yang Shun)](https://github.com/yangshun/front-end-interview-handbook/blob/master/questions/javascript-questions.md)
    
-   [Read more in-depth on CodeBurst.io](https://codeburst.io/the-simple-rules-to-this-in-javascript-35d97f31bde3)

### 2. Explain what is inheritance and how you use inheritance in code

Almost all objects in JavaScript have the _prototype_ property. By using it and more specifically the prototype chain we can mimic inheritance. The prototype is a reference to another object and it is used whenever JS can’t find the property you’re looking for on the current object. Simply put, whenever you call a property on an object and it doesn’t exist, JavaScript will go to the prototype object and look for it there. If it finds it it will use it, if not it will go to that object’s property and look there.

	function Animal(name) {  
		this.name = name;  
	}

	Animal.prototype.sleep = function() {  
		console.log(this.name + ': Zzz...');  
	}

	var dog = new Animal('dog');  
	dog.sleep(); // dog: Zzz

_Sources_

-   [https://hackernoon.com/understanding-javascript-prototype-and-inheritance-d55a9a23bde2](https://hackernoon.com/understanding-javascript-prototype-and-inheritance-d55a9a23bde2)

### 3. What's the difference between .call(), apply(), and bind()

-   _call()_ invokes the function and allows you to pass in arguments one by one.
    
-   _apply()_ invokes the function and allows you to pass in arguments as an array.
    
-   _bind()_ returns a new function, allowing you to pass in a this array and any number of arguments.
    

**Call**

	var person1 = {
		firstName: 'Jon', 
		lastName: 'Kuperman'
	};  
	var person2 = {
		firstName: 'Kelly', 
		lastName: 'King'
	};

	function say(greeting) { 
		console.log(greeting + ' ' + this.firstName + ' ' + this.lastName);  
	}

	say.call(person1, 'Hello'); // Hello Jon Kuperman  
	say.call(person2, 'Hello'); // Hello Kelly King

**Apply**

	var person1 = {
		firstName: 'Jon', 
		lastName: 'Kuperman'
	};  
	var person2 = {
		firstName: 'Kelly', 
		lastName: 'King'
	};

	function say(greeting) {  
		console.log(greeting + ' ' + this.firstName + ' ' + this.lastName);  
	}

	say.apply(person1, ['Hello']); // Hello Jon Kuperman  
	say.apply(person2, ['Hello']); // Hello Kelly King

**Bind**

	var person1 = {
		firstName: 'Jon', 
		lastName: 'Kuperman'
	};  
	var person2 = {
		firstName: 'Kelly', 
		lastName: 'King'
	};

	function say() {  
		console.log('Hello ' + this.firstName + ' ' + this.lastName);  
	}

	var sayHelloJon = say.bind(person1);  
	var sayHelloKelly = say.bind(person2);

	sayHelloJon(); // Hello Jon Kuperman  
	sayHelloKelly(); // Hello Kelly King

Call and apply are pretty interchangeable. Just decide whether it’s easier to send in an array or a comma separated list of arguments. Just remember that Call is for comma (separated list) and Apply is for Array.

Bind is a bit different. It returns a new function. Call and Apply execute the current function immediately.

_Sources_

-   [https://stackoverflow.com/questions/15455009/javascript-call-apply-vs-bind](https://stackoverflow.com/questions/15455009/javascript-call-apply-vs-bind)

### 4. Construct a function named Person, and contain the below in ES5:
-   Name - property
-   getName() - method

	    function Person() {  ​  
    		constructor(name) {  
    			this.name = name;  
    		}  
    		getName() { 
    			return console.log(this.name);  
    		}  
    	}

### 5. What's the difference between the below:

	

1. 
		$('#parent-table .row').on('click', function () {

		})
2.
		$('#parent-table').on('click', '.row', function() {
			
		})


Technically, both works the same actually. Just that there's a huge difference in terms of performance and code efficiency.

For (1), depending on how many rows there are in the table, it will take a lot of time to go through this command, especially if there is a few thousand rows of data. However for (2), user click on the table first, then the system would check for the specific row. (1) gives back thousands of data, whereas the (2) gives back only 1 big structure. So (2) is the better option.
