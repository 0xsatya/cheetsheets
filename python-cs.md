# Python cheetcodes

```
      
Built In Functions
------------------------------------
print()
id(variable) - gives address of variable.
len(obj) - length of string or array.
str(x) - Converts object x to a string representation.
bool(x) - converts in True or False.
repr(x) - Converts object x to an expression string.
eval(str) - Evaluates a string and returns an object.
tuple(s) - Converts s to a tuple.
list(s) - Converts s to a list.
set(s) - Converts s to a set.
dict(d) - Creates a dictionary. d must be a sequence of (key,value) tuples.
frozenset(s) - Converts s to a frozen set.
chr(x) - Converts an integer to a character.
print (r'C:\\nowhere') - C:\\nowhere
bin(5) = binary representation of number. = '0b101'
int('0b101', 2) = 5
--------------------------------------------------------
Built in Methods
---------------------------
-methods starts with ex .method_name()
-they are different fromo functions
-Ex. str.split(), .trim()
-in detail STRING INBUILY METHODS heading

---------------------------
a = b = c = 1
a, b, c = 1, 2, "john"

Python has five standard data types −
	Numbers
	String
	List
	Tuple
	Dictionary

#Delete reference of variable
del var
del var_a, var_b
---------------------------------
variables-
-it should in snake_case
-its case sensitive
-dont overwrite keywords of python in variable
----------------------------------
----Variable Scope----
local
parent
global
python inbuilt
----------------------

#augmented assingnment operator
x += 2;
------------------------------------

###########################################################
datatypes- 8
int, float, bool, str, list, tuple, set, dict
############################################################
-- Math Functions --
round(4.5)
abs(-20) = 20

############################################################

---Strings---
---------------
str = 'Hello World!'
str[start, stop, stepover]

print (str)          # Prints complete string
print (str[0])       # Prints first character of the string
print (str[2:5])     # Prints characters starting from 3rd to 5th
print (str[2:])      # Prints string starting from 3rd character
print (str * 2)      # Prints string two times
print (str + "TEST") # Prints concatenated string

Results
---------------
Hello World!
H
llo
llo World!
Hello World!Hello World!
Hello World!TEST
------------------
long_string = '''
Hello
words
'''
#strings are immutable
- str[3] = 4 => will give error

#Functions of Stings
------------------------------
len(str)
format()
split()
join()
format_map()
upper()
lower()
replace()
find()
translate()
encode()		is used to encode the string using the provided encoding.
count()			Python String count() function returns the number of occurrences of a substring in the given string.
startswith()	Python string startswith() function returns True if the string starts with the given prefix, otherwise it returns False.
endswith()		Python string endswith() function returns True if the string ends with the given suffix, otherwise it returns False.
capitalize()	Python String capitalize() function returns the capitalized version of the string.
center()		Python string center() function returns a centered string of specified size.
casefold()		Python string casefold() function returns a casefolded copy of the string. This function is used to perform case-insensitive string comparison.
expandtabs()	Python string expandtabs() function returns a new string with tab characters (\t) replaced with one or more whitespaces.
index()			Python String index() function returns the lowest index where the specified substring is found.
__contains__()	Python String class has __contains__() function that we can use to check if it contains another string or not. We can also use “in” operator to perform this check.


###########################################################
---while loops---
while condition:
	print---
else: #only if loop is not ending with break; statement
	print----

--- for loop ---
fruits = ["apple", "banana", "cherry"]
for x in fruits:
  print(x)
 
--- loop in string ---
for x in "banana":
  print(x)

--- loop in range ---
for x in range(6):
  print(x)
  
for x in range(2, 6):
  print(x)

for x in range(2, 30, 3): // loop with increment of 3 //default loop with 1.
  print(x)
  
--- do sth when loop ends ---
or x in range(6):
  print(x)
else:
  print("Finally finished!")

--- if dont want to do anything ---
for x in [0, 1, 2]:
  pass


--- USING FILTER Function---
def isOfLengthFour(strObj):
    if len(strObj) == 2:
        return True
    else:
        return False
 
def main():
    # List of string
    listOfStr = ['hi', 'this' , 'is', 'a', 'very', 'simple', 'string' , 'for', 'us']
    filteredList = list(filter(isOfLengthFour , listOfStr))
 
###########################################################
#List
----------------
list = [ 'abcd', 786 , 2.23, 'john', 70.2 ]
tinylist = [123, 'john']

print (list)          # Prints complete list
print (list[0])       # Prints first element of the list
print (list[1:3])     # Prints elements starting from 2nd till 3rd 
print (list[2:])      # Prints elements starting from 3rd element
print (tinylist * 2)  # Prints list two times
print (list + tinylist) # Prints concatenated lists

This produces the following result −

['abcd', 786, 2.23, 'john', 70.200000000000003]
abcd
[786, 2.23]
[2.23, 'john', 70.200000000000003]
[123, 'john', 123, 'john']
['abcd', 786, 2.23, 'john', 70.200000000000003, 123, 'john']

---list operations -----
del list[2] - delete value
len([1, 2, 3]) =	3	Length
[1, 2, 3] + [4, 5, 6] ==	[1, 2, 3, 4, 5, 6]	Concatenation
['Hi!'] * 4 =	['Hi!', 'Hi!', 'Hi!', 'Hi!']	Repetition
3 in [1, 2, 3]	= True	Membership
for x in [1,2,3] : print (x,end = ' ') =	1 2 3	Iteration

---list functions ------
len(list)
max(list) - max value
min(list) - min value
list(seq) - converts a tuple into list.
sorted(list) = produces new copy of array 

---list methods ---------
list.append(obj) - 
lsit.count(obj) - how many times obj occurs
list.extend(seq)
list.index(obj) , or list.index('x', 0, 4)
list.insert(index, obj) - inserts object into list at offset index
list.pop(obj=list[-1]) removes and returns last obj
list.remove(obj) - removes obj from list.
list.reverse() - reverses objects of list in place.
list.sort([func]) - sorts obj of list, use compare func if given.
list.copy() - returns copy of array
list(range(0,100))
' '.join(list) = returns string from list.
print('abcd' in list)
---list unpacking ------------
a, b, c, *other, d = [1,2,3,4,5,6,7,8,9,11]
=> a=1, b=2, c=3, other =[4,5,6,7,8,9], d=11


###########################################################
#Tuple
----------------------
- similar to list but these are immutable 
- it can't be sorted or reverses
- faster than list if not required to be changed.
- use it when not required to be changed

tuple = ( 'abcd', 786 , 2.23, 'john', 70.2  )
tinytuple = (123, 'john')

print (tuple)           # Prints complete tuple
print (tuple[0])        # Prints first element of the tuple
print (tuple[1:3])      # Prints elements starting from 2nd till 3rd 
print (tuple[2:])       # Prints elements starting from 3rd element
print (tinytuple * 2)   # Prints tuple two times
print (tuple + tinytuple) # Prints concatenated tuple
This produces the following result −

('abcd', 786, 2.23, 'john', 70.200000000000003)
abcd
(786, 2.23)
(2.23, 'john', 70.200000000000003)
(123, 'john', 123, 'john')
('abcd', 786, 2.23, 'john', 70.200000000000003, 123, 'john')

---Operation on tuple -------
tup1 = () - empty tuple
tup1 = (50,) - comma even if one element.
tup3 = tup1 + tup2 - updaes tuple
tup1[0] =100 - NOT VALID
del tup1 - deletes whole tuple.

---Indexing , Slicing, Matrixes ------
T=('C++', 'Java', 'Python')
T[2]	= 'Python'	Offsets start at zero
T[-2]	= 'Java'	Negative: count from the right
T[1:]	= ('Java', 'Python')	Slicing fetches sections

---Inbuilt Functions ------
cmp(tuple1, tuple2) - Compares elements of both tuples.
len(tuple) - Gives the total length of the tuple.
max(tuple) - Returns item from the tuple with max value.
min(tuple) - Returns item from the tuple with min value.
tuple(seq) - Converts a list into tuple.



###############################################################
#Dictionary
-----------------------
dict = {}
dict['one'] = "This is one"
dict[2]     = "This is two"

tinydict = {'name': 'john','code':6734, 'dept': 'sales'}

print (dict['one'])       # Prints value for 'one' key
print (dict[2])           # Prints value for 2 key
print (tinydict)          # Prints complete dictionary
print (tinydict.keys())   # Prints all the keys
print (tinydict.values()) # Prints all the values
This produces the following result −

Result--
This is one
This is two
{'name': 'john', 'dept': 'sales', 'code': 6734}
dict_keys(['name', 'dept', 'code'])
dict_values(['john', 'sales', 6734])

---Updating Dict------
dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}
dict['Age'] = 8; # update existing entry
dict['School'] = "DPS School" # Add new entry

--Deleting Dict------
dict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}

del dict['Name'] # remove entry with key 'Name'
dict.clear()     # remove all entries in dict
del dict         # delete entire dictionary

--Properties---
(a) More than one entry per key is not allowed
(b) Keys must be immutable. This means you can use strings, numbers or tuples as dictionary keys but something like ['key'] is not allowed.

---Function & Description---
cmp(dict1, dict2) 	- No longer available in Python 3.
len(dict) 			- Gives the total length of the dictionary. 
str(dict) 			- Produces a printable string representation of a dictionary
type(variable) 		- Returns the type of the passed variable. If passed variable is dictionary, then it would return a dictionary type.

---Method & Description---
dict.clear() 	- Removes all elements of dictionary dict
dict.copy() 	- Returns a shallow copy of dictionary dict
dict.fromkeys() - Create a new dictionary with keys from seq and values set to value.
dict.get(key, default=None) - For key key, returns value or default if key not in dictionary
dict.has_key(key) 	- Removed, use the in operation instead.
dict.items() 		- Returns a list of dict's (key, value) tuple pairs
dict.keys() 		- Returns list of dictionary dict's keys
dict.setdefault(key, default = None) - Similar to get(), but will set dict[key] = default if key is not already in dict
dict.update(dict2) 	- Adds dictionary dict2's key-values pairs to dict
dict.values() 		- Returns list of dictionary dict's values

##############################################################
---SETS---

- doesn't support indexes

my_set = {1,2,3,4,5} - unique value of set
set(my_list) - remove duplicates and convert into set
my_set.copy()
my_set.clear() - clears all values

my_set = set()
my_set.add(1)  # {1}
my_set.add(100)# {1, 100}
my_set.add(100)# {1, 100} --> no duplicates!
new_list = [1,2,3,3,3,4,4,5,6,1]
set(new_list)           # {1, 2, 3, 4, 5, 6}

my_set.remove(100)      # {1} --> Raises KeyError if element not found
my_set.discard(100)     # {1} --> Doesn't raise an error if element not found
my_set.clear()          # {}

new_set = {1,2,3}.copy()# {1,2,3}
set1 = {1,2,3}
set2 = {3,4,5}
set3 = set1.union(set2)               # {1,2,3,4,5}
set4 = set1.intersection(set2)        # {3}
set5 = set1.difference(set2)          # {1, 2}
set6 = set1.symmetric_difference(set2)# {1, 2, 4, 5}
set1.issubset(set2)                   # False
set1.issuperset(set2)                 # False
set1.isdisjoint(set2)                 # False --> return True if two sets have a null intersection.

##############################################################
---OPERATORS
-------------
Logical Operators
AND NOT

Membership operator
in, not in

Identity Operators
is, is not

Terniary Operators
is_frient = True
can_message = "message allowe" if is_friend else "not allowe to message"


------RANGE------
if x in range(1,10): //will check for 	1,2,3....,9 //10 is not included

for x in range(0,10):
	print(number)
for _ in range(0,10):
	print(_)
	
list(range(10))

for i, char in enumerate('Hellooo'):
	print(i, char)


STRING INBUILY METHODS
---------------------------------------------------------
capitalize() 									- Capitalizes first letter of string
center(width, fillchar) 						- Returns a string padded with fillchar with the original string centered to a total of width columns.
count(str, beg = 0,end = len(string)) 			- Counts how many times str occurs in string or in a substring of string if starting index beg and ending index end are given.
decode(encoding = 'UTF-8',errors = 'strict') 	- Decodes the string using the codec registered for encoding. encoding defaults to the default string encoding.
encode(encoding = 'UTF-8',errors = 'strict') 	- Returns encoded string version of string; on error, default is to raise a ValueError unless errors is given with 'ignore' or 'replace'.
endswith(suffix, beg = 0, end = len(string))	- Determines if string or a substring of string (if starting index beg and ending index end are given) ends with suffix; &returns true, false.
expandtabs(tabsize = 8) 						- Expands tabs in string to multiple spaces; defaults to 8 spaces per tab if tabsize not provided.
find(str, beg = 0, end = len(string)) 			- Determine if str occurs in string or in a substring of string returns index if found and -1 otherwise.
index(str, beg = 0, end = len(string)) 			- Same as find(), but raises an exception if str not found.

isalnum() 	- Returns true if string has at least 1 character and all characters are alphanumeric and false otherwise.
isalpha() 	- Returns true if string has at least 1 character and all characters are alphabetic and false otherwise.
isdigit() 	- Returns true if string contains only digits and false otherwise.
islower() 	- Returns true if string has at least 1 cased character and all cased characters are in lowercase and false otherwise.
isnumeric() - Returns true if a unicode string contains only numeric characters and false otherwise.
isspace()	- Returns true if string contains only whitespace characters and false otherwise.
istitle() 	- Returns true if string is properly "titlecased" and false otherwise.
isupper() 	- Returns true if string has at least one cased character and all cased characters are in uppercase and false otherwise.
join(seq) 	- Merges (concatenates) the string representations of elements in sequence seq into a string, with separator string.
len(string) - Returns the length of the string
ljust(width[, fillchar]) - Returns a space-padded string with the original string left-justified to a total of width columns.
lower() 	- Converts all uppercase letters in string to lowercase.
lstrip() 	- Removes all leading whitespace in string.
maketrans() - Returns a translation table to be used in translate function.
max(str) 	- Returns the max alphabetical character from the string str.
min(str) 	- Returns the min alphabetical character from the string str.

replace(old, new [, max]) 					- Replaces all occurrences of old in string with new or at most max occurrences if max given.
rfind(str, beg = 0,end = len(string)) 		- Same as find(), but search backwards in string.
rindex( str, beg = 0, end = len(string)) 	- Same as index(), but search backwards in string.
rjust(width,[, fillchar]) 					- Returns a space-padded string with the original string right-justified to a total of width columns.
rstrip() 									- Removes all trailing whitespace of string.
split(str="", num=string.count(str)) 		- Splits string according to delimiter str (space if not provided) and returns list of substrings; split into at most num substrings if given.
splitlines( num=string.count('\n')) 		- Splits string at all (or num) NEWLINEs and returns a list of each line with NEWLINEs removed.
startswith(str, beg=0,end=len(string))		-  Determines if string or a substring of string (if starting index beg and ending index end are given) starts with substring str;
translate(table, deletechars="") 			- Translates string according to translation table str(256 chars), removing those in the del string.
strip([chars]) 								- Performs both lstrip() and rstrip() on string

swapcase() 			- Inverts case for all letters in string.
title() 			- Returns "titlecased" version of string, that is, all words begin with uppercase and the rest are lowercase.

upper() 			- Converts lowercase letters in string to uppercase.
zfill (width) 		- Returns original string leftpadded with zeros to a total of width characters; intended for numbers, zfill() retains any sign given (less one zero).
isdecimal() 		- Returns true if a unicode string contains only decimal characters and false otherwise.



##################################################################
---LAMBDA Function---
# Function definition is here
sum = lambda arg1, arg2: arg1 + arg2

# Now you can call sum as a function
print ("Value of total : ", sum( 10, 20 ))
print ("Value of total : ", sum( 20, 20 ))

##################################################################
--Import Modules----
	import module1[, module2[,... moduleN]
Ex-
	import support
# Now you can call defined function that module as follows
	support.print_func("Zara")

or  specific attribute from module1
	from modname import name1[, name2[, ... nameN]]



##################################################################
---Setting environment variable The PYTHONPATH Variable ----

The PYTHONPATH is an environment variable, consisting of a list of directories. The syntax of PYTHONPATH is the same as that of the shell variable PATH.

Here is a typical PYTHONPATH from a Windows system −
	set PYTHONPATH = c:\python34\lib;
And here is a typical PYTHONPATH from a UNIX system −
	set PYTHONPATH = /usr/local/lib/python

##################################################################
dir() - built-in function returns a sorted list of strings containing the names defined by a module.

globals() and locals() - functions can be used to return the names in the global and local namespaces depending on the location from where they are called.

reload(module_name)

##################################################################
---FILE OPERATIONS----
fo = open("foo.txt", "wb")
print ("Name of the file: ", fo.name)
print ("Closed or not : ", fo.closed)
print ("Opening mode : ", fo.mode)
fo.close()
------
fo = open("foo.txt", "w")
fo.write( "Python is a great language.\nYeah its great!!\n")
fo.close()
------Renaming and Deleting--
import os
os.rename( "test1.txt", "test2.txt" )
os.remove("text2.txt") - Delete existing file.
os.chdir("newdir")
os.mkdir("newdir")
os.getcwd()
os.rmdir('dirname') - deletes directory



##################################################################
--- Exception Handling ----
Exception 		- Base class for all exceptions
StopIteration 	- Raised when the next() method of an iterator does not point to any object.
SystemExit 		- Raised by the sys.exit() function.
StandardError 	- Base class for all built-in exceptions except StopIteration and SystemExit.
ArithmeticError - Base class for all errors that occur for numeric calculation.
OverflowError 	- Raised when a calculation exceeds maximum limit for a numeric type.
FloatingPointError 	- Raised when a floating point calculation fails.
ZeroDivisonError 	- Raised when division or modulo by zero takes place for all numeric types.
AssertionError 		- Raised in case of failure of the Assert statement.
AttributeError		- Raised in case of failure of attribute reference or assignment.
EOFError 			- Raised when there is no input from either the raw_input() or input() function and the end of file is reached.
ImportError 		- Raised when an import statement fails.
KeyboardInterrupt 	- Raised when the user interrupts program execution, usually by pressing Ctrl+c.
LookupError 		- Base class for all lookup errors.
IndexError 			- Raised when an index is not found in a sequence.
KeyError 			- Raised when the specified key is not found in the dictionary.
NameError - Raised when an identifier is not found in the local or global namespace.
UnboundLocalError - Raised when trying to access a local variable in a function or method but no value has been assigned to it.
EnvironmentError - Base class for all exceptions that occur outside the Python environment.
IOError - Raised when an input/ output operation fails, such as the print statement or the open() function  when trying to open a file that does not exist.
OSError - Raised for operating system-related errors.
SyntaxError - Raised when there is an error in Python syntax.
IndentationError - Raised when indentation is not specified properly.
SystemError - Raised when the interpreter finds an internal problem, but when this error is encountered the Python interpreter does not exit.
SystemExit - Raised when Python interpreter is quit by using the sys.exit() function. If not handled in the code, causes the interpreter to exit.
TypeError - Raised when an operation or function is attempted that is invalid for the specified data type.
ValueError - Raised when the built-in function for a data type has the valid type of arguments, but the arguments have invalid values specified.
RuntimeError- Raised when a generated error does not fall into any category.
NotImplementedError - Raised when an abstract method that needs to be implemented in an inherited class is not actually implemented.


-----------TRY EXCEPT-----------
try:
   You do your operations here
   ......................
except ExceptionI or '':
   If there is ExceptionI, then execute this block.
except ExceptionII:
   If there is ExceptionII, then execute this block.
   ......................
else:
   If there is no exception then execute this block. 

----------
try:
   You do your operations here;
   ......................
   Due to any exception, this may be skipped.
finally:
   This would always be executed.
   ......................
   
-----------

##################################################################
----CREATING CLASSES-----------
class Employee:
   'Common base class for all employees'
   empCount = 0

   def __init__(self, name, salary):
      self.name = name
      self.salary = salary
      Employee.empCount += 1
   
   def displayCount(self):
     print ("Total Employee %d" % Employee.empCount)

   def displayEmployee(self):
      print ("Name : ", self.name,  ", Salary: ", self.salary)
	  
emp1 = Employee("Zara", 2000)
-----inbuilt attributes----
hasattr(emp1, 'salary')    # Returns true if 'salary' attribute exists
getattr(emp1, 'salary')    # Returns value of 'salary' attribute
setattr(emp1, 'salary', 7000) # Set attribute 'salary' at 7000
delattr(emp1, 'salary')    # Delete attribute 'salary'
------built in class attributes----
print ("Employee.__doc__:", Employee.__doc__)
print ("Employee.__name__:", Employee.__name__)
print ("Employee.__module__:", Employee.__module__)
print ("Employee.__bases__:", Employee.__bases__)
print ("Employee.__dict__:", Employee.__dict__ )

------INHERITANCE--------
class A:        # define your class A
class B:         # define your calss B
class C(A, B):   # subclass of A and B
------
issubclass(sub, sup)  	- boolean function returns True, if the given subclass sub is indeed a subclass of the superclass sup.

isinstance(obj, Class) - boolean function returns True, if obj is an instance of class Class or is an instance of a subclass of Class

-----OVERRIDING-----
class Parent:        # define parent class
   def myMethod(self):
      print ('Calling parent method')

class Child(Parent): # define child class
   def myMethod(self):
      print ('Calling child method')

c = Child()          # instance of child
c.myMethod()         # child calls overridden method

------OVERLOADING-----
class Vector:
   def __init__(self, a, b):
      self.a = a
      self.b = b

   def __str__(self):
      return 'Vector (%d, %d)' % (self.a, self.b)
   
   def __add__(self,other):
      return Vector(self.a + other.a, self.b + other.b)

v1 = Vector(2,10)
v2 = Vector(5,-2)
print (v1 + v2)

-----DATA HIDING------
class JustCounter:
   __secretCount = 0
  
   def count(self):
      self.__secretCount += 1
      print (self.__secretCount)

counter = JustCounter()
counter.count()
counter.count()
print (counter.__secretCount)



##################################################################
--------Regular Expression------
https://www.tutorialspoint.com/python3/python_reg_expressions.htm


##################################################################
----CGI PROGRAMING---
#Here is small CGI program to list out all the CGI variables

import os

print ("Content-type: text/html\r\n\r\n");
print ("<font size=+1>Environment</font><\br>");
for param in os.environ.keys():
   print ("<b>%20s</b>: %s<\br>" % (param, os.environ[param]))

Calling -
http://www.test.com/cgi-bin/hello.py?key1=value1&key2=value2

# Import modules for CGI handling 
import cgi, cgitb 

# Create instance of FieldStorage 
form = cgi.FieldStorage() 

# Get data from fields
first_name = form.getvalue('first_name')
last_name  = form.getvalue('last_name')

print "Content-type:text/html\r\n\r\n"
print "<html>"
print "<head>"
print "<title>Hello - Second CGI Program</title>"
print "</head>"
print "<body>"
print "<h2>Hello %s %s</h2>" % (first_name, last_name)
print "</body>"
print "</html>"

-----Setting up Cookies---
#!/usr/bin/python
print "Set-Cookie:UserID = XYZ;\r\n"
print "Set-Cookie:Password = XYZ123;\r\n"
print "Set-Cookie:Expires = Tuesday, 31-Dec-2007 23:12:40 GMT;\r\n"
print "Set-Cookie:Domain = www.tutorialspoint.com;\r\n"
print "Set-Cookie:Path = /perl;\n"
print "Content-type:text/html\r\n\r\n"
...........Rest of the HTML Content....

-----Retrieving Cookies------
# Import modules for CGI handling 
from os import environ
import cgi, cgitb

if environ.has_key('HTTP_COOKIE'):
   for cookie in map(strip, split(environ['HTTP_COOKIE'], ';')):
      (key, value ) = split(cookie, '=');
      if key == "UserID":
         user_id = value

      if key == "Password":
         password = value

print "User ID  = %s" % user_id
print "Password = %s" % password

------- MySQL database "TESTDB"------
import pymysql

# Open database connection
db = pymysql.connect("localhost","testuser","test123","TESTDB" )

# prepare a cursor object using cursor() method
cursor = db.cursor()

# execute SQL query using execute() method.
cursor.execute("SELECT VERSION()")

# Fetch a single row using fetchone() method.
data = cursor.fetchone()
print ("Database version : %s " % data)
db.close()

-----SQL INSERT----
import pymysql

# Open database connection
db = pymysql.connect("localhost","testuser","test123","TESTDB" )

# prepare a cursor object using cursor() method
cursor = db.cursor()

# Prepare SQL query to INSERT a record into the database.
sql = "INSERT INTO EMPLOYEE(FIRST_NAME, \
   LAST_NAME, AGE, SEX, INCOME) \
   VALUES ('%s', '%s', '%d', '%c', '%d' )" % \
   ('Mac', 'Mohan', 20, 'M', 2000)
try:
   # Execute the SQL command
   cursor.execute(sql)
   # Commit your changes in the database
   db.commit()
except:
   # Rollback in case there is any error
   db.rollback()

# disconnect from server
db.close()

----READ OPERATIONS----

import pymysql

# Open database connection
db = pymysql.connect("localhost","testuser","test123","TESTDB" )

# prepare a cursor object using cursor() method
cursor = db.cursor()

# Prepare SQL query to INSERT a record into the database.
sql = "SELECT * FROM EMPLOYEE \
      WHERE INCOME > '%d'" % (1000)
try:
   # Execute the SQL command
   cursor.execute(sql)
   # Fetch all the rows in a list of lists.
   results = cursor.fetchall()
   for row in results:
      fname = row[0]
      lname = row[1]
      age = row[2]
      sex = row[3]
      income = row[4]
      # Now print fetched result
      print ("fname = %s,lname = %s,age = %d,sex = %s,income = %d" % \
         (fname, lname, age, sex, income ))
except:
   print ("Error: unable to fetch data")

# disconnect from server
db.close()

--------------
db.commit();
db.rollback();
db.close();


##################################################################

----Simple Server----write internal servers---
import socket                                         

# create a socket object
serversocket = socket.socket(
	        socket.AF_INET, socket.SOCK_STREAM) 

# get local machine name
host = socket.gethostname()                           

port = 9999                                           

# bind to the port
serversocket.bind((host, port))                                  

# queue up to 5 requests
serversocket.listen(5)                                           

while True:
   # establish a connection
   clientsocket,addr = serversocket.accept()      

   print("Got a connection from %s" % str(addr))
    
   msg = 'Thank you for connecting'+ "\r\n"
   clientsocket.send(msg.encode('ascii'))
   clientsocket.close()
   
   
----Simple Client-----
import socket

# create a socket object
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 

# get local machine name
host = socket.gethostname()                           

port = 9999

# connection to hostname on the port.
s.connect((host, port))                               

# Receive no more than 1024 bytes
msg = s.recv(1024)                                     

s.close()
print (msg.decode('ascii'))

---OUTPUT----
# Following would start a server in background.
$ python server.py & 

# Once server is started run client as follows:
$ python client.py



##################################################################
----THREADING HANDLING-----
 import threading
import time

exitFlag = 0

class myThread (threading.Thread):
   def __init__(self, threadID, name, counter):
      threading.Thread.__init__(self)
      self.threadID = threadID
      self.name = name
      self.counter = counter
   def run(self):
      print ("Starting " + self.name)
      print_time(self.name, self.counter, 5)
      print ("Exiting " + self.name)

def print_time(threadName, delay, counter):
   while counter:
      if exitFlag:
         threadName.exit()
      time.sleep(delay)
      print ("%s: %s" % (threadName, time.ctime(time.time())))
      counter -= 1

# Create new threads
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)

# Start new Threads
thread1.start()
thread2.start()
thread1.join()
thread2.join()
print ("Exiting Main Thread")


---OUTPUT----
Starting Thread-1
Starting Thread-2
Thread-1: Fri Feb 19 10:00:21 2016
Thread-2: Fri Feb 19 10:00:22 2016
Thread-1: Fri Feb 19 10:00:22 2016
Thread-1: Fri Feb 19 10:00:23 2016
Thread-2: Fri Feb 19 10:00:24 2016
Thread-1: Fri Feb 19 10:00:24 2016
Thread-1: Fri Feb 19 10:00:25 2016
Exiting Thread-1
Thread-2: Fri Feb 19 10:00:26 2016
Thread-2: Fri Feb 19 10:00:28 2016
Thread-2: Fri Feb 19 10:00:30 2016
Exiting Thread-2
Exiting Main Thread



```
