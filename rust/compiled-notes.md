## Rust notes and Cheetcodes


```
-------------------------------
## Command Description
-------------------------------

$ cargo init            Create a new binary project
$ cargo init --lib      Create a new library project
$ cargo check           Check code for errors
$ cargo clippy          Run code linter (use rustup component add clippy to install)
$ cargo doc             Generate documentation
$ cargo run             Run the project
$ cargo --bin NAME      Run a specific project binary
$ cargo build           Build everything in debug mode

$ cargo build --bin NAME        Build a specific binary in debug mode
$ cargo build --release         Bulld everything in release mode
$ cargo build --target NAME     Build for a specific target
$ cargo --explain CODE          Detailed information regarding an compiler error code

$ cargo test                Run all tests
$ cargo test TEST_NAME      Run a specific test
$ cargo test --doc          Run doctests only
$ cargo test --examples     Run tests for example code only
$ cargo bench               Run benchmarks

-------------------------------
## FREQUENTLY USED COMMANDS
-------------------------------

$ cargo new   // it creates new project with Cargo.toml file
$ cargo build // it builds the project
$ cargo check // it checks and compile code without producing executable.

$ cargo run   //it replaces build and run executable.
            // first checks for rebuild and compiles and run code in one go.

-------------------------------
## Put following in main.rs file to avoid warnings, although warnings are superuseful
-------------------------------

#![allow(unused)]
#![allow(warnings)]
-------------------------------
## PRIMITIVE DATA TYPES
-------------------------------
## SCALAR - 4
-------------------------------
integer ->
floating-point numbers -> f32, f64
boolean -> bool
characters ->

-------------------------------
## COMPOUND - 2
-------------------------------
tuple
let tup: (i32, f64, u8) = (500, 6.4, 1);
array
let a = [1, 2, 3, 4, 5];

-------------------------------
## Signed Integers => [-2^(n-1) to 2^(n-1) -1]
-------------------------------

Type    Default  Range
----    -------  ------
i8      0        -128..127
i16     0        -32768..32767
i32     0        -2147483648..2147483647
i64     0        -9223372036854775808..9223372036854775807
i128    0        min: -170141183460469231731687303715884105728
i128    0        max: 170141183460469231731687303715884105727
isize   0        <pointer size on target architecture>

-------------------------------
## Unsigned Integers => [0 to 2^(n-1)]
-------------------------------
Type    Default Range
u8      0       0..255 
u16     0       0..65535
u32     0       0..4294967295
u64     0       0..18446744073709551615
u128    0       0..340282366920938463463374607431768211455
usize   0       <pointer size on target architecture>

-------------------------------
## Floating Point Numbers
------------------------------- 
Type    Default     Notes
----    -------     ------
f32     0           32-bit floating point
f64     0           64-bit floating point

-------------------------------
## Strings / Characters
-------------------------------
Type        Notes
-----       ---------
char        Unicode scalar value. Create with single quotes ''
String      UTF-8-encoded string
&str        Slice into String / Slice into a static str. Create with double quotes "" or r#""# for a raw mode (no escape sequences, can use double quotes)
OsString    Platform-native string
OsStr       Borrowed OsString
CString     C-compatible nul-terminated string
CStr        Borrowed CString

-------------------------------
## Other
-------------------------------
Type    Notes
----    --------
bool    true or false
unit    () No value / Meaningless value
fn      Function pointer
tuple   Finite length sequence
array   Fixed-sized array
slice   Dynamically-sized view into a contiguous sequence

-------------------------------
## Variables
-------------------------------

// SCALAR TYPES - integer, float, boolean, character

// Rust has type inference, however, type can explicitly mentioned.
let x = 5; // x: i32

// `let` will create a new variable binding
let foo = 1;

// bindings are immutable by default
foo = 2; // ERROR: cannot assign; `foo` not mutable

let mut bar = 1; // create mutable binding
bar = 2; // OK to mutate

let baz = 'a'; // use single quotes to create a character
let baz = "ok"; // use double quotes to create a string

// variables can be shadowed, so these lines have been valid
let baz = 42; // `baz` is now an integer; 'a' and "ok" no longer accessible

// Rust infers types, but you can use annotations as well
let foo: i32 = 50; // set `foo` to i32
let foo: u8 = 100; // set `foo` to u8
// let foo: u8 = 256; // ERROR: 256 too large to fit in u8

let bar = 14.5_f32; // underscore can be used to set numeric type...
let bar = 99_u8;
let bar = 1_234_567; // ...and also to make it easier to read long numbers

let baz; // variables can start uninitialized, but they must be set before usage
// let foo = baz; // ERROR: possibly uninitialized.
baz = 0; // `baz` is now initialized
// baz = 1; // ERROR: didn't declare baz as mutable

//Integers default to i32 and floats to f64

// Variables can be type annotated.
let logical: bool = true;

let a_float: f64 = 1.0;  // Regular annotation
let an_integer   = 5i32; // Suffix annotation

// Or a default will be used.
let default_float   = 3.0; // `f64`
let default_integer = 7;   // `i32`

// A type can also be inferred from context
let mut inferred_type = 12; // Type i64 is inferred from another line
inferred_type = 4294967296i64;

// A mutable variable's value can be changed.
let mut mutable = 12; // Mutable `i32`
mutable = 21;

// Error! The type of a variable can't be changed.
mutable = true;

// Variables can be overwritten with shadowing.
let mutable = true;


// naming convention:
let use_snake_case_for_variables = ();

let guess: u32 = "42".parse().expect("Not a number!");

------------------
## CHARACTERS
------------------
- chars represent a unicode scalar value => lot more than ASCII
- Unicode Scalar Values range from U+0000 to U+D7FF and U+E000 to U+10FFFF inclusive.

------------------
## COMPOUND TYPES
------------------
// TUPLES
let tup: (i32, f64, u8) = (500, 6.4, 1);

// ARRAYS
let a = [1, 2, 3, 4, 5];

------------------
## Constants
------------------

// `const` will create a new constant value
const PEACE: char = '☮'; // type annotations are required
const MY_CONST: i32 = 4; // naming conventions is SCREAMING_SNAKE_CASE

// const UNINIT_CONST: usize; // ERROR: must have initial value for constants

// use `once_cell` crate if you need lazy initialization of a constant
use once_cell::sync::OnceCell;
const HOME_DIR: OnceCell<String> = OnceCell::new();

// use .set to set the value (can only be done once)
HOME_DIR.set(std::env::var("HOME").expect("HOME not set"));

// use .get to retrieve the value
HOME_DIR.get().unwrap();

----------------------------------
## REFERENCES & BORROWING
----------------------------------
- use reference to avoid transfer of ownership
- The Rules of References
  At any given time, you can have either but not both of: 
    1. One mutable reference. 
    2. Any number of immutable references.

----------------------------------
## TYPE ALIASES
----------------------------------

//Type aliases allow long types to be represented in a more compact format.
// use `type` to create a new type alias
type Foo = Bar;
type Miles = u64;
type Centimeters = u64;
type Callbacks = HashMap<String, Box<dyn Fn(i32, i32) -> i32>>;

struct Contact {
    name: String,
    phone: String,
}
type ContactName = String;

// type aliases can contain other type aliases
type ContactIndex = HashMap<ContactName, Contact>;

// type aliases can be used anywhere a type can be used
fn add_contact(index: &mut ContactIndex, contact: Contact) {
    index.insert(contact.name.to_owned(), contact);
}

// type aliases can also contain lifetimes ...
type BorrowedItems<'a> = Vec<&'a str>;
// ... and also contain generic types
type GenericThings<T> = Vec<Thing<T>>;

----------------------------------
## FUNCTIONS
----------------------------------

// use the `fn` keyword to create a function
fn func_name() { /_ body _/ }

// type annotations required for all parameters
fn print(msg: &str) {
    println!("{msg}");
}

// use -> to return values
fn sum(a: i32, b: i32) -> i32 {
    a + b // `return` keyword optional
}
sum(1, 2); // call a function

// `main` is the entry point to all Rust programs
fn main() {}

// functions can be nested
fn outer() -> u32 {
    fn inner() -> u32 
    { 42 }
    inner() // call nested function & return the result
}

// use `pub` to make a function public
pub fn foo() {}

// naming convention:
fn snake_case_for_functions() {}

----------------------------------
## CONTROL FLOW
----------------------------------

----------------------------------
## IF condition
----------------------------------

if some_bool { /_ body _/ }

if one && another {
    // when true
} else {
    // when false
}

if a || (b && c) {
    // when one of the above
} else if d {
    // when d
} else {
    // none are true
}

// `if` is an expression, so it can be assigned to a variable
let (min, max, num) = (0, 10, 12);
let num = if num > max {
    max
} else if num < min {
    min
} else {
    num
};
assert_eq!(num, 10);

----------------------------------
## MATCH (SWITCH) Statement
----------------------------------

let num = 0;
match num {
    // ... on a single value
    0 => println!("zero"),
    
    // ... on multiple values
    1 | 2 | 3 => println!("1, 2, or 3"),
    
    // ... on a range
    4..=9 => println!("4 through 9"),

    // ... with a guard
    n if n >= 10 && n <= 20 => println!("{n} is between 10 and 20"),
    
    // ... using a binding
    n @ 21..=30 => println!("{n} is between 21 and 30"),
    
    // ... anything else
    \_ => println!("number is ignored"),
}

// `match` is an expression, so it will evaluate and can be assigned
let num = 0;
let msg = match num {
    0 => "zero",
    1 => "one",
    \_ => "other",
};
assert_eq!(msg, "zero");

----------------------------------
## WHILE
----------------------------------

// must be mutable so it can be modified in the loop
let mut i = 0;

// as long as `i` is less than 10, execute the body
while i < 10 {
    if i == 5 {
        break; // completely stop execution of the loop
    }
    if i == 8 {
        continue; // stop execution of this iteration, restart from `while`
    }
    // don't forget to adjust `i`, otherwise the loop will never terminate
    i += 1;
}

// `while` loops can be labeled for clarity and must start with single quote (')
let mut r = 0;
let mut c = 0;

// label named 'row
'row: while r < 10 {
    // label named 'col
    'col: while c < 10 {
        if c == 3 {
            break 'row; // break from 'row, terminating the entire loop
        }
        if c == 4 {
            continue 'row; // stop current 'col iteration and continue from 'row
        }
        if c == 5 {
            continue 'col; // stop current 'col iteration and continue from 'col
        }
        c += 1;
    }
    r += 1;
}

----------------------------------
while let

//while let will continue looping as long as a pattern match is successful. The let portion of while let is similar to if let: it can be used to destructure data for utilization in the loop.

---

let mut maybe = Some(10);
// if `maybe` is a `Some`, bind the inner data to `value` and execute the loop
while let Some(value) = maybe {
    println!("{maybe:?}");
    if value == 1 {
        // loop will exit on next iteration
        // because the pattern match will fail
        maybe = None;
    } else {
        maybe = Some(value - 1);
    }
}

----------------------------------
## FOR
----------------------------------

// Rust's for loop is to iterate over collections that implement the Iterator trait.

// iterate through a collection
let numbers = vec![1, 2, 3];
for num in numbers {
    // values are moved into this loop
}
----------------------------------

// .into_iter() is implicitly called when using `for`
let numbers = vec![1, 2, 3];
for num in numbers.into_iter() {
    // values are moved into this loop
}
----------------------------------

// use .iter() to borrow the values
let numbers = vec![1, 2, 3];
for num in numbers.iter() {
    // &1
    // &2
    // &3
}
----------------------------------
// ranges can be used to iterate over numbers
for i in 1..3 { // exclusive range
    // 1
    // 2
}

----------------------------------
## LOOP
----------------------------------

// The loop keyword is used for infinite loops. 
// Prefer using loop instead of while when you specifically want to loop endlessly.

loop { /_ forever _/ }
----------------------------------

// loops can be labled
'outer: loop {
    'inner: loop {
        continue 'outer; // immediately begin the next 'outer loop
        break 'inner; // exit out of just the 'inner loop
    }
}
----------------------------------
// loops are expressions
let mut iterations = 0;
let total = loop {
    iterations += 1;
    if iterations == 5 {
        // using `break` with a value will evaluate the loop
        break iterations;
    }
};
// total == 5

----------------------------------
## ENUMS & PATTERN MATCHING
----------------------------------

enum IpAddr {
    V4(String),
    V6(String),
}

let home = IpAddr::V4(String::from("127.0.0.1"));
let loopback = IpAddr::V6(String::from("::1"));

----------------------------------
// can put any kind of data inside an enum variant: strings, numeric types, or structs, 
//for example 
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}

----------------------------------
// can define methods on enums similar to structs
impl Message {
    fn call(&self) {
        // method body would be defined here
    }
}

let m = Message::Write(String::from("hello"));
m.call();

----------------------------------
// The Option Enum and Its Advantages Over Null Values
pub enum Option<T> {
    None,
    Some(T),
}

----------------------------------
// The match Control Flow Operator
enum UsState {
    Alabama,
    Alaska,
    // ... etc
}

enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}

fn value_in_cents(coin: Coin) -> u32 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {
            println!("State quarter from {:?}!", state);
            25
        },
    }
}

fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        None => None,
        Some(i) => Some(i + 1),
    }
}

let five = Some(5);
let six = plus_one(five);
let none = plus_one(None);
----------------------------------

let some_u8_value = 0u8;
match some_u8_value {
    1 => println!("one"),
    3 => println!("three"),
    5 => println!("five"),
    7 => println!("seven"),
    * => (),
}
----------------------------------

// Concise Control Flow with if let

----------------------------------

=======================================================
## STRUCTURES
=======================================================

// Structures allow data to be grouped into a single unit.

struct Foo; // define a structure containing no data
let foo = Foo; // create a new `Foo`

struct Dimension(i32, i32, i32); // define a "tuple struct" containing 3 data points
let container = Dimension(1, 2, 3); // create a new `Dimension`
let (w, d, h) = (container.0, container.1, container.2);
// w, d, h, now accessible

// define a structure containing two pieces of information
struct Baz {
    field_1: i32, // an i32
    field_2: bool, // a bool
}

// create a new `Baz`
let baz = Baz {
    field_1: 0, // all fields must be defined
    field_2: true,
};

----------------------------------
## impl Blocks
----------------------------------
// impl blocks allow functionality to be associated with a structure or enumeration.

struct Bar {
    inner: bool,
}

// `impl` keyword to implement functionality
impl Bar {
    
    // `Self` is an alias for the name of the structure
    pub fn new() -> Self {
        // create a new `Bar`
        Self { inner: false }
    }

    // `pub` (public) functions are accessible outside the module
    pub fn make_bar() -> Bar {
        Bar { inner: false }
    }

    // use `&self` to borrow an instance of `Bar`
    fn is_true(&self) -> bool {
        self.inner
    }

    // use `&mut self` to mutably borrow an instance of `Bar`
    fn make_true(&mut self) {
        self.inner = true;
    }

    // use `self` to move data out of `Bar`
    fn into_inner(self) -> bool {
        // `Bar` will be destroyed after returning `self.inner`
        self.inner
    }
}

let mut bar = Bar::new(); // make a new `Bar`
bar.make_true(); // change the inner value
assert_eq!(bar.is_true(), true); // get the inner value
let value = bar.into_inner(); // move the inner value out of `Bar`

// `bar` was moved into `bar.into_inner()` and can no longer be used


=======================================================
## TUPLES
=======================================================

// Tuples offer a way to group unrelated data into an anonymous data type. 
// Since tuples are anonymous, try to keep the number of elements limited to avoid ambiguities.

// create a new tuple named `tup` containing 4 pieces of data
let tup = ('a', 'b', 1, 2);

// tuple members are accessed by index
assert_eq!(tup.0, 'a');
assert_eq!(tup.1, 'b');
assert_eq!(tup.2, 1);
assert_eq!(tup.3, 2);
----------------------------------

// tuples can be destructured into individual variables
let (a, b, one, two) = (tup.0, tup.1, tup.2, tup.3);
let (a, b, one, two) = ('a', 'b', 1, 2);
// a, b, one, two now can be used as individual variables
----------------------------------

// tuple data types are just existing types surrounded by parentheses
fn double(point: (i32, i32)) -> (i32, i32) {
    (point.0 _ 2, point.1 _ 2)
}

=======================================================
## STRINGS
=======================================================

// Rust has only one string type in the core language, which is the string slice str that is usually seen in its borrowed form &str
// String literals, for example, are stored in the binary output of the program and are therefore string slices
let data = "initial contents";
let s = data.to_string();
-------------------------------------------

// the method also works on a literal directly:
let s = "initial contents".to_string();
let hello = String::from("Hello, world!");
-------------------------------------------

// You can append a char to a String with the push method, and append a &str with the push_str method:
let mut hello = String::from("Hello, ");
hello.push('w');
hello.push_str("orld!");
-------------------------------------------

let mut s = String::from("foo");
s.push_str("bar");

let mut s1 = String::from("foo");
let s2 = "bar";
s1.push_str(&s2);
println!("s2 is {}", s2);

let mut s = String::from("lo");
s.push('l');

let s1 = String::from("Hello, ");
let s2 = String::from("world!");
let s3 = s1 + &s2; // Note that s1 has been moved here and can no longer be used

let s1 = String::from("tic");
let s2 = String::from("tac");
let s3 = String::from("toe");
// format is same as println and doesn't take ownership
let s = format!("{}-{}-{}", s1, s2, s3);
-------------------------------------------

// If you have a vector of UTF-8 bytes, you can create a String from it with the from_utf8 method:
// some bytes, in a vector
let sparkle_heart = vec![240, 159, 146, 150];

// We know these bytes are valid, so we'll use `unwrap()`.
let sparkle_heart = String::from_utf8(sparkle_heart).unwrap();
assert_eq!("💖", sparkle_heart);
-------------------------------------------

// // `s` is ASCII which represents each `char` as one byte
let s = "hello";
assert_eq!(s.len(), 5);
-------------------------------------------

// A `char` array with the same contents would be longer because
// every `char` is four bytes
let s = ['h', 'e', 'l', 'l', 'o'];
let size: usize = s.into_iter().map(|c| mem::size_of_val(&c)).sum();
assert_eq!(size, 20);

-------------------------------------------

// Find first word example
fn first_word(s: &str) -> &str{
    let s_bytes = s.as_bytes();
    for (i, &val) in s_bytes.iter().enumerate() {
        if val == b' ' {
            return &s[..i];
        }
    }
    &s[..]
}

fn main(){
    let my_string = String::from("hello world");
    let f_word = first_word(&my_string);
    println!("first word: {}", f_word);

    // first_word works on slices of `String`s
    let word = first_word(&my_string[..]);
    println!("first word: {}", word);

    let my_string_literal = "hello world";
    // first_word works on slices of string literals
    let word = first_word(&my_string_literal[..]);
    println!("first word: {}", word);

    let word = first_word(my_string_literal);
    println!("first word: {}", word);

}

-------------------------------------
## STRING methods
-------------------------------------

1 new()
    -> pub const fn new()
    → String Creates a new empty String.
2 to_string()
    -> fn to_string(&self)
    → String Converts the given value to a String.
3 replace()
    -> pub fn replace<'a, P>(&'a self, from: P, to: &str)
    → String Replaces all matches of a pattern with another string.
4 as_str()
    -> pub fn as_str(&self)
    → &str Extracts a string slice containing the entire string.
5 push()
    -> pub fn push(&mut self, ch: char)
    -> Appends the given char to the end of this String.
6 push_str()
    -> pub fn push_str(&mut self, string: &str)
    -> Appends a given string slice onto the end of this String.
7 len()
    -> pub fn len(&self)
    → usize Returns the length of this String, in bytes.
8 trim()
    -> pub fn trim(&self)
    → &str Returns a string slice with leading and trailing whitespace removed.
9 split_whitespace()
    -> pub fn split_whitespace(&self)
    → SplitWhitespace Splits a string slice by whitespace and returns an iterator.
10 split()
    -> pub fn split<'a, P>(&'a self, pat: P)
    → Split<'a, P> , where P is pattern can be &str, char, or a closure that determines the split. Returns an iterator over substrings of this string slice, separated by characters matched by a pattern.
11 chars()
    -> pub fn chars(&self)
    → Chars Returns an iterator over the chars of a string slice.
12 as_bytes()
    -> convert into bytes.

-------------------------------------------
let s = "hello";
let third_character = s.chars().nth(2);
assert_eq!(third_character, Some('l'));
-------------------------------------------

let s = "hello";
assert_eq!(s.as_bytes()[0], 104);
assert_eq!(s.as_bytes()[0], b'h');
-------------------------------------------

===========================================
## ARRAYS
===========================================

// Arrays in Rust are fixed size. Most of the time you'll want to work with a slice or Vector, but arrays can be useful with fixed buffer sizes.

let array = [0; 3]; // array size 3, all elements initialized to 0
let array: [i32; 5] = [1, 2, 3, 4, 5];
let slice: &[i32] = &array[..];

// Arrays can be safely accessed using `.get`, which returns an
// `Option`. This can be matched as shown below, or used with
// `.expect()` if you would like the program to exit with a nice
// message instead of happily continue.

for i in 0..xs.len() + 1 { // OOPS, one element too far
    match xs.get(i) {
        Some(xval) => println!("{}: {}", i, xval),
        None => println!("Slow down! {} is too far!", i),
    }
}

===========================================
## SLICES
===========================================

// Slices are views into a chunk of contiguous memory. 
// They provide convenient high-performance operations for existing data.
// Slices are similar to arrays, but their length is not known at compile time.
// Instead, a slice is a two-word object, the first word is a pointer to the data, 
// and the second word is the length of the slice.

let mut nums = vec![1, 2, 3, 4, 5];
let num_slice = &mut nums[..]; // make a slice out of the Vector
num_slice.first(); // Some(&1)
num_slice.last(); // Some(&5)
num_slice.reverse(); // &[5, 4, 3, 2, 1]
num_slice.sort(); // &[1, 2, 3, 4, 5]

// get a view of "chunks" having 2 elements each
let mut chunks = num_slice.chunks(2);
chunks.next(); // Some(&[1, 2])
chunks.next(); // Some(&[3, 4])
chunks.next(); // Some(&[5])

===========================================
VECTOR
===========================================

// A vector is a dynamic or "growable" array, implemented as the standard library type
  
let v: Vec<i32> = Vec::new();
let v = vec![1, 2, 3]; // v: Vec<i32>

-------------------------------------------
// In addition, (mutable) vectors can grow automatically:
let mut nums = vec![1, 2, 3]; // mut nums: Vec<i32>
nums.push(4);
println!("The length of nums is now {}", nums.len()); // Prints 4

OR

let mut v = Vec::new();
v.push(5);
v.push(6);
v.push(7);
v.push(8);
-------------------------------------------

let mut v = vec![100, 32, 57];
for i in &mut v {
    \*i += 50;
    println!("{}", i);
}

#[derive(Debug)]
enum SpreadsheetCell {
    Int(i32),
    Text(String),
    Float(f64),
}

let v1 = vec![
    SpreadsheetCell::Int(45),
    SpreadsheetCell::Float(123.45),
    SpreadsheetCell::Text(String::from("Blue")),
];

for i in &v1 {
    println!("Spreadsheet data {:?}", i);
}

-------------------------------------------

// you might want to reference just one line of a file read into memory.
// By nature, a slice is not created directly, but from an existing variable.
let a = [0, 1, 2, 3, 4];
let middle = &a[1..4]; // A slice of a: just the elements 1, 2, and 3

for e in middle.iter() {
println!("{}", e); // Prints 1, 2, 3
}

-------------------------------------------
## ARRAY INBUIT FUNCTIONS
-------------------------------------------

array.into_iter()   - iterate by value
array.iter()        - iterate by reference

// iterates by value
// enumerate returns the tuple of index and value
array.array.into_iter().enumerate()     

for item in IntoIterator::into_iter(array) {}   - iterates by value
for item in array                               - Iterates by value
let x = [1, 2, 3];
let y = x.map(|v| v + 1);

-------------------------------------------
let y = x.map(|v| { temp += 1; v * temp });
assert_eq!(y, [1, 4, 9]);
-------------------------------------------
let x = ["Ferris", "Bueller's", "Day", "Off"];
let y = x.map(|v| v.len());
assert_eq!(y, [6, 9, 3, 3]);
-------------------------------------------
#![feature(array_try_map)]
let a = ["1", "2", "3"];
let b = a.try_map(|v| v.parse::<u32>()).unwrap().map(|v| v + 1);
assert_eq!(b, [2, 3, 4]);
-------------------------------------------

#![feature(array_zip)]
let x = [1, 2, 3];
let y = [4, 5, 6];
let z = x.zip(y);
assert_eq!(z, [(1, 4), (2, 5), (3, 6)]);
-------------------------------------------

array.as_ref(&self) -> &[T]ⓘ
Converts this type into a shared reference of the (usually inferred) input type.

============== ITERATOR ==============
let a = [1, 2, 3];
let mut iter = a.iter();

// A call to next() returns the next value...
assert_eq!(Some(&1), iter.next());
assert_eq!(Some(&2), iter.next());
assert_eq!(Some(&3), iter.next());

-------------------------------------------
// ... and then None once it's over.
assert_eq!(None, iter.next());
-------------------------------------------

#![feature(iter_next_chunk)]
let mut iter = "lorem".chars();
assert_eq!(iter.next_chunk().unwrap(), ['l', 'o']); // N is inferred as 2
assert_eq!(iter.next_chunk().unwrap(), ['r', 'e', 'm']); // N is inferred as 3
assert_eq!(iter.next_chunk::<4>().unwrap_err().as_slice(), &[]); // N is explicitly 4
-------------------------------------------

let quote = "not all those who wander are lost";
let [first, second, third] = quote.split_whitespace().next_chunk().unwrap();
assert_eq!(first, "not");
assert_eq!(second, "all");
assert_eq!(third, "those");
-------------------------------------------

// The even numbers in the range of zero to nine.
let iter = (0..10).filter(|x| x % 2 == 0);

-------------------------------------------
// We might iterate from zero to ten times. Knowing that it's five
// exactly wouldn't be possible without executing filter().
assert_eq!((0, Some(10)), iter.size_hint());

-------------------------------------------
// Let's add five more numbers with chain()
let iter = (0..10).filter(|x| x % 2 == 0).chain(15..20);

-------------------------------------------
---- fn count() --
// Consumes the iterator, counting the number of iterations and returning it.
// panic if total elements are more than usize:MAX
let a = [1, 2, 3];
assert_eq!(a.iter().count(), 3);

let a = [1, 2, 3, 4, 5];
assert_eq!(a.iter().count(), 5);

-------------------------------------------
----- last() ----
let a = [1, 2, 3];
assert_eq!(a.iter().last(), Some(&3));

let a = [1, 2, 3, 4, 5];
assert_eq!(a.iter().last(), Some(&5));

-------------------------------------------
----- advance_by() ---

let a = [1, 2, 3, 4];
let mut iter = a.iter();

assert_eq!(iter.advance_by(2), Ok(()));
assert_eq!(iter.next(), Some(&3));
assert_eq!(iter.advance_by(0), Ok(()));
assert_eq!(iter.advance_by(100), Err(1)); // only `&4` was skipped

-------------------------------------------
----- step_by() ----
let a = [0, 1, 2, 3, 4, 5];
let mut iter = a.iter().step_by(2);

assert_eq!(iter.next(), Some(&0));
assert_eq!(iter.next(), Some(&2));
assert_eq!(iter.next(), Some(&4));
assert_eq!(iter.next(), None);

-------------------------------------------
---- chain() -----
let a1 = [1, 2, 3];
let a2 = [4, 5, 6];

let mut iter = a1.iter().chain(a2.iter());

assert_eq!(iter.next(), Some(&1));
assert_eq!(iter.next(), Some(&2));
assert_eq!(iter.next(), Some(&3));
assert_eq!(iter.next(), Some(&4));
assert_eq!(iter.next(), Some(&5));
assert_eq!(iter.next(), Some(&6));
assert_eq!(iter.next(), None);

-------------------------------------------

let s1 = &[1, 2, 3];
let s2 = &[4, 5, 6];
let mut iter = s1.iter().chain(s2);

-------------------------------------------

let a1 = [1, 2, 3];
let a2 = [4, 5, 6];

let mut iter = a1.iter().zip(a2.iter());
assert_eq!(iter.next(), Some((&1, &4)));
assert_eq!(iter.next(), Some((&2, &5)));

-------------------------------------------

let line = "Some line of text for example";
let text = line.split(" ").nth(3).unwrap();
let text = line.split(" ").skip(3).next();
println!("{}", text);

-------------------------------------------

fn main() {
let line = "Some line of text for example";
let l = line.split(" ")
.enumerate()
.filter(|&(i, _)| i == 3 )
.map(|(_, e)| e);

    //.collect() can take all the values in an Iterator's stream and stick them into a Vec
    let lvec: Vec<&str> = l.collect();
    let text = &lvec[0];
    println!("{}", text);

## }

#![feature(iter_intersperse)]
//intersperse() - places seperator between array elements.
let hello = ["Hello", "World", "!"].iter().copied().intersperse(" ").collect::<String>();
assert_eq!(hello, "Hello World !");

-------------------------------------------
------ map() -----
// Takes a closure and creates an iterator which calls that closure on each element.
let a = [1, 2, 3];

let mut iter = a.iter().map(|x| 2 \* x);

assert_eq!(iter.next(), Some(2));
assert_eq!(iter.next(), Some(4));
assert_eq!(iter.next(), Some(6));
assert_eq!(iter.next(), None);

// If you’re doing some sort of side effect, prefer for to map():

// don't do this:
(0..5).map(|x| println!("{x}"));

// it won't even execute, as it is lazy. Rust will warn you about this.

// Instead, use for:
for x in 0..5 {
println!("{x}");
}

----------- for_each() ------------
// Calls a closure on each element of an iterator. break and continue are not possible from a closure

use std::sync::mpsc::channel;

let (tx, rx) = channel();
(0..5).map(|x| x \* 2 + 1)
.for_each(move |x| tx.send(x).unwrap());

let v: Vec<\_> = rx.iter().collect();
assert_eq!(v, vec![1, 3, 5, 7, 9]);

----------- filter() ------------
// Creates an iterator which uses a closure to determine if an element should be yielded.
let a = [0i32, 1, 2];
let mut iter = a.iter().filter(|x| x.is_positive());
assert_eq!(iter.next(), Some(&1));
assert_eq!(iter.next(), Some(&2));
assert_eq!(iter.next(), None);

// Because the closure passed to filter() takes a reference, and many iterators iterate over references, this leads to a possibly confusing situation, where the type of the closure is a double reference:

let a = [0, 1, 2];
let mut iter = a.iter().filter(|x| \**x > 1); // need two *s!
assert_eq!(iter.next(), Some(&2));
assert_eq!(iter.next(), None);

----------- enumerate() ------------

// Creates an iterator which gives the current iteration count as well as the next value.

// The iterator returned yields pairs (i, val), where i is the current index of iteration and val is the value returned by the iterator.

let a = ['a', 'b', 'c'];

let mut iter = a.iter().enumerate();

assert_eq!(iter.next(), Some((0, &'a')));
assert_eq!(iter.next(), Some((1, &'b')));
assert_eq!(iter.next(), Some((2, &'c')));
assert_eq!(iter.next(), None);

----------- take() ------------

let a = [1, 2, 3];
let mut iter = a.iter().take(2);
assert_eq!(iter.next(), Some(&1));
assert_eq!(iter.next(), Some(&2));
assert_eq!(iter.next(), None);

// take() is often used with an infinite iterator, to make it finite:

let mut iter = (0..).take(3);
assert_eq!(iter.next(), Some(0));
assert_eq!(iter.next(), Some(1));
assert_eq!(iter.next(), Some(2));
assert_eq!(iter.next(), None);

//If less than n elements are available, take will limit itself to the size of the underlying iterator:

let v = [1, 2];
let mut iter = v.into_iter().take(5);
assert_eq!(iter.next(), Some(1));
assert_eq!(iter.next(), Some(2));
assert_eq!(iter.next(), None);

----------- flat_map() ------------

let words = ["alpha", "beta", "gamma"];

// chars() returns an iterator
let merged: String = words.iter()
.flat_map(|s| s.chars())
.collect();
assert_eq!(merged, "alphabetagamma");

------------ flatten() --------------
// Creates an iterator that flattens nested structure.
let data = vec![vec![1, 2, 3, 4], vec![5, 6]];
let flattened = data.into_iter().flatten().collect::<Vec<u8>>();
assert_eq!(flattened, &[1, 2, 3, 4, 5, 6]);

-------------------------------------------
// Mapping and then flattening:

let words = ["alpha", "beta", "gamma"];
// chars() returns an iterator
let merged: String = words.iter()
.map(|s| s.chars())
.flatten()
.collect();
assert_eq!(merged, "alphabetagamma");

-------------------------------------------
// You can also rewrite this in terms of flat_map(), which is preferable in this case since it conveys intent more clearly:

let words = ["alpha", "beta", "gamma"];
// chars() returns an iterator
let merged: String = words.iter()
.flat_map(|s| s.chars())
.collect();
assert_eq!(merged, "alphabetagamma");

-------------------------------------------
------------ inspect() --------------
let a = [1, 4, 2, 3];

// this iterator sequence is complex.
let sum = a.iter()
.cloned()
.filter(|x| x % 2 == 0)
.fold(0, |sum, i| sum + i);

println!("{sum}");

// let's add some inspect() calls to investigate what's happening
let sum = a.iter()
.cloned()
.inspect(|x| println!("about to filter: {x}"))
.filter(|x| x % 2 == 0)
.inspect(|x| println!("made it through filter: {x}"))
.fold(0, |sum, i| sum + i);

println!("{sum}");

-------------------------------------------
------------ by_ref() --------------
// Borrows an iterator, rather than consuming it.
let mut words = ["hello", "world", "of", "Rust"].into_iter();

// Take the first two words.
let hello*world: Vec<*> = words.by_ref().take(2).collect();
assert_eq!(hello_world, vec!["hello", "world"]);

// Collect the rest of the words.
// We can only do this because we used `by_ref` earlier.
let of*rust: Vec<*> = words.collect();
assert_eq!(of_rust, vec!["of", "Rust"]);

------------ collect() --------------

// Transforms an iterator into a collection.
// collect() can take anything iterable, and turn it into a relevant collection. This is one of the more powerful methods in the standard library, used in a variety of contexts.

let a = [1, 2, 3];
let doubled: Vec<i32> = a.iter()
.map(|&x| x \* 2)
.collect();
assert_eq!(vec![2, 4, 6], doubled);

-------------------------------------------

let a = [1, 2, 3];
let doubled = a.iter().map(|x| x \* 2).collect::<Vec<i32>>();
assert_eq!(vec![2, 4, 6], doubled);

-------------------------------------------

let a = [1, 2, 3];
let doubled = a.iter().map(|x| x \* 2).collect::<Vec<\_>>();
assert_eq!(vec![2, 4, 6], doubled);

-------------------------------------------

let chars = ['g', 'd', 'k', 'k', 'n'];
let hello: String = chars.iter()
.map(|&x| x as u8)
.map(|x| (x + 1) as char)
.collect();
assert_eq!("hello", hello);

------- try_collect() -----

#![feature(iterator_try_collect)]

let u = vec![Some(1), Some(2), Some(3)];
let v = u.into_iter().try_collect::<Vec<i32>>();
assert_eq!(v, Some(vec![1, 2, 3]));
Failing to collect in the same way:

#![feature(iterator_try_collect)]

let u = vec![Some(1), Some(2), None, Some(3)];
let v = u.into_iter().try_collect::<Vec<i32>>();
assert_eq!(v, None);

------------ is_partitioned() --------------
// Checks if the elements of this iterator are partitioned according to the given predicate, such that all those that return true precede all those that return false.

#![feature(iter_is_partitioned)]

assert!("Iterator".chars().is_partitioned(char::is_uppercase));
assert!(!"IntoIterator".chars().is_partitioned(char::is_uppercase));

-------------- FOLD -------------

// iterator and fold
let a = [1, 2, 3];
let sum = a.iter().fold(0, |acc, elem| acc + elem);
assert_eq!(6, sum);

-------------------------------------------

// fold() can be combined with other adapters, but is typically the last call in a chain:
let a = [1, 2, 3, 4, 5];
let sum_of_even = a
.iter()
.filter(|elem| elem % 2 == 0)
.fold(0, |acc, elem| acc + elem);
assert_eq!(6, sum_of_even);

-------------------------------------------

let a = [1, 2, 3];
// the sum of all of the elements of the array
let sum = a.iter().fold(0, |acc, x| acc + x);
assert_eq!(sum, 6);

-------------------------------------------

let numbers = [1, 2, 3, 4, 5];
let zero = "0".to_string();
let result = numbers.iter().fold(zero, |acc, &x| {
format!("({acc} + {x})")
});
assert_eq!(result, "(((((0 + 1) + 2) + 3) + 4) + 5)");

-------------- REDUCE ----------

use reduce::Reduce;
fn main() {
// Reduce a non-empty iterator into Some(value)
let v = vec![1usize, 2, 3, 4, 5];
let sum
= v.into_iter().reduce(|a, b| a + b);
assert_eq!(Some(15), sum);

    // Reduce an empty iterator into None
    let v = Vec::<usize>::new();
    let sum = v.into_iter().reduce(|a, b| a + b);
    assert_eq!(None, sum);

## }

let reduced: i32 = (1..10).reduce(|acc, e| acc + e).unwrap();
assert_eq!(reduced, 45);
// Which is equivalent to doing it with `fold`:
let folded: i32 = (1..10).fold(0, |acc, e| acc + e);
assert_eq!(reduced, folded);

-------------------------------------------

//Safely calculate the sum of a series of numbers: #![feature(iterator_try_reduce)]
let numbers: Vec<usize> = vec![10, 20, 5, 23, 0];
let sum = numbers.into_iter().try_reduce(|x, y| x.checked_add(y));
assert_eq!(sum, Some(Some(58)));

-------------------------------------------

//Determine when a reduction short circuited: #![feature(iterator_try_reduce)]
let numbers = vec![1, 2, 3, usize::MAX, 4, 5];
let sum = numbers.into_iter().try_reduce(|x, y| x.checked_add(y));
assert_eq!(sum, None);

-------------------------------------------

//Determine when a reduction was not performed because there are no elements: #![feature(iterator_try_reduce)]
let numbers: Vec<usize> = Vec::new();
let sum = numbers.into_iter().try_reduce(|x, y| x.checked_add(y));
assert_eq!(sum, Some(None));

----------- all() -------

// Tests if every element of the iterator matches a predicate.
let a = [1, 2, 3];
assert!(a.iter().all(|&x| x > 0));
assert!(!a.iter().all(|&x| x > 2));

---

// Stopping at the first false:

let a = [1, 2, 3];
let mut iter = a.iter();
assert!(!iter.all(|&x| x != 2));

// we can still use `iter`, as there are more elements.
assert_eq!(iter.next(), Some(&3));

--------- any() -------

// Tests if any element of the iterator matches a predicate.
// Stopping at the first true:
let a = [1, 2, 3];
assert!(a.iter().any(|&x| x > 0));
assert!(!a.iter().any(|&x| x > 5));

--------- find() -------

// Searches for an element of an iterator that satisfies a predicate.
//find() takes a closure that returns true or false. It applies this closure to each element of the iterator, and if any of them return true, then find() returns Some(element). If they all return false, it returns None.

//find() is short-circuiting; in other words, it will stop processing as soon as the closure returns true.
// Basic usage:

let a = [1, 2, 3];
assert_eq!(a.iter().find(|&&x| x == 2), Some(&2));
assert_eq!(a.iter().find(|&&x| x == 5), None);

-------------------------------------------
//Stopping at the first true:
let a = [1, 2, 3];
let mut iter = a.iter();
assert_eq!(iter.find(|&&x| x == 2), Some(&2));

// we can still use `iter`, as there are more elements.
assert_eq!(iter.next(), Some(&3));

------- find_map() --------

// Applies function to the elements of iterator and returns the first non-none result.
// iter.find_map(f) is equivalent to iter.filter_map(f).next().

let a = ["lol", "NaN", "2", "5"];
let first_number = a.iter().find_map(|s| s.parse().ok());
assert_eq!(first_number, Some(2));

-------- max() && min() ----------

//Returns the maximum element of an iterator.
// Basic usage:

let a = [1, 2, 3];
let b: Vec<u32> = Vec::new();
assert_eq!(a.iter().max(), Some(&3));
assert_eq!(b.iter().max(), None);
assert_eq!(a.iter().min(), Some(&1));
assert_eq!(b.iter().min(), None);

assert_eq!(
[2.4, f32::NAN, 1.3]
    .into_iter()
    .reduce(f32::max)
    .unwrap(),
    2.4
);

-------- max_by_key() && max_by() ----------

// fn max_by_key()
// Returns the element that gives the maximum value from the specified function.
let a = [-3_i32, 0, 1, 5, -10];
assert_eq!(\*a.iter().max_by_key(|x| x.abs()).unwrap(), -10);

// fn max_by()
// Returns the element that gives the maximum value with respect to the specified comparison function.
let a = [-3_i32, 0, 1, 5, -10];
assert_eq!(\*a.iter().max_by(|x, y| x.cmp(y)).unwrap(), 5);

// similarly min_by_key() && min_by()

-------- rev() ----------

// reverses itereator
let a = [1, 2, 3];
let mut iter = a.iter().rev();
assert_eq!(iter.next(), Some(&3));
assert_eq!(iter.next(), Some(&2));
assert_eq!(iter.next(), Some(&1));

-------- unzip() ----------

let a = [(1, 2), (3, 4), (5, 6)];

let (left, right): (Vec<_>, Vec<_>) = a.iter().cloned().unzip();

assert_eq!(left, [1, 3, 5]);
assert_eq!(right, [2, 4, 6]);

// you can also unzip multiple nested tuples at once
let a = [(1, (2, 3)), (4, (5, 6))];

let (x, (y, z)): (Vec<_>, (Vec<_>, Vec<\_>)) = a.iter().cloned().unzip();
assert_eq!(x, [1, 4]);
assert_eq!(y, [2, 5]);
assert_eq!(z, [3, 6]);

-------- copied() ----------
// Creates an iterator which copies all of its elements.

let a = [1, 2, 3];

let v*copied: Vec<*> = a.iter().copied().collect();

// copied is the same as .map(|&x| x)
let v*map: Vec<*> = a.iter().map(|&x| x).collect();

assert_eq!(v_copied, vec![1, 2, 3]);
assert_eq!(v_map, vec![1, 2, 3]);

-------------------------------------------
-------- cloned() ----------
//Creates an iterator which clones all of its elements.
let a = [1, 2, 3];

let v*cloned: Vec<*> = a.iter().cloned().collect();

// cloned is the same as .map(|&x| x), for integers
let v*map: Vec<*> = a.iter().map(|&x| x).collect();

assert_eq!(v_cloned, vec![1, 2, 3]);
assert_eq!(v_map, vec![1, 2, 3]);

// To get the best performance, try to clone late:

let a = [vec![0_u8, 1, 2], vec![3, 4], vec![23]];
// don't do this:
let slower: Vec<_> = a.iter().cloned().filter(|s| s.len() == 1).collect();
assert_eq!(&[vec![23]], &slower[..]);
// instead call `cloned` late
let faster: Vec<_> = a.iter().filter(|s| s.len() == 1).cloned().collect();
assert_eq!(&[vec![23]], &faster[..]);

-------------------------------------------
-------- cycle() ----------
// repeat endlessly

-------- array_chunks(const N: usize) ----------
// Returns an iterator over N elements of the iterator at a time

#![feature(iter_array_chunks)]

let mut iter = "lorem".chars().array_chunks();
assert_eq!(iter.next(), Some(['l', 'o']));
assert_eq!(iter.next(), Some(['r', 'e']));
assert_eq!(iter.next(), None);
assert_eq!(iter.into_remainder().unwrap().as_slice(), &['m']);

-----> sum() <===========

let a = [1, 2, 3];
let sum: i32 = a.iter().sum();

assert_eq!(sum, 6);


-----> product() <===========

fn factorial(n: u32) -> u32 {
(1..=n).product()
}
assert_eq!(factorial(0), 1);
assert_eq!(factorial(1), 1);
assert_eq!(factorial(5), 120);

-----> cmp() <===========

// Lexicographically compares the elements of this Iterator with those of another.

Examples
use std::cmp::Ordering;

assert_eq!([1].iter().cmp([1].iter()), Ordering::Equal);
assert_eq!([1].iter().cmp([1, 2].iter()), Ordering::Less);
assert_eq!([1, 2].iter().cmp([1].iter()), Ordering::Greater);

-----> cmp_by() <===========
//Lexicographically compares the elements of this Iterator with those of another with respect to the specified comparison function.

// Basic usage: #![feature(iter_order_by)]

use std::cmp::Ordering;

let xs = [1, 2, 3, 4];
let ys = [1, 4, 9, 16];

assert_eq!(xs.iter().cmp_by(&ys, |&x, &y| x.cmp(&y)), Ordering::Less);
assert_eq!(xs.iter().cmp_by(&ys, |&x, &y| (x _ x).cmp(&y)), Ordering::Equal);
assert_eq!(xs.iter().cmp_by(&ys, |&x, &y| (2 _ x).cmp(&y)), Ordering::Greater);

-----> eq() <===========

// Determines if the elements of this Iterator are equal to those of another.

Examples
assert_eq!([1].iter().eq([1].iter()), true);
assert_eq!([1].iter().eq([1, 2].iter()), false);

-----> ne() <======
// not equal
assert_eq!([1].iter().ne([1].iter()), false);
assert_eq!([1].iter().ne([1, 2].iter()), true);

-----> lt() --> less than

// Determines if the elements of this Iterator are lexicographically less than those of another.

Examples
assert_eq!([1].iter().lt([1].iter()), false);
assert_eq!([1].iter().lt([1, 2].iter()), true);
assert_eq!([1, 2].iter().lt([1].iter()), false);
assert_eq!([1, 2].iter().lt([1, 2].iter()), false);

-----> le() -->
Determines if the elements of this Iterator are lexicographically less or equal to those of another.

Examples
assert_eq!([1].iter().le([1].iter()), true);
assert_eq!([1].iter().le([1, 2].iter()), true);
assert_eq!([1, 2].iter().le([1].iter()), false);
assert_eq!([1, 2].iter().le([1, 2].iter()), true);

-----> gt() && ge()

assert_eq!([1].iter().gt([1].iter()), false);
assert_eq!([1].iter().gt([1, 2].iter()), false);
assert_eq!([1, 2].iter().gt([1].iter()), true);
assert_eq!([1, 2].iter().gt([1, 2].iter()), false);

assert_eq!([1].iter().ge([1].iter()), true);
assert_eq!([1].iter().ge([1, 2].iter()), false);
assert_eq!([1, 2].iter().ge([1].iter()), true);
assert_eq!([1, 2].iter().ge([1, 2].iter()), true);

-----> is_sorted()
// Checks if the elements of this iterator are sorted.

assert!([1, 2, 2, 9].iter().is_sorted());
assert!(![1, 3, 2, 4].iter().is_sorted());
assert!([0].iter().is_sorted());
assert!(std::iter::empty::<i32>().is_sorted());
assert!(![0.0, 1.0, f32::NAN].iter().is_sorted());

-----> is_sorted_by()

assert!([1, 2, 2, 9].iter().is_sorted_by(|a, b| a.partial_cmp(b)));
assert!(![1, 3, 2, 4].iter().is_sorted_by(|a, b| a.partial_cmp(b)));
assert!([0].iter().is_sorted_by(|a, b| a.partial_cmp(b)));
assert!(std::iter::empty::<i32>().is_sorted_by(|a, b| a.partial_cmp(b)));
assert!(![0.0, 1.0, f32::NAN].iter().is_sorted_by(|a, b| a.partial_cmp(b)));

==========================================
HASHMAPS
==========================================
use std::collections::HashMap;

let mut scores = HashMap::new();

scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);


use std::collections::HashMap;

let teams = vec![String::from("Blue"), String::from("Yellow")];
let initial_scores = vec![10, 50];
let scores: HashMap<_, _> = teams.iter().zip(initial_scores.iter()).collect(); //zip creates tuple from two vectors

-------------------------------------------

HashMaps and Ownership

// For types that implement the Copy trait, like i32, the values are copied into the hash map.
// For owned values like String, the values will be moved and the hash map will be the owner of those
use std::collections::HashMap;

let field_name = String::from("Favorite color");
let field_value = String::from("Blue");

let mut map = HashMap::new();
map.insert(field_name, field_value);
// field_name and field_value are invalid at this point, try using them and

// fetching value
scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Yellow"), 50);
let team_name = String::from("Blue");
let score = scores.get(&team_name);

//iterating over hashmap
for (key, value) in &scores {
    println!("{}: {}", key, value);
}

// UPDATING HASHMAP
//=> updating to new value
scores.insert(String::from("Blue"), 10);
scores.insert(String::from("Blue"), 25);

//=> only insert if no key value
let mut scores = HashMap::new();
scores.insert(String::from("Blue"), 10);
scores.entry(String::from("Yellow")).or_insert(50);
scores.entry(String::from("Blue")).or_insert(50);
println!("{:?}", scores); //{"Yellow": 50, "Blue": 10}

//=> Updating a Value Based on the Old Value
use std::collections::HashMap;
let text = "hello world wonderful world";
let mut map = HashMap::new();
for word in text.split_whitespace() {
    let count = map.entry(word).or_insert(0);
    \*count += 1;
}
println!("{:?}", map); //{"world": 2, "hello": 1, "wonderful": 1}

---

## ITERATOR

// The Iterator trait provides a large amount of functionality for iterating over collections using combinators.

// create a new vector ...
let nums = vec![1, 2, 3, 4, 5];

// ... then turn it into an iterator and multiply each element by 3 ...
let tripled = nums.iter().map(|n| n \* 3);

// ... then filter out all the even numbers ...
let odds_only = tripled.filter(|n| n % 2 == 1);

// ... and finally collect the odd numbers into a new Vector
let new_vec: Vec<i32> = odds_only.collect(); // type annotation required

// same steps as above, but chaining it all together:
// create a new Vector
let nums = vec![1, 2, 3, 4, 5];
let tripled_odds_only = nums // take the `nums` vector
    .iter() // then turn it into an iterator
    .filter_map(|n| { // then perform a filter and map operation on each element
        let n = n \* 3; // multiply the element by 3
        if n % 2 == 1 {
            Some(n) // keep if odd
        } else {
            None // discard if even
        }
    })
    .collect::<Vec<i32>>(); // collect the remaining numbers into a Vector

// This example takes a vector of (x,y) points where all even indexes
// are the x-coordinates, and all odd indexes are y-coordinates and
// creates an iterator over tuples of the points.

// Points Vector: x, y, x, y, x, y, x, y, x, y
let points = vec![0, 0, 2, 1, 4, 3, 6, 5, 8, 7];

// `step_by` will skip every other index; iteration starts at index 0
let x = points.iter().step_by(2);

// use `skip` to skip 1 element so we start at index 1
// then skip every other index starting from index 1
let y = points.iter().skip(1).step_by(2);

// `zip` takes two iterators and generates a new one by taking
// alternating elements from each iterator. `enumerate` provides
// the iteration count as an index
let points = x.zip(y).enumerate();
for (i, point) in points {
println!("{i}: {point:?}");
// 0: (0, 0)
// 1: (2, 1)
// 2: (4, 3)
// 3: (6, 5)
// 4: (8, 7)
}

// create a new Vector
let nums = vec![1, 2, 3];
let sum = nums // take `nums`
.iter() // create an iterator
.sum::<i32>(); // add all elements together and return an i32
assert_eq!(sum, 6);

// common methods of lib
use std::ops::{Range, RangeInclusive};
assert_eq!((3..5), std::ops::Range { start: 3, end: 5 });
assert_eq!(3 + 4 + 5, (3..6).sum());

// The start..=end syntax is a RangeInclusive:q
assert_eq!((3..=5), std::ops::RangeInclusive::new(3, 5));
assert_eq!(3 + 4 + 5, (3..=5).sum());

---

## Various Attributes

// An attribute to hide warnings for unused code. #![allow(dead_code)]

#[derive(Debug)]

======================================
Generic Types, Traits, and Lifetimes
======================================

# ==================================

# ==================================


```
