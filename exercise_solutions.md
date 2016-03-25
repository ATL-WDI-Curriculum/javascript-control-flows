#### Exercises


1) Iterate through a shopping list and print each item in a shopping list.

```js
var shoppingList = ["apples", "oranges", "carrots"];
	
// iterate here

for(i = 0; i < shoppingLists.length; i++){
    console.log(shoppingLists[i]);
}
```

2) Iterate through a list of shopping lists and print each item in each list.

```js
var shoppingLists = [
						["apples", "oranges", "carrots"],
						["ham", "turkey", "cheese"],
						["fruits", "vegetables", "meat"]
					];
// iterate here
	
for(i = 0; i < shoppingLists.length; i++){
    for(j = 0; j < shoppingLists[i].length; j++){
        console.log(shoppingLists[i][j]);
    }
}	
```


3) Word counting:

```js
var shakespeare = "Our doubts are traitors, and make us lose the good we oft might win, by fearing to attempt."
```
	
- a. Count the number of space separated words in the string above (Hint: do this with and without a `for` loop.).

```js
shakespeare.split(" ").length
```

- b. Count the number of words that in a string that have the letter `a` in them.

```js
var splitArray = shakespeare.split(" ");

counter = 0;

for (i = 0; i < splitArray.length; i++){
	if(splitArray[i].includes("a")){
		counter++;
	}
}
```


4) Capitalize the first letter in every word in a string, i.e
	
```js
"hello world" => "Hello World"	
```
```js
var word = "hello world"

var splitStr = word.split(' ');

for (var i = 0; i < splitStr.length; i++) {
    splitStr[i] = splitStr[i].charAt(0).toUpperCase() + splitStr[i].substring(1);     
}
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

```js
Math.min.apply(Math, numbers);
Math.max.apply(Math, numbers);
```

6) You have a list of numbers in the `numbers` array above somehow got shuffled and one is missing. Luckily you know that the numbers were from `1 to 100`. Find the missing number. 

```js
for (i = 0; i < 100; i++){
	if (numbers.includes(i) === false) {
		console.log(i);
	}
}
```

7) Find the `sum` of the values in an array and the `average` in the `numbers` array above. 

```js
var sum = numbers.reduce((a, b) => a + b, 0);

var average = sum/numbers.length
console.log("The sum of the numbers is: " + sum + "  and the average is: " + average);
```

8) Find the average of only the odd numbers the `numbers` array above.

```js
for (i = 0; i < numbers.length; i++){
	if (i % 2 !== 0){
		sum += i;
	}
}

console.log("The sum of the odds is: " + sum);
```

9) Write a loop that creates an array of `100` random integers (not decimal numbers).

```js
var randomArray = [];

for (i = 0; i < 100; i++) {
	randomArray.push(Math.floor((Math.random() * 100)));
}

console.log(randomArray);
```

10) Find the numbers in common in two different lists of numbers.

```js
var numbers1 = [1, 2, 3, 4, 5, 6]
var numbers2 = [2, 3, 4]
var matches = [];

for (i = 0 ;i < numbers1.length; i++) {
    if (numbers2.indexOf(numbers1[i]) != -1)
        matches.push(numbers1[i]);
}

console.log(matches);
```