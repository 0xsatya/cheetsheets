## Javascript Docs

- [Javascript questions lydiahallie](https://github.com/lydiahallie/javascript-questions)

## Javascript Cheetsheet

```
 Learning methods-
----------------------------------------------------------------------
Javascript primitives - 6 types
	1-number
	2-string
	3-boolean
	4-null
	5-undefined
	6-symbol

-	every thing else is object.
-	javascript points to above 6 primitive types.
-	all javascript objects are new.

6 DATATYPES considered as FALSE
	-	0
	-	false
	-	null
	-	NaN
	-	undefined
	-	""
-----------------------------------------------------------------------

var x = 140; 	// can be redeclared, reassigned
const x = 140; 	// can't redecalred, reassigned or used before declaration
let x = 140;	// can't redeclared, but reassigned.


-----------------------------------------------------------------------
###################### ARRAYS ###############################
-----------------------------------------------------------------------
var cars = ["Mercedes", "Tesla","Volvo"];

pop(): 		 removing the last element of an array.
push(): 	  adding a new element at the very end of an array.
concat(): 	 joining various arrays into a single array.
reverse(): 	 reversing the order of the elements in an array.
shift(): 	 removing the first element of an array.
slice(): 	 pulling a copy of a part of an array into a new array.
splice(): 	 adding elements in a particular way and position.
toString():  converting the array elements into strings.
unshift(): 	 adding new elements at the beginning of the array.
valueOf(): 	 returning the primitive value of the given object.
indexOf(): 	 This method returns the first index at which a given element is found in an array.
lastIndexOf(): This method returns the final index at which a given element appears in an array.
join(): 	 combining elements of an array into one single string and then returning it.
sort(): 	 sorting the array elements based on some condition.

uses
-------
Arrays≡
var dogs = ["Bulldog", "Beagle", "Labrador"];
var dogs = new Array("Bulldog", "Beagle", "Labrador");  // declaration

alert(dogs[1]);             // access value at index, first item being [0]
dogs[0] = "Bull Terier";    // change the first item

for (var i = 0; i < dogs.length; i++) {     // parsing with array.length
	console.log(dogs[i]);
}

Methods
-------------
dogs.toString();                        // convert to string: results "Bulldog,Beagle,Labrador"
dogs.join(" * ");                       // join: "Bulldog * Beagle * Labrador"
dogs.pop();                             // remove last element
dogs.push("Chihuahua");                 // add new element to the end
dogs[dogs.length] = "Chihuahua";        // the same as push
dogs.shift();                           // remove first element
dogs.unshift("Chihuahua");              // add new element to the beginning
delete dogs[0];                         // change element to undefined (not recommended)
dogs.splice(2, 0, "Pug", "Boxer");      // add elements (where, how many to remove, element list)
var animals = dogs.concat(cats,birds);  // join two arrays (dogs followed by cats and birds)
dogs.slice(1,4);                        // elements from [1] to [4-1]
dogs.sort();                            // sort string alphabetically
dogs.reverse();                         // sort string in descending order
x.sort(function(a, b){return a - b});   // numeric sort
x.sort(function(a, b){return b - a});   // numeric descending sort
highest = x[0];                         // first item in sorted array is the lowest (or highest) value
x.sort(function(a, b){return 0.5 - Math.random()});     // random order sort

-----------------------------------------------------------------------
###################### STRINGS ###############################
-----------------------------------------------------------------------

toLowerCase() —  	converting strings to lower case
toUpperCase() —  	converting strings to upper case
charAt() —  		returning the character at a particular index of a string
charCodeAt() —  	returning to us the Unicode of the character at a  given index
fromCharCode() —  	returning a string made from a particular sequence of UTF-16 code units
concat() —  		concatenating or joining multiple strings into a single string
match() —  			retrieving the matches of a string against a pattern string which is provided
replace() —  		finding and replacing a given text in the string
indexOf() —  		providing the index of the first appearance of a given text inside the string
lastIndexOf() — 	it searches for the last occurrence of the character and searches backwards
search() —  		executing a search for a matching text and returning the index of the searched string
substr() —  		a substring in it depends on a given number of characters
slice() —  			extracting an area of the string and returning it
split() —  			splitting a string object into an array of strings at a particular index
substring() — 		it does not allow negative positions
valueOf() —  		returning the primitive value (one without any properties or methods) of a string object


-----------------------------------------------------------------------
###################### DATES OBJECTS ###############################
-----------------------------------------------------------------------

JavaScript Date Objects

Setting Dates: Dates can be set using the following three ways:
------------------------
Date() 		— Returns a new date object that contains the current date and time.

Date(1993, 6, 19, 5, 12, 50, 32) 	— We can create a custom date object with the pattern as Year, month, day, hour, minutes, seconds, and milliseconds are represented by the numbers. Except for the year and month, we can omit anything we like.

Date("1999-12-22") 	— Date as a string declaration

Getting the values of Time and Date: The following methods can be used for getting the date and time values in JavaScript:
------------------------
getDate() 		returns the month's day as a number (1-31)
getTime() 		— Get the milliseconds since January 1, 1970
getUTCDate() 	returns the month's day (day) in the supplied date in universal time (also available for day, month, full year, hours, minutes etc.)
getMilliseconds() 	— This function returns the milliseconds (0-999)
getMinutes() 		— Returns the current minute (0-59)
getMonth() 			returns the current month as a number (0-11)
parse 				—  It returns the number of milliseconds since January 1, 1970 from a string representation of a date.
getDay() 			returns a number representing the weekday (0-6)
getFullYear() 		returns the current year as a four-digit value (yyyy)
getHours() 			— Returns the current hour (0-23)
getSeconds() 		— Returns the second number (0-59)

Setting a Part of the Dates: We can set a part of the dates in JavaScript using the following methods:
------------------------
setDate() 		— Returns the current date as a number (1-31)
setFullYear() 	— This function sets the year (optionally month and day)
setMonth() 		— This function sets the month (0-11)
setSeconds() 	— This function sets the seconds (0-59)
setTime() 		— This function is used to set the time (milliseconds since January 1, 1970)
setMinutes() 	— This function sets the minutes (0-59)
setUTCDate() 	— According to universal time, sets the day of the month for a given date (also available for day, month, full-year, hours, minutes etc.)
setHours() 			— Changes the time (0-23)
setMilliseconds() 	— This function sets the milliseconds (0-999)


-----------------------------------------------------------------------
#################### Numbers and Mathematics  #########################
-----------------------------------------------------------------------

Numbers Properties:
------------------------
MAX VALUE 			— The maximum numeric value that JavaScript can represent.
NaN 				— The "Not-a-Number" value is NaN.
NEGATIVE INFINITY 	– The value of Infinity is negative.
POSITIVE INFINITY 	– Infinity value that is positive.
MIN VALUE 			— The smallest positive numeric value that JavaScript can represent.

Numbers Methods:
--------------------------
toString() 			— Returns a string representation of an integer.
toFixed() 			— Returns a number's string with a specified number of decimals.
toPrecision() 		— Converts a number to a string of a specified length.
valueOf() 			— Returns a number in its original form.
toExponential() 	— Returns a rounded number written in exponential notation as a string.


Maths Properties:
---------------------------
E 			— Euler's number is E.
SQRT1_2 	— 1/2 square root
SQRT2 		stands for square root of two.
LOG2E 		— E's base 2 logarithm
LN2 		— The natural logarithm of 2 is LN2.
LN10 		— The natural logarithm of ten is LN10.
LOG10E 		— E's base ten logarithm
PI 			— PI stands for Pianistic Integer.

Maths Methods:
----------------------------
exp(x) 			— Ex's value
floor(x) 		— x's value rounded to the nearest integer.
log(x) 			— The natural logarithm (base E) of x is log(x).
abs(x) 			— Returns the value of x in its absolute (positive) form.
acos(x) 		— In radians, the arccosine of x.
asin(x) 		— In radians, the arcsine of x.
pow(x,y) 		— x to the power of y
random() 		— Returns a number between 0 and 1 at random.
round(x) 		— Rounds the value of x to the nearest integer.
sin(x) 			— The sine of x is sin(x) (x is in radians)
sqrt(x) 		— x's square root
tan(x) 			— The angle's tangent
atan(x) 		- is the numeric value of the arctangent of x.
atan2(y,x) 		— Arctangent of its arguments' quotient
ceil(x) 		— x's value rounded to the next integer
cos(x) 			– The cosine of x is cos(x) (x is in radians)
max(x,y,z,...,n) 	— Returns the highest-valued number.
min(x,y,z,...,n) 	— The number with the lowest value is the same as the number with the highest value.

EXAMPLES
------------------
Numbers and Math∑
------------------
var pi = 3.141;
pi.toFixed(0);          // returns 3
pi.toFixed(2);          // returns 3.14 - for working with money
pi.toPrecision(2)       // returns 3.1
pi.valueOf();           // returns number
Number(true);           // converts to number
Number(new Date())      // number of milliseconds since 1970
parseInt("3 months");   // returns the first number: 3
parseFloat("3.5 days"); // returns 3.5
Number.MAX_VALUE        // largest possible JS number
Number.MIN_VALUE        	// smallest possible JS number
Number.NEGATIVE_INFINITY	// -Infinity
Number.POSITIVE_INFINITY	// Infinity

var pi = Math.PI;       // 3.141592653589793
Math.round(4.4);        // = 4 - rounded
Math.round(4.5);        // = 5
Math.pow(2,8);          // = 256 - 2 to the power of 8
Math.sqrt(49);          // = 7 - square root
Math.abs(-3.14);        // = 3.14 - absolute, positive value
Math.ceil(3.14);        // = 4 - rounded up
Math.floor(3.99);       // = 3 - rounded down
Math.sin(0);            // = 0 - sine
Math.cos(Math.PI);      // OTHERS: tan,atan,asin,acos,
Math.min(0, 3, -2, 2);  // = -2 - the lowest value
Math.max(0, 3, -2, 2);  // = 3 - the highest value
Math.log(1);            // = 0 natural logarithm
Math.exp(1);            // = 2.7182pow(E,x)
Math.random();          // random number between 0 and 1
Math.floor(Math.random() * 5) + 1;  // random integer, from 1 to 5

Constants like Math.PI: +56962781548
--------------------------
E, PI, SQRT2, SQRT1_2, LN2, LN10, LOG2E, Log10E

-----------------------------------------------------------------------
###################### FUNCTIONS ###############################
-----------------------------------------------------------------------

Functions For Throwing Data As Output:
------------------------------------------
prompt(): 		creating a dialogue box for taking input from the user.
alert(): 		outputting information in an alert box in the browser window
console.log():  writing data to the browser's console and is used for the purpose of debugging code by developers.
document.write(): 	This function is used for writing straight to our HTML document
confirm(): 		opening up a yes or no dialogue box and for returning a boolean value depending upon the user's click

Global Functions:
---------------------------
parseFloat(): 		parsing the argument passed to it and returning a floating-point number.
parseInt(): 		parsing the argument passed to it and returning an integral number.
encodeURI(): 		encoding a URI into a UTF-8 encoding scheme.
decodeURI(): 		decoding a (URI) made by encodeURI() function or similar functions.
encodeURIComponent(): the same purpose as encodeURI() only for URI components.
decodeURIComponent(): decoding a URI component.
isNaN(): 	determining if a given value is Not a Number or not.
Number(): 	returning a number converted from what is passed as an argument to it.
eval(): 	evaluating JavaScript programs presented as strings.
isFinite(): determining if a passed value is finite or not.

-----------------------------------------------------------------------
###################### conditions and switch ##########################
-----------------------------------------------------------------------
If - Else
---------------
if ((age >= 14) && (age < 19)) {        // logical condition
	status = "Eligible.";               // executed if condition is true
} else {                                // else block is optional
	status = "Not eligible.";           // executed if condition is false
}

Switch Statement
------------------
switch (new Date().getDay()) {      // input is current day
case 6:                         // if (day == 6)
	text = "Saturday";
	break;
case 0:                         // if (day == 0)
	text = "Sunday";
	break;
default:                        // else...
	text = "Whatever";
}


-----------------------------------------------------------------------
###################### Loops and iterations ###########################
-----------------------------------------------------------------------

While Loop
-----------
var i = 1;                      // initialize
while (i < 100) {               // enters the cycle if statement is true
	i *= 2;                     // increment to avoid infinite loop
	document.write(i + ", ");   // output
}

Do While Loop
---------------
var i = 1;                      // initialize
do {                            // enters cycle at least once
	i *= 2;                     // increment to avoid infinite loop
	document.write(i + ", ");   // output
} while (i < 100)

For Loop
--------------
for (var i = 0; i < 10; i++) {
	if (i == 5) { break; }          // stops and exits the cycle
	document.write(i + ", ");       // last output number is 4
}

Continue
--------------
for (var i = 0; i < 10; i++) {
	if (i == 5) { continue; }       // skips the rest of the cycle
	document.write(i + ", ");       // skips 5
}

-----------------------------------------------------------------------
###################### HOISTING & CLOSURE #############################
-----------------------------------------------------------------------
// Function Hoisting: Hoisting has the advantage of allowing you to use a function before declaring
display("Lion");
function display(inputString) {
 console.log(inputString); // 'Lion' gets logged
}

// CLOSURE
// A closure is a function that has been bundled together (enclosed) with references to its surroundings (the lexical environment).

function subtractor(subtractingInteger) {
 return function(a) {
   return a - subtractingInteger;
 };
}
var subtract2 = subtractor(2);
var subtract5 = subtractor(5);
console.log(subtract2(5));  // 3 is logged
console.log(subtract5(5)); // 0 is logged

-----------------------------------------------------------------------
###################### TRY & ERROR ###############################
-----------------------------------------------------------------------

Errors⚠
try {                           // block of code to try
	undefinedFunction();
}
catch(err) {                    // block to handle errors
	console.log(err.message);
}

-----------------------------------------------------------------------
###################### PROMISES ###############################
-----------------------------------------------------------------------

function sum (a, b) {
	return Promise(function (resolve, reject) {
	 setTimeout(function () {                                       // send the response after 1 second
	   if (typeof a !== "number" || typeof b !== "number") {        // testing input types
		 return reject(new TypeError("Inputs must be numbers"));
	   }
	   resolve(a + b);
	 }, 1000);
	});
}

var myPromise = sum(10, 5);
myPromsise.then(function (result) {
	document.write(" 10 + 5: ", result);
	return sum(null, "foo");              // Invalid data and return another promise
}).then(function () {                   // Won't be called because of the error
}).catch(function (err) {               // The catch handler is called instead, after another second
	console.error(err);                   // => Please provide two numbers to sum.
});


-----------------------------------------------------------------------
--- JAVASCRIPT TWEAKS ---
	- all global variables are properties of window.
	- Writing var a = 1 is functionally equivalent to writing window.a = 1.
	- all variable declarations are hoisted to the top of the containing scope.
	- Consider this simpler example:
		alert("a" in window);
		var a;

		-- Equivalent to --
		var a;
		alert("a" in window);

	- while variable declarations are hoisted, variable initializations are not
	-  Just to be clear, a function declaration looks like this:
		function functionName(arg1, arg2){
		    //function body
		}
		This is opposed to a function expression, which is a variable assignment:

		var functionName = function(arg1, arg2){
		    //function body
		};
	- function expressions are not hoisted.
	- function declarations override variable declarations but not variable initializations. i.e.
	- The variable initialization overrides the function declaration.
	- When a method is called on an object, this points to the object on which the method resides.
	- this is also equal to window inside of a function that isn’t an object property
	-
-----------------------------------------------------------------------
--- MISCELLANEOUS ---

	// The directive looks like a string: "use strict" or 'use strict'. When it is located at the top of a script, the whole script works the “modern” way.

	"use strict";

	//declare variable using let
	let message = "Hello"
	let user = 'John', age = 25, message = 'Hello';

	//In older scripts, you may also find another keyword: var instead of let:
	var message = 'Hello';

	//To declare a constant (unchanging) variable, use const instead of let:
	const myBirthday = '18.04.1982';

	//The typeof operator
	- The typeof operator returns the type of the argument. .
	- As an operator: typeof x. OR
	- As a function: typeof(x).

------------------------------------------------------------
--- BASIC TYPES IN  JS ---
------------------------------------------------------------
There are 8 basic data types in JavaScript.

	-number 	// for numbers of any kind: integer or floating-point, integers are limited by ±253.
	-bigint 	// is for integer numbers of arbitrary length.
	-string 	// for strings. A string may have one or more characters, there’s no separate single-character type.
	-boolean 	// for true/false.
	-null 		// for unknown values – a standalone type that has a single value null.
	-undefined 	// for unassigned values – a standalone type that has a single value undefined.
	-object 	// for more complex data structures.
	-symbol 	// for unique identifiers.
-----------------------------------------------------------------------
--- BackTick ---

	let name = "Ilya";

	// the expression is a number 1
	alert( `hello ${1}` ); // hello 1

	// the expression is a string "name"
	alert( `hello ${"name"}` ); // hello name

	// the expression is a variable, embed it
	alert( `hello ${name}` ); // hello Ilya

--- TypeConversion ---

	let value = true;
	alert(typeof value); // boolean

	value = String(value); // now value is a string "true"
	alert(typeof value); // string

	let num = Number(str); // becomes a number 123

	let age = Number("an arbitrary string instead of a number");
	alert(age); // NaN, conversion failed

--- Numeric Conversion Rules ---

	Value			Becomes…
	undefined		NaN
	null			0
	true and false	1 and 0
	string			Whitespaces from the start and end are removed.
					If the remaining string is empty, the result is 0. Otherwise, the number is “read” from the string. An error gives NaN.

	alert( Number("   123   ") ); // 123
	alert( Number("123z") );      // NaN (error reading a number at "z")
	alert( Number(true) );        // 1
	alert( Number(false) );       // 0

--- Boolean Conversion ---

	Value							Becomes…
	0, null, undefined, NaN, ""		false
	any other value					true

-----------------------------------------------------------------------
--- OPERATORS  ---

	alert( 5 % 2 ); // 1, a remainder of 5 divided by 2
	alert( 8 % 3 ); // 2, a remainder of 8 divided by 3

	alert( 2 ** 2 ); // 4  (2 multiplied by itself 2 times)
	alert( 2 ** 3 ); // 8  (2 * 2 * 2, 3 times)
	alert( 2 ** 4 ); // 16 (2 * 2 * 2 * 2, 4 times)
	alert( 4 ** (1/2) ); // 2 (power of 1/2 is the same as a square root)
	alert( 8 ** (1/3) ); // 2 (power of 1/3 is the same as a cubic root)

--- Concatenation ---

	alert( '1' + 2 ); // "12"
	alert( 2 + '1' ); // "21"
	alert(2 + 2 + '1' ); // "41" and not "221"

	alert( 6 - '2' ); // 4, converts '2' to a number
	alert( '6' / '2' ); // 3, converts both operands to numbers

--- Uniary + ---

	let apples = "2";
	let oranges = "3";

	// both values converted to numbers before the binary plus
	alert( +apples + +oranges ); // 5

	// the longer variant
	// alert( Number(apples) + Number(oranges) ); // 5

--- Assignment Operator = ---

	let a = 1;
	let b = 2;
	let c = 3 - (a = b + 1);
	alert( a ); // 3
	alert( c ); // 0


	let counter = 2;
	counter++;        // works the same as counter = counter + 1, but is shorter
	alert( counter ); // 3

--- Find value of expressions ---

	"" + 1 + 0 = "10" 	// (1)
	"" - 1 + 0 = -1 	// (2)
	true + false = 1
	6 / "3" = 2
	"2" * "3" = 6
	4 + 5 + "px" = "9px"
	"$" + 4 + 5 = "$45"
	"4" - 2 = 2
	"4px" - 2 = NaN
	7 / 0 = Infinity
	" -9  " + 5 = " -9  5" // (3)
	" -9  " - 5 = -14 		// (4)
	null + 1 = 1 // (5)
	undefined + 1 = NaN 	// (6)
	" \t \n" - 2 = -2 // (7)


------------------------------------------------------------
--- ALERT PROMPT ---

	let a = prompt("First number?", 1);
	let b = prompt("Second number?", 2);

	alert(a + b); // 12



------------------------------------------------------------
################## STRINGS ##########################
------------------------------------------------------------
--- STRINGS ---

	-- String comparison --
	alert( 'Z' > 'A' ); // true
	alert( 'Glow' > 'Glee' ); // true
	alert( 'Bee' > 'Be' ); // true

------------------------------
	# LENGTH
	var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
	let sln = txt.length;

------------------------------

	# charAt
	alert( str.charAt(0) ); // H
	for (let char of "Hello") {
	  alert(char); // H,e,l,l,o (char becomes "H", then "e", then "l" etc)
	}

------------------------------

	# TOUPPERCASE & TOLOWERCASE
	alert( 'Interface'.toUpperCase() ); // INTERFACE
	alert( 'Interface'.toLowerCase() ); // INTERFACE


------------------------------

	# str.indexOf - SEARCHING A SUBSTRING
	let str = 'Widget with id';
	alert( str.indexOf('Widget') ); // 0, because 'Widget' is found at the beginning
	alert( str.indexOf('widget') ); // -1, not found, the search is case-sensitive
	alert( str.indexOf("id") ); // 1, "id" is found at the position 1 (..idget with id)

------------------------------

	# FIND ALL OCCURENCES OF A SUBSTRING
	let str = "As sly as a fox, as strong as an ox";
	let target = "as";
	let pos = -1;
	while ((pos = str.indexOf(target, pos + 1)) != -1) {
	  alert( pos );
	}

------------------------------

	# GETTING LAST INDEX OF SUBSTRING
	str.lastIndexOf(substr, pos) - searches from the end.

------------------------------

	# SLICE - GETTING A SUBSTRING
	let str = "stringify";
	alert( str.slice(0, 5) ); // 'strin', the substring from 0 to 5 (not including 5)
	alert( str.slice(0, 1) ); // 's', from 0 to 1, but not including 1, so only character at 0

	alert( str.slice(2) ); // 'ringify', from the 2nd position till the end

	alert( str.slice(-4, -1) ); // 'gif'

------------------------------

	# SUBSTRING
	// these are same for substring
	alert( str.substring(2, 6) ); // "ring"
	alert( str.substring(6, 2) ); // "ring"

	// ...but not for slice:
	alert( str.slice(2, 6) ); // "ring" (the same)
	alert( str.slice(6, 2) ); // "" (an empty string)

------------------------------

	# SUBSTRING WITH START AND LENGTH
	str.substr(start [, length])
	- Returns the part of the string from start, with the given length.
	let str = "stringify";
	alert( str.substr(2, 4) ); // 'ring', from the 2nd position get 4 characters


-----------------------------------------------------------------------
###################### ARRAYS ###############################
-----------------------------------------------------------------------
--- Arrays ---

	# ADD/REMOVE ITEMS

	arr.push(...items) – adds items to the end,
	arr.pop() – extracts an item from the end,
	arr.shift() – extracts an item from the beginning,
	arr.unshift(...items) – adds items to the beginning.

------------------------------

	# DELETE ELEMENT FROM ARRAYS
	let arr = ["I", "go", "home"];
	delete arr[1]; // remove "go"
	alert( arr[1] ); // undefined
	// now arr = ["I",  , "home"];
	alert( arr.length ); // 3

------------------------------

	# SPLICE - method is a swiss army knife for arrays. It can do everything: insert, remove and replace elements.

	let arr = ["I", "study", "JavaScript"];
	arr.splice(1, 1); // from index 1 remove 1 element
	alert( arr ); // ["I", "JavaScript"]

------------------------------

	# SPLICE RETURNS ARRAY OF REMOVED ELEMENTS
	let arr = ["I", "study", "JavaScript", "right", "now"];
	// remove 2 first elements
	let removed = arr.splice(0, 2);
	alert( removed ); // "I", "study" <-- array of removed elements

	# SPLICE TO ADD ELEMENTS - he splice method is also able to insert the elements without any removals. For that we need to set deleteCount to 0:
	let arr = ["I", "study", "JavaScript"];
	// from index 2
	// delete 0
	// then insert "complex" and "language"
	arr.splice(2, 0, "complex", "language");
	alert( arr ); // "I", "study", "complex", "language", "JavaScript"

------------------------------

	## SLICE //its not splice as above
	arr.slice([start], [end])
	let arr = ["t", "e", "s", "t"];
	alert( arr.slice(1, 3) ); // e,s (copy from 1 to 3)
	alert( arr.slice(-2) ); // s,t (copy from -2 till the end)

------------------------------

	# CONCATENATE TWO OR MORE ARRAYS
	let arr = [1, 2];

	// create an array from: arr and [3,4]
	alert( arr.concat([3, 4]) ); // 1,2,3,4

	// create an array from: arr and [3,4] and [5,6]
	alert( arr.concat([3, 4], [5, 6]) ); // 1,2,3,4,5,6

	// create an array from: arr and [3,4], then add values 5 and 6
	alert( arr.concat([3, 4], 5, 6) ); // 1,2,3,4,5,6


------------------------------

	## SEARCHING
	let arr = [1, 0, false];
	alert( arr.indexOf(0) ); // 1
	alert( arr.indexOf(false) ); // 2
	alert( arr.indexOf(null) ); // -1
	alert( arr.includes(1) ); // true

	const arr = [NaN];
	alert( arr.indexOf(NaN) ); // -1 (should be 0, but === equality doesn't work for NaN)
	alert( arr.includes(NaN) );// true (correct)

------------------------------

	## FIND AND FINDINDEX
	let result = arr.find(function(item, index, array) {
	  // if true is returned, item is returned and iteration is stopped
	  // for falsy scenario returns undefined
	});

	let users = [
	  {id: 1, name: "John"},
	  {id: 2, name: "Pete"},
	  {id: 3, name: "Mary"}
	];
	let user = users.find(item => item.id == 1);
	alert(user.name); // John

------------------------------

	## FILTER  - 	The find method looks for a single (first) element that makes the function return true.

	let results = arr.filter(function(item, index, array) {
	  // if true item is pushed to results and the iteration continues
	  // returns empty array if nothing found
	});

	let users = [
	  {id: 1, name: "John"},
	  {id: 2, name: "Pete"},
	  {id: 3, name: "Mary"}
	];
	// returns array of the first two users
	let someUsers = users.filter(item => item.id < 3);
	alert(someUsers.length); // 2

------------------------------

	## MAP --
	- The arr.map method is one of the most useful and often used.

	let result = arr.map(function(item, index, array) {
	  // returns the new value instead of item
	});

	let lengths = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);
	alert(lengths); // 5,7,6

------------------------------

	## SORT

	let arr = [ 1, 2, 15 ];
	// the method reorders the content of arr
	arr.sort();
	alert( arr );  // 1, 15, 2


	function compareNumeric(a, b) {
	  if (a > b) return 1;
	  if (a == b) return 0;
	  if (a < b) return -1;
	}
	let arr = [ 1, 2, 15 ];
	arr.sort(compareNumeric);
	alert(arr);  // 1, 2, 15

	let countries = ['Österreich', 'Andorra', 'Vietnam'];
	alert( countries.sort( (a, b) => a > b ? 1 : -1) ); // Andorra, Vietnam, Österreich (wrong)
	alert( countries.sort( (a, b) => a.localeCompare(b) ) ); // Andorra,Österreich,Vietnam (correct!)


------------------------------

	## REVERSE --
	let arr = [1, 2, 3, 4, 5];
	arr.reverse();
	alert( arr ); // 5,4,3,2,1


------------------------------

	## SPLIT AND JOIN
	let names = 'Bilbo, Gandalf, Nazgul';
	let arr = names.split(', ');
	for (let name of arr) {
	  alert( `A message to ${name}.` ); // A message to Bilbo  (and other names)
	}

	let arr = 'Bilbo, Gandalf, Nazgul, Saruman'.split(', ', 2);
	alert(arr); // Bilbo, Gandalf

	let str = "test";
	alert( str.split('') ); // t,e,s,t

	let arr = ['Bilbo', 'Gandalf', 'Nazgul'];
	let str = arr.join(';'); // glue the array into a string using ;
	alert( str ); // Bilbo;Gandalf;Nazgul

------------------------------

	## REDUCE AND REDUCERIGHT
	let value = arr.reduce(function(accumulator, item, index, array) {
	  // ...
	}, [initial]);


	accumulator – is the result of the previous function call, equals initial the first time (if initial is provided).
	item – is the current array item.
	index – is its position.
	array – is the array.

	let arr = [1, 2, 3, 4, 5];
	let result = arr.reduce((sum, current) => sum + current, 0);
	alert(result); // 15


	alert(typeof {}); // object
	alert(typeof []); // same

------------------------------

	### Summary
	A cheat sheet of array methods:

	## To add/remove elements:
	push(...items) 		– adds items to the end,
	pop() 				– extracts an item from the end,
	shift()				– extracts an item from the beginning,
	unshift(...items) 	– adds items to the beginning.
	splice(pos, deleteCount, ...items) – at index pos delete deleteCount elements and insert items.
	slice(start, end) 	– creates a new array, copies elements from position start till end (not inclusive) into it.
	concat(...items) 	– returns a new array: copies all members of the current one and adds items to it. If any of items is an array, then its elements are taken.

------------------------------

	## To search among elements:

	indexOf/lastIndexOf(item, pos) 	– look for item starting from position pos, return the index or -1 if not found.
	includes(value) 				– returns true if the array has value, otherwise false.
	find/filter(func) 				– filter elements through the function, return first/all values that make it return true.
	findIndex is like find, but returns the index instead of a value.

------------------------------

	## To iterate over elements:

	forEach(func) 					– calls func for every element, does not return anything.

------------------------------

	## To transform the array:
	map(func) 					– creates a new array from results of calling func for every element.
	sort(func) 					– sorts the array in-place, then returns it.
	reverse() 					– reverses the array in-place, then returns it.
	split/join 					– convert a string to array and back.
	reduce(func, initial) 		– calculate a single value over the array by calling func for each element and passing an intermediate result between the calls.

------------------------------

	## Additionally:
	Array.isArray(arr) 			- checks arr for being an array.

	## Please note that methods sort, reverse and splice modify the array itself.



-----------------------------------------------------------------------
--- IF ELSE ---

	let year = prompt('In which year was the ECMAScript-2015 specification published?', '');

	if (year < 2015) {
	  alert( 'Too early...' );
	} else if (year > 2015) {
	  alert( 'Too late' );
	} else {
	  alert( 'Exactly!' );
	}

--- conditional operator ---

	let result = condition ? value1 : value2;

--- Multiple? ---

	let age = prompt('age?', 18);

	let message = (age < 3) ? 'Hi, baby!' :
	  (age < 18) ? 'Hello!' :
	  (age < 100) ? 'Greetings!' :
	  'What an unusual age!';

	alert( message );

------------------------------------------------------------
## LOOPS ##
------------------------------------------------------------

--- For Loop ---

	for (let i = 0; i < 3; i++) { // shows 0, then 1, then 2
	  alert(i);
	}

--- FOREACH ---

	arr.forEach(function(item, index, array) {
	  // ... do something with item
	});

	// for each element call alert
	["Bilbo", "Gandalf", "Nazgul"].forEach(alert);

	["Bilbo", "Gandalf", "Nazgul"].forEach((item, index, array) => {
	  alert(`${item} is at index ${index} in ${array}`);
	});



-----------------------------------------------------------------------

const myArray = [1,2,3,4]

---MAP---
newArray = myArray.map(el => el+1)
//newArray = [2,3,4,5]
//el is argument passed as each element.
newArray = myArray.map(() => 'a') // no argument passed.

-----------------------------------------------------------------------

---FETCH & PROMICES---
-earlier fetch , promices in ES-6 to simplify it.

fetch('link of url to fetch data'_
	.then(response => response.json)
	.then(json => console.log(json))
	.catch(error => console.log('Ihave errored'));

----------------------------------------------------------------------

const myPromise = new Promice((resolve, reject) =>{
	if(flase){
	 setTimeout(()=>{
		resolve('I hve succeeded');
	 }, 1000);
	} else{
		reject('I hav e failed');
	}
});

myPromise
 .then(value => console.log(value))
 .catch(rejectValue => console.log(rejectValue));

OR

myPromise
 .then(value => value+'!!!') 	//value+'!!!' is returned and passed to next then()
 .then(newVal => console.log(newVal))
 .catch(rejectValue => console.log(rejectValue));


-------------------------------------------
---FILTER---
const myAarr = [1,3,5,7,9]
myArr.filter(el => el > 4) //if  el>4 , element retains in new array else removed.

---INCLUDES---

-takes a single argument.
myArr.includes(3) - true
myArr.includes(3, index) - starts searching from the index value & return true or false

includes - finds primitive type by value and objects by references.

----------------------------------------------
---ASYNC & WAIT---
------------------------------------------------------------
--making a synchronous function to async methods---

fetch('')
.then(res => res.json)
.then(users => {
	const fu = user[0];
	return fetch('');
})
.then(res => res.json())
.then(posts => console.log(posts));
.catch(error =>  consol.log(errors)); //catch errors for any then methods.


---converting above async method to sync method---

const myAsyncFunction = async () => {
	try{
		const userRes = await fetch('https://jsonplaceholder.typicode.com/users');
		const users = await userRes.json();
		const secondUser = users[1];
		const postRes = await fetch('https://jsonplaceholder.typicode.com/?userId'+secondUser);
		const posts = await postRes.json();
		console.log(posts);
	}
	catch (err){
		console.log('there is error');
	}
};

-----------------------------------------------------------
---FIND---
const myAarr = [1,3,5,7,9]
myArr.find(el=>el===5); or el>5

---REDUCE---
const myAarr = [1,2,3,4,5]
--reduce if we want two things-
	- get only one element at the end.
	- if want to persist the outcome of each subsequent iteration.

myArr.reduce((accumulator, currentElement) =>
	accumulator + currentElement, 0); //0 is starting value of accumulator


------------------------------------------------------------
---Memoization---Caching
------------------------------------------------------------
-memoization is caching returned value for a function for set of parameters.

---Currying---
const multiplyBy = (a) => (b) => a*b;

multiplyBy(5)(4) // = 20;
or
multiplyBy5 = multiplyBy(5);
multiplyBy5(4) // = 20


------------------------------------------------------------
---Built in functions
------------------------------------------------------------
parseInt('234', 10); //234

// You can also use the unary + operator to convert values to numbers:
+ '42';   // 42
parseInt('hello', 10); // NaN

// reliably test for NaN using the built-in Number.isNaN() function, which behaves just as its name implies:

Number.isNaN(NaN); // true
Number.isNaN('hello'); // false
Number.isNaN('1'); // false
Number.isNaN(undefined); // false
Number.isNaN({}); // false
Number.isNaN([1]) // false
Number.isNaN([1,2]) // false

// But don’t test for NaN using the global isNaN() function, which has unintuitive behavior:

isNaN('hello'); // true
isNaN('1'); // false
isNaN(undefined); // true
isNaN({}); // true
isNaN([1]) // false
isNaN([1,2]) // true

// You can test for Infinity, -Infinity and NaN values using the built-in isFinite() function:

isFinite(1 / 0); // false
isFinite(-Infinity); // false
isFinite(NaN); // false

------------------------------------------------------------
---ARROW in functions
------------------------------------------------------------


var getA = function(a){
	retur a;
};
OR
let getA = a => a;

let square = a => a*a;
let square = (a) => { return a*a};

-----------------------------------------------------------------------
###################### FUNCTIONS ###############################
-----------------------------------------------------------------------



```
