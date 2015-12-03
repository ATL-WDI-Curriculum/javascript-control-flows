# JS Control Flow
## Cond, Loop, Iterator, and all that

| Objectives |
| :---- |
| 	Identify and discuss boolean operators and truthyness |
| 	Apply different boolean operators with objects in conditional statements |
|	Discuss and apply loops and iterators using conditional statements |


## Agenda

* Javascript Control Flow
  * Logical Operators
  	* `&&`, `||`, and `!`
  	* comparisons
  	* truthy and falsey 	
  * Conditionals (if/else)
  	* short circuit 
  	* Ternary operator
  * For iterator
  	* What is iterating? Compute with for loops: factorial, repeating 50 times.
  	* `for` 
  	* `for ... in`
  * While loop
  	* generic condition
  * Switch case
  * Operator precidence
  
## What is Control Flow?

[Funny Flow Chart](https://www.laserfiche.com/content/uploads/2014/03/engineering-flow-chart.png)

Control Flow is a fundamental concept in programming that allows you to dictate how your code runs under different conditions or until a certain condition is met.  
 



## Logical Operators

There are two types of binary operators that work with booleans, (a binary operator just requires two arguments.)

* **AND**, denoted `&&` 
* **OR**, denoted `||`


There is a third unary operatory, (a unary operator that requires just one argument).

* **NOT**, denoted `!`

[MDN Logical Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)

Quick Notes:

* The `&&` operator requires both left and right values to be `true` to return `true`, i.e.
	
	````js
	true && true //=> true
	````
and any other combination is false.

* The `||` operator requires just one of the left or right values to be `true` to return true.
	* Only `false || false` will return `false`

* Which one is faster?
	
* The `!` takes a value and returns the opposite boolean value, i.e. ` !(true) //=> false`.



## Comparisons

To compare two values in Javascript for equality testing we use `===`, which will check the sameness of the thing on the left with the thing on the right. Note sameness is a very fuzzy word, and thus, `===` is also very fuzzy concept, which should be approached with caution in every language. 

Here are some cases when equality testing seems reasonable

```javascript	
	true === true 
	//=> true
	false === true
	//=> false
	
	1 === 1
	//=> true
	1 === 2
	//=> false
	
	"hello" === "hello"
	//=> true	
```


But here are some cases when it does not. 


```javascript	
	{} === {}
	//=> false
	[] === []
	//=> false	
```


**Explanation**

The second set of examples fail because both **object literals** and **arrays** are objects, and not just values like strings, numbers, and booleans. Objects can be complex collections of values in memory that we  are referring to in a program, and so, we only reference each object by an id to simply things. However, that means when we go to compare the two objects we don't care if they look like similar collections. We only compare their respective ids when checking for equality, and each `{}` or `[]` represents a new object with it's own unique id.

Arrays and objects are called **reference** types for the above reasons, so be careful with using them too intuitively.


### Truthy

In a language some values can be taken to be `true` or `false`, and we can check this using the `!` operator

```javascript

	!!(1)
	//=> true
	
	!!(0)
	//=> false
	
	!!(-1)
	//=> true
	
	!!([])
	//=> true
	
	!!({})
	//=> true
	
	!!(null)
	//=> false
	
	!!('')
	//=> false
```

The following values are always falsy:

- false
- 0 (zero)
- "" (empty string)
- null
- undefined
- NaN (a special Number value meaning Not-a-Number!)


## Conditionals

Conditionals are a way of essentially skipping over a block of code if it does not pass boolean expression.


* `if(expr) { code }`, run code block if `expr` is `true`

```javascript
var num = 22;

if (num % 2  === 0) {
	console.log("is even");
}
```

* `if (expr) { ... } else { ... }`
	*  you can specifiy the `else` block to run if `expr` is `false`
* `if (expr1) { ... } else if (expr2) { ... } ... else { ... }`
	*  if `expr1` is false then each `else if` expression will be evaluated until one is `true`, and an `else` will be run otherwise.
	


```javascript
var expr1 = true;
var expr2 = true;


if (expr1) {
	console.log("expr1 is true!");
} else if (expr2) {
	console.log("expr2 is true!");
}

```


The above example will print `"expr1 is true"` and the `else if` is never reached. If `expr1` is `false` it would only print `"expr2 is true"`


###YOU DO:
Goto [repl.it](https://www.repl.it/) to complete the following exercise...

Write a script that prompts the user for their current mood. If the user inputs `happy`, print 'Yay me too!' to the console, `sad` print 'Aw cheer up', else just print 'So moody!'. (A solution is at the bottom of this lesson:)



----
### Exercises


#### Warming up

1. Use conditionals to check if a hardcoded number is `odd` or `even`, and then `console.log` the number is `odd` or `even` with the numbers value.

	```js
	var num = ;// write a number here
	
	// write your conditions here
	
	```

2. Use conditionals to check if a hardcoded number is divisible by `2` or  `3` and then `console.log` that the number is divisible by two or three.

	```js
	var num = ;// write a number here
	
	// write your conditions here
	
	```

3. Use conditionals to check if a hardcoded `quantity` is `1` or greater than one. If the `quantity`  is one or greater `console.log` either `1 pet` or `quantity + " pets"` respectively.

	```js
	var quantity = ;// write a number here
	
	// write your conditions here
	
	```

#### Ternary Operators

Another way to write a very shorthand conditional is using a **ternary operator**, `expr1 ? expr2 : expr3 `. 

```js
true ? console.log("it is true"): console.log("it is false");
//=>  "it is true"
false ? console.log("it is true"): console.log("it is false");
//=> "it is false"
```

### Iterating

It is a way of incrementally repeating a task. Iterating is a way of describing procedures like 

```js
print "hello world" 50 times
``` 
It is also a way of describing 

```js
print each item in a shopping list
```

It can also be a way of solving problems like

```js
how would I print all vegetables in a shoppping list?
```


Typically iteration has three or four main parts 

* an initial state
* a condition for repeating
* process to be run for each repetition 
* a state change for proceeding to the next step

It isn't surprising that the primary means of iterating in most languages is called a `for` loop, which has the following structure

```js
for ( intial state; check condition; change state) {
	run this code for before changing state
}
```


or a  more concrete example


```js
var friends = ["larry", "moe", "curly"];

for (var index = 0; index < friends.length; index = index + 1) {
	console.log(friends[index])
}
```

#### Exercises


1) Iterate through a shopping list and print each item in a shopping list.

```js
	var shoppingList = ["apples", "oranges", "carrots"];
		
	// iterate here
```

2) Iterate through a list of shopping lists and print each item in each list.

```js
	var shoppingLists = [
							["apples", "oranges", "carrots"],
							["ham", "turkey", "cheese"],
							["fruits", "vegetables", "meat"]
						];
	// iterate here
```


3) Word counting:
	
- a. Count the number of space separated words in the string below (Hint: do this with and without a `for` loop.).
- b. Count the number of words that in a string that have the letter `a` in them.

```js
var shakespeare = "Our doubts are traitors, and make us lose the good we oft might win, by fearing to attempt."

```


4) Capitalize the first letter in every word in a string, i.e
	
```js
"hello world" => "Hello World"	
```

5) Find the largest and smallest number in the array below.

```js
	var numbers = [56, 74, 31, 89, 8, 
					22, 5, 19, 28, 100,
					82, 72, 39, 25, 90, 
					1, 97, 83, 58, 38, 
					57, 71, 70, 7, 3, 
					12, 48, 45, 43, 84, 
					68, 49, 37, 41, 92, 
					96, 6, 66, 95, 15, 
					67, 2, 59, 4, 91, 
					44, 50, 17, 30, 88, 
					34, 55, 64, 9, 27, 
					73, 60, 32, 81, 10, 
					53, 61, 63, 51, 65, 
					36, 26, 99, 76, 47, 
					21, 14, 16, 40, 79, 
					75, 85, 42, 86, 18, 
					23, 24, 46, 69, 29, 
					77, 20, 54, 80, 87, 
					13, 94, 98, 93, 62, 
					35, 33, 11, 52];			
```

6) You have a list of numbers in the `numbers` array above somehow got shuffled and one is missing. Luckily you know that the numbers were from `1 to 100`. Find the missing number. 

7) Find the `sum` of the values in an array and the `average` in the `numbers` array above. 

8) Find the average of only the odd numbers the `numbers` array above.

9) Write a loop that creates an array of `100` random integers (not decimal numbers).

10) Find the numbers in common in two different lists of numbers.

## While loops

The while loop is the other type of repetitive control flow structure. However, `for` handled most of the general iteration tasks we could hope to perform. You should hardly ever need just a `while` loop. It will run so long as a condition is true.


```js
while (true) {}
```

This should be enough to break a browser.

In the browser try the [`prompt`](https://developer.mozilla.org/en-US/docs/Web/API/Window.prompt) function out. 


#### Exercises 

1. Re-write exercise `1` for `for` loops using a `while` loop.
2. Use `prompt` and the `while` loop to create an array of `5` names.
3. Use [`confirm`](https://developer.mozilla.org/en-US/docs/Web/API/Window.confirm) to check if a user wants to continue looping. If `yes` print `hello`, and if anything else print `goodbye` and `stop` looping.
4. Implement a guessing game using `prompt` and `while`.


## For ... In


A `for... in` loop is a way to iterate through an object. Go to [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) and read about how to use it. 

#### Exercise

1. Come up with a use case for the `for ... in` loop and share it with your neighbor. 

##Infinite Loops

- While writing a loop it is possible to create a loop that will go until infinity.
- Obviously we try to avoid this while coding.

```js
for (var i = 0; i > 0; i++) {
  console.log(i);
}
```

## Switch Statement

This is how it works:

- The switch expression is evaluated once.
- The value of the expression is compared with the values of each case.
- If there is a match, the associated block of code is executed.

####Example
The `getDay()` method returns the weekday as a number between 0 and 6. (Sunday=0, Monday=1, Tuesday=2 ..)

Use the weekday number to calculate weekday name:

```js
switch (new Date().getDay()) {
    case 0:
        day = "Sunday";
        break;
    case 1:
        day = "Monday";
        break;
    case 2:
        day = "Tuesday";
        break;
    case 3:
        day = "Wednesday";
        break;
    case 4:
        day = "Thursday";
        break;
    case 5:
        day = "Friday";
        break;
    case 6:
        day = "Saturday";
        break;
}

```

- When the JavaScript code interpreter reaches a break keyword, it breaks out of the switch block.
- This will stop the execution of more code and case testing inside the block.
- When a match is found, and the job is done, it's time for a break.
There is no need for more testing.

#####What is faster switch or if/else?

Note that for the if-else structure, the variable being checked is reloaded into a register for comparison every single time. The switch-case structure loads the variable one time, and proceeds to perform the series of comparisons. 

Use if instead of switch when:

- You want to test for the truthiness of an expression.
- You only have a single affirmative test.


##Solution to the `moody` you do exercise

```js
var mood = prompt("What is your mood?");

if (mood == 'sad') {
    console.log('hrmph');
} else if (mood == 'happy') {
    console.log('YOWZA!');
} else {
    console.log('not impressed');
}
```