---
title: "NodeJs: Loops, Closure and Async Invocation"
date: 2015-10-04T00:00:00+00:00
publishdate: 2015-10-04T00:00:00+00:00
lastmod: 2015-10-04T00:00:00+00:00
tags: ["NodeJS", "JavaScript"]
disableNextPrev: true
hidden: true
comments: true
draft: false
---

## Closure
Closure is something that is very familiar to all C# developers who know lambda expressions/functions but they just may not know that it is called Closure in JavaScript.  
Lets look at what is closure in JavaScript without further ado with an example:

```js
function outer(){
	var inOuter = "outer";
	inner();
	
	function inner(){
		console.log(inOuter); // prints 'outer'
	}
}
```

In this example, the variable `inOuter` is defined in the function `outer` but it is used in the function `inner`. This is possible because, the a function in JavaScript can access all the variables in the scope where the function is defined and this is called Closure.

## Loop and Closure
Lets consider the following example:

```js
function outer(){
	for(var i=1; i<=5; i++){
		inner();
	}
	
	function inner(){
		console.log(i); // prints 1, 2, 3, 4, 5
	}
}
```

Here the function `inner` is called from a loop and iterator variable is printed from inside the function `inner`. It prints, as you guessed, `1, 2, 3, 4, 5`.
This is because the function `inner` get the value of `i` whatever it is when the function `inner` is invoked.

## Loop, Closure and async invocation
Lets look at what happens if we invoke the function `inner` asynchronously

```js
function outer(){
	for(var i=1; i<=5; i++){
		process.nextTick(inner); // We can use setImmediate or setTimeout in browser environment to get similar effect
	}
	
	function inner(){
		console.log(i); // prints 6, 6, 6, 6, 6
	}
}
```

You may not expect it to print `6, 6, 6, 6, 6` but that's what it does. This is because the loop runs to completion in the current tick and the function `inner` is only invoked in some tick down the line.
So, the value of `i` will be `6` when function `inner` is executed and it prints `6`.

Now, what do you do if you want to print `1, 2, 3, 4, 5`  instead of `6, 6, 6, 6, 6`?  
Well, it turns out, you can do this simply by creating new function to create a new variable scope. This is because, in JavaScript variables are scoped to function instead of block.

>Note: Starting ES2015, you can use `let` instead of `var` to create block scope.

Here is the revised code:

```js
function outer(){
	for(var i=1; i<=5; i++){
		process.nextTick((function(){
			var j = i;
			return inner;		
	
			function inner(){
				console.log(j); // prints 1, 2, 3, 4, 5
			}
		})());
	}
}
```

We have created a new scope and assigned value of `i` to `j` which is defined in the new scope. We have also moved the function `inner` to the new scope.  
That's it, now it prints what we want it to print.