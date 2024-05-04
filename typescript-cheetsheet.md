## Typescript

- [Typescript lang from Scratch](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html)
- [2ality from ex](https://2ality.com/2018/04/type-notation-typescript.html)
- [Mit rust programming](https://web.mit.edu/rust-lang_v1.25/arch/amd64_ubuntu1404/share/doc/rust/html/book/second-edition/ch01-00-introduction.html)
- [Rust CS binding](https://www.cs.brandeis.edu/~cs146a/rust/doc-02-21-2015/book/README.html)
- [Doc rust lang](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html)

## Typescript language tuts

```
TYPESCRIPT TUTS
---------------------------


References:-
=> https://rmolinamir.github.io/typescript-cheatsheet/
=> https://2ality.com/2018/04/type-notation-typescript.html

-----------------------------------------------------------------------
###################### TYPES ###############################
-----------------------------------------------------------------------
Primitive Types
------------------
There are 7 primitive types in JS:

- string
- number
- bigInt
- boolean
- undefined
- null
- symbol

let firstname: string = "Danny"
let firstname = "Danny"

Union Types
------------------
A variable that can be assigned more than one type

let age: number | string
age = 26
age = "26"

Dynamic Types
------------------
The any type basically reverts TS back to JS

let age: any = 100
age = true

Literal Types
------------------
We can refer to specific strings & numbers in type positions

let direction: "UP" | "DOWN"
direction = "UP"

Objects
-------------------
let person: {
  name: string
  isProgrammer: boolean
}

person = {
  name: "Danny",
  isProgrammer: true,
}

person.age = 26 // Error - no age prop on person object
person.isProgrammer = "yes" 

declaring and Initiating variables
---------------------
// Arrays
const hobbies: string[] = ['Programming', 'Cooking'];
const numbers = [1, 3.22, 6, -1] // This variable will automatically be assigned a number[] array type.

// Tuples
const address: [string, number] = ["Street", 99];

// Objects
let myCar: any = 'BMW';
console.log(myCar); // Prints: BMW

myCar = { brand: 'BMW', series: 3 };
console.log(myCar) // Prints: { brand: "BMW", series: 3 }

// Enums
enum Color {
	Gray, 		// 0
	Red, 		// 1
	Green = 100, 	// 100
	Blue, 		// 101
	Yellow = 2 		// 2
}

const myColor: Color = Color.Green
console.log(myColor); // Prints: 100

Functions => Argument Types || Function Types
-----------------------------------------------

// argument types
function multiply(value1: number, value2: number) {
	return value1 * value2;
}

// console.log(multiply('Robert', 5)) // Not possible, both arguments must be of type number.
console.log(multiply(10,5)) // Prints: 50

//function type
const myMultiply: (val1: number, val2: number) => number;
// myMultiply = sayHello; // Not possible.
// myMultiply(); // Not possible.
myMultiply = multiply;

console.log(myMultiply(5, 2));

Void Function type
--------------------
// The type void is a little like the opposite of any: the absence of having any type at all. 

function sayHello(): void {
  console.log('Hello!');
  // return myName; // Not possible because the function can't return anything due to the void assigned type (more on this below).
}


// Declaring variables of type void is not useful because you can only assign undefined or null to them:

let unusable: void = undefined;

Objects
------------
// The type object represents the non-primitive type, i.e. any thing that is not number, string, boolean, symbol, null, or undefined.

 let userData: { name: string, age: number } = {
    name: 'Max',
    age: 27
  };
  // userData = { // Not valid
  //   name: 2,
  //   age: 'Age'
  // };
  // userData = { // Not valid
  //   a: 'Robert',
  //   b: 24
  // };
  userData = {
    name: 'Robert',
    age: 24
  };

Complex Objects
-------------------
// As you may expect, the assigned types to the object key-value pairs can reach high levels of complexity, for example:

  let complex: { data: number[], output: (all: boolean) => number[] } = {
    data: [100, 3,99, 10],
    output: function(all: boolean): number[] {
      return this.data
    }
  };
  // complex = {}; // Not possible.


Optional object properties
-----------------------------

  const right: { name: string, age?: number } = {
    name: 'Robert'
  };

  const alsoRight: { name: string, age?: number } = {
    name: 'Robert',
    age: 24
  };

  // This is not possible because the name key-value pair is missing.
  // const wrong: { name: string, age?: number } = {
  //   age: 24
  // };


Alias
----------
  type Complex = { data: number[], output: (all: boolean) => number[] };

  let complex2: Complex  = {
    data: [100, 3,99, 10],
    output: function(all: boolean): number[] {
      return this.data
    }
  };

Union
--------

// Variables are not restricted to only one assigned type. This is where union types come in where we can assign two or more types (e.g. assign number and string) to a single variable. For example:

  let myRealRealAge: number | string = 24;
  myRealRealAge = '24';
  // myRealRealAge = true // Not possible since myRealRealAge only accepts a number or a string.


Intersection
-------------
  interface Loggable {
      log(name: string, age: number): void
  }

  interface Person {
      name: string
      age: number
      isStark?: boolean // May be undefined.
  }

  type LoggablePerson = Loggable & Person;

  const logPerson:(name: string, age: number) => void = (name, age) => {
      console.log(`I am ${name}, and I am ${age} years old.`)
  }

  const jonSnow: LoggablePerson = {
      name: "Jon Snow",
      age: 23,
      log: logPerson
  }

  console.log('jonSnow.name ->', jonSnow.name); // Prints: "Jon Snow"
  console.log('jonSnow.age ->', jonSnow.age); // Prints: 23
  console.log('jonSnow.isStark ->', jonSnow.isStark); // Prints: undefined
  console.log(
      'jonSnow.log(jonSnow.name, jonSnow.age) ->',
      jonSnow.log(jonSnow.name, jonSnow.age)
  ); // Prints: I am Jon Snow, and I am 23 years old.


Check
-------------
Programmatically checking for types work exactly as it works in JavaScript:

  let finalValue = 'A string';
  if (typeof finalValue == 'string') {
    console.log('finalValue is a string');
  }

Nullable
----------
// In TypeScript, both undefined and null actually have their own types named undefined and null respectively. 
// Much like void, they’re not extremely useful on their own:

  let canBeNull: null | number = 12;

  canBeNull = null;
  let canAlsoBeNull;
  canAlsoBeNull = null;
  let canThisBeAny = null;
  canThisBeAny = 12;

Type Assertion
--------------
  const someValue: any = "this is a string";
  const strLength: number = (<string>someValue).length;


Template Literals
--------------------
  const userName = 'Robert';
  const greeting = `Hello I'm ${userName}`;

  console.log(greeting)

ES6
-----
// TypeScript natively supports the newer ES6 (A.K.A. ECMAScript 6 and ECMAScript 2015) JavaScript features.

  const userName = 'Robert';
  const greeting = `Hello I'm ${userName}`;
  console.log(greeting)

  const greet = (name: string = 'Robert') => console.log(`Hello, ${name}`);
  greet('Robert Molina');

  const greet = (name: string = 'Robert') => console.log(`Hello, ${name}`);
  greet(); // Prints: "Robert"

Spread Operator
----------------
  const numbers: number[] = [-3, 33, 38, 5];
  console.log(Math.min(...numbers));
  const newArray: number[] = [55, 20, ...numbers];
  console.log(newArray);

Arrays Destructuring
--------------------
  const testResults: number[] = [3.89, 2.99, 1.38];
  const [result1, result2, result3] = testResults;
  console.log(result1, result2, result3);

Object Destructuring
----------------------
  const scientist: { firstName: string, experience: number } = { firstName: 'Robert', experience: 9000 };
  const { firstName, experience } = scientist;
  console.log(firstName, experience);


-----------------------------------------------------------------------
###################### Classes ###############################
-----------------------------------------------------------------------
// Traditional JavaScript uses functions and prototype-based inheritance to build up reusable components
// TypeScript offers public, private, and protected modifiers to every class member variable. 
// Unlike C# which requires that each member be explicitly labeled public, In TypeScript, each member is public by default.

  class Person {
    private type: string | null = null;
    protected age: number = 23;

    constructor(public name: string, public userName: string, private email: string) {
      this.name = name;
      this.userName = userName;
      this.email = email;
    }

    public printAge = () => {
      console.log(this.age);
      this.setType('Young guy');
    }

    private setType = (type: string) => {
      this.type = type;
      console.log(this.type);
    }
  }

  const person = new Person('Francisco', 'rmolinamir', 'example@email.com');
  person.printAge(); // Prints: 23
  // person.setType('Cool guy'); // Not possible, since setType is a private member of Person.

Private Members
--------------------
// When a member is marked private, it cannot be accessed from outside of its containing class. 
// However, should a class X inherit properties from Person, class A will be able to access all private properties from Person (e.g. type and setType) due to being inside (or having access to)

 class Type {
      private type: string | null = null;

      setType = (type: string) => {
        this.type = type;
        console.log(this.type);
      }
  }

  class Person extends Type {
      protected age: number = 23;

      constructor(public name: string, public userName: string, private email: string) {
        super()
        this.name = name;
        this.userName = userName;
        this.email = email;
      }

      public printAge = () => {
        console.log(this.age);
        this.setType('Young guy');
      }
  }

  const person = new Person('Rob', 'rm', 'email');

  person.setType('Cool guy'); // Prints: Cool guy

  console.log(person); // Prints:
  /**
   * Person
   *
   * age: 23
   * email: "email"
   * name: "Rob"
   * printAge: ƒ ()
   * setType: ƒ (type)
   * type: "Cool guy"
   * userName: "rm"
   *
   */


Inheritance
-------------
  class Robert extends Person {
    constructor(userName: string, email: string) {
      super('Robert Molina', userName, email);
      this.age = 25;
      this.printAge()
    }
  }

  const robert = new Robert('rmolinamir', 'example@email.com');

  console.log(robert);

Getters & Setters
-------------------
class Plant {
    private _species: string = 'Default';
    get species() {
      return this._species;
    }
    set species(value: string) {
      if (value.length > 3) {
        this._species = value;
      } else {
        this._species = 'Default';
      }
    }
    public getSpecies = () => this._species
  }

  const plant = new Plant();

  console.log(plant.species); // Prints Default
  plant.species = 'AB';
  console.log(plant.species); // Prints Default
  plant.species = 'Green Plant';
  console.log(plant.species); // Prints Green Plant

Static Properties & Methods
----------------------------
  class Helpers {
    static PI: number = 3.14;
    static calcCircumference(diameter: number): number {
      return this.PI * diameter;
    }
  }

  console.log(Helpers.PI); // Prints: 3.14
  console.log(2 * Helpers.PI); // Prints: 6.28
  console.log(Helpers.calcCircumference(10)); // Prints: 31.42

Abstract Classes
--------------------

  abstract class Project {
    projectName: string = 'Default';
    budget: number = 0;
    abstract changeName(name: string): void;
    calcBudget() {
      return this.budget * 2;
    }
  }

  class ITProject extends Project {
    changeName = (name: string) => {
      this.projectName = name;
    }
  }

  const newProject = new ITProject();

  console.log(newProject) // Prints: { projectName: "Default", budget: 0, ...  }
  newProject.changeName('Super IT Project');
  console.log(newProject); // Prints: { projectName: "'Super IT Project", budget: 0, ...  }
  newProject.budget = 1000;
  console.log(newProject.budget); // Prints: 1000
  console.log(newProject.calcBudget()); // Prints: 2000

Export
----------
Any declaration (such as a variable, function, class, type alias, enum or interface) can be exported by adding the export keyword.

Exporting a variable and a function:
-------------------------------------
  export const PI = 3.14;
  export const calculateCircumference = (diameter: number) => {
    return diameter * PI;
  }

Exporting an interface for a react.js class component’s state:
---------------------------------------------------------------
  export interface IAppState {
    counterValue: number;
  }

  class App extends React.Component<{} /* IAppProps */, IAppState> {
    public state = { counterValue: 0 }; // State is required to be public.
    // ...
  }

Exporting an interface for a react.js functional component onClick handlers:
-----------------------------------------------------------------------------
  export enum ECounterHandlers {
    Inc,
    Dec
  }
  interface ICounterOutputProps {
    counter: number;
    onClick: (mode: ECounterHandlers) => void;
  }
  const counterOutput = (props: ICounterOutputProps) => {
    return (
      /// ...
        <button onClick={() => props.onClick(ECounterHandlers.Dec)}>Decrement</button>
        <button onClick={() => props.onClick(ECounterHandlers.Inc)}>Increment</button>
      /// ...
    );
  }

Default Exports
----------------
// The default exports are really handy. For instance, a library like React.js might have a default export of React, commonly imported under the name React. 
// Each file may only have one default export, for example:

  const calculateRectangle = (width: number, length: number) => {
    return width * length;
  }
  export default calculateRectangle

Import
--------
//  Importing is just about as easy as exporting from a module.
//  Importing an exported declaration is done through using the import keyword. 

  TypeScript v^3.0
  ├── app.ts
  ├── src
  │   ├── circle.ts
  │   ├── rectangle.ts
  
  import { PI, calculateCircumference } from './src/circle'
  import calculateRectangle from './src/rectangle'

  console.log(PI); // Prints: 3.14
  console.log(calculateCircumference(10)); // Prints: 31.42
  console.log(calculateRectangle(5, 10)); // Prints: 50


Interfaces
------------
  interface SimplePerson {
    firstName: string;
  }
  const simplePerson: SimplePerson = { firstName: 'Robert' };
  const simpleGreet = (simplePerson: SimplePerson) => console.log(`Hello ${simplePerson}!`);
  simpleGreet(simplePerson); // Prints: "Hello Robert!"

Interfaces with optional properties
-----------------------------------
  interface SimplePerson {
    firstName: string;
    lastName?: string;
    age?: number;
  }

  // Not possible because the firstName key-value pair is missing.
  // const wrong: SimplePerson = { lastName: 'Molina', age: 24 };
  const right: SimplePerson = { firstName: 'Robert', age: 24 };

Interface - Index Signatures (Dynamic Property Names)
-----------------------------------------------------
  interface NamedPerson {
    firstName: string;
    age?: number;
    [propName: string]: any;
  }

  const person: NamedPerson = {
    firstName: 'Robert',
    lastName: 'Molina',
    age: 24,
    hobbies: ['Programming', 'Cooking'],
    greet(lastName: string) {
      console.log(`Hi, I am ${this.firstName} ${lastName}!`);
    }
  }

Implements Keyword
------------------
1. Implementing an interface to a Class
---------------------------------------
  interface NamedPerson {
    firstName: string;
    age?: number;
    [propName: string]: any;
    greet(lastName: string): void;
  }

  class Person implements NamedPerson {
    constructor(public firstName: string, public lastName: string) {}
    greet(lastName: string) {
      console.log(`Hi, I am ${this.firstName} ${lastName}!`);
    }
  }

  const myPerson = new Person('Robert', 'Molina');
  greet(myPerson); // Prints: "Hi, I am Robert Moina"

2. Implementing an interface to a function
--------------------------------------------
  interface DoubleValueFunc {
    (number1: number, number2: number): number;
  }

  let myDoubleFunction: DoubleValueFunc;
  myDoubleFunction = (num1: number, num2: number) => {
    return (num1 + num2) * 2;
  }

  console.log(myDoubleFunction(10,50)); // Prints: 120

Interface multiple extends
--------------------------
  interface Shape {
    color: string;
  }

  interface PenStroke {
    penWidth: number;
  }

  interface Square extends Shape, PenStroke {
    sideLength: number;
  }

  const square: Square = {
    color: "magenta",
    penWidth: 2.5,
    sideLength: 0.5
  }

-----------------------------------------------------------------------
###################### GENERIC INTERFACES #############################
-----------------------------------------------------------------------
Omit type when extending an interface
-------------------------------------

type Omit<T, K extends keyof T> = Pick<T, Exclude<keyof T, K>>


// From T pick a set of properties K
declare function pick<T, K extends keyof T>(obj: T, ...keys: K[]): Pick<T, K>;
const nameAndAgeOnly = pick(person, "name", "age");  // { name: string, age: number }

type T00 = Exclude<"a" | "b" | "c" | "d", "a" | "c" | "f">;  // "b" | "d"




-----------------------------------------------------------------------
###################### GENERICS ###############################
-----------------------------------------------------------------------
  // BELOW IS NOT A GENERIC FUN
  function echo(data: string) {
    return data;
  }
  
  // Rewrite above fun to a generic one
Simple Generics
-----------------
// To write a generic, let’s take the example above and turn it into a simple generic function. 
// Here’s how the original echo function would be rewritten into a simple generic:

  function echo(data: any) {
    return data;
  }

  console.log(echo('Robert')); // Prints: "Robert"
  console.log(echo(24).length); // Prints: undefined.
  console.log(echo({ name: 'Robert', age: 24 })); // Prints: { name: "Robert", age: 24 }

Better Generics
----------------
  function betterEcho<T>(data: T) {
    return data;
  }

  // Now I get types in the IDE, the compiler also knows what type is returned from betterEcho.
  console.log(betterEcho('Robert').length);
  // console.log(betterEcho(24).length); // Compiler & IDE warning: Property 'length' does not exist on type `number`.
  console.log(betterEcho<number>(24).toExponential(2)); // I would get IDE support.
  console.log(betterEcho({ name: 'Robert', age: 24 }).age); // I would also get IDE support.

Built-in Generics
------------------
// Some types though, have built-in generics. 
// I’ve even used some as examples before without having touched yet on generics. Here are some very simple examples:

  const testResults: Array<number> = [1.94, 2.33];
  testResults.push(-2.99);
  // testResults.push('string'); // Not possible.

  // Arrays
  function printAll<T>(args: T[]) {
    args.forEach(element => console.log(element));
  }

  printAll<string>(['Apple', 'Banana']);
  printAll<number>([1, 3, 5]);
  // printAll<number>([1, 'string', 5]); // Not possible.

Generic Types
-----------------
// The Generic Types are exactly what the name says. 
// It’s a way of declaring any kind of variable with a generic type. Let’s see how to create generic functions and generic interfaces. For example:

Functions:
----------------
// The type of generic functions is just like those of non-generic functions, with the type parameters listed first, similarly to function declarations.

  function betterEcho<T>(data: T) {
    return data;
  }

  const echoStr: <T>(data: T) => T = betterEcho;
  console.log(echoStr<string>('Hello world!').toLocaleUpperCase()); // Prints: "HELLO WORLD!"

  const echoNum: <T>(data: T) => T = betterEcho;
  console.log(echoNum<number>(312).toString()); // Prints: "312"

Interfaces:
------------
  interface GenericIdentityFn<T> {
      (arg: T): T;
  }

  function identity<T>(arg: T): T {
      return arg;
  }

  let myIdentity: GenericIdentityFn<number> = identity;


Generic Class
--------------
// A generic class has a similar shape to a generic interface. Generic classes have a generic type parameter list in angle brackets (<>) following the name of the class.

// Here is a simple example for starters using constraints. 
// The generic types may be constrained by extending them to certain types. 
// For example, we may constrain (with the extends keyword) a type T to type number, or type string only. Here is an example:

  class GenericMath<T extends number | string> {
    constructor(public baseValue: T, public multiplyValue: T) {}
    calculate(): number {
      return +this.baseValue * +this.multiplyValue
    }
  }

  // const genericMath = new GenericMath<number>(10, 'string'); // Not possible because 'string' can't be converted to a number.
  // const genericMathBoolean = new GenericMath<boolean>(10, '20'); // Not possible because T only extends to number and string only.
  const onlyNumbers = new GenericMath<number>(10, 20);
  const onlyStrings = new GenericMath<string>('10', '20');
  const bothTypes = new GenericMath<number | string>(10, '20');

  console.log(onlyNumbers.calculate()); // Prints: 200
  console.log(onlyStrings.calculate()); // Prints: 200
  console.log(bothTypes.calculate()); // Prints: 200

// Here is a more advanced example where we use multiple types when defining the generic class types:

  class MultipleTypesMath<T extends number, U extends number | string> {
    constructor(public baseValue: T, public multiplyValue: U) {}
    calculate(): number {
      return +this.baseValue * +this.multiplyValue;
    }
  }

  const multipleTypesMath = new MultipleTypesMath<number, number | string>(5, '20');
  console.log(multipleTypesMath.calculate()); // Prints: 100


```
