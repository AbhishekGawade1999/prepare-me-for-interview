
### Basics
- ### Functions
	- A reusable code, can be inbuilt like print or imported using modules or can be written manually
	- `print("hello world")`
	- `print("x is", x)`
		- Output ==> x is 5
	- print(f"x is {x}")
		- Output ==> x is 5
- ### Literals
	- A
	- ![[Pasted image 20251125201100.png]]
	- B
	- ![](../Pasted%20image%2020251125201210.png)
	- Integers - 20/-20
	- Float - 0.1
	- Strings - "Abhishk"
	- Boolean - true/false || 0/1
- ### Operators
	- Arithmetic
		- Exponential
			- ** = `2**3`= 2ˆ3 = 8
		- Multiplication
			- `2*3`= 6
		- Division
			- `10/2`= 5
		- Floor Division
			- `5/2` = 2
		- Modulo
			- `4%2`= 0
			- `5%2`= 1
		- Plus & Minus
		- floor division = //
	- ![[Screenshot 2025-11-21 at 8.07.30 AM.png]]
- ### Variables
	- name = "Abhishek"
- ### Comments
	- `# comment goes here`
- ### Input
	- ![[Screenshot 2025-11-21 at 8.28.51 AM.png]]
	- ![[Screenshot 2025-11-21 at 8.30.16 AM.png]]
- ### String
	- `print("ha"*10)` ==> `hahahahahahahahahaha`
	- ![[Screenshot 2025-11-21 at 5.37.13 PM.png]]
- ### Comparison Operators:
	- ![[Screenshot 2025-11-21 at 5.41.38 PM.png]]

---
## Conditional Statements
- ### if/elif/else
```
if age > 1 && age <= 18:
	print("Age is: " + age + " Which is below 18")
elif age > 18 && age <= 50:
	print("Age is: " + age + " Which is middle age")
else:
	print("Age is: " + age + " Old Age")
```
- ### Loop
	- ### While
	```
	secret_number = 10
	guessed_number = int(input("Enter a number: "))
	
	while guessed_number != secret_number :
		guessed_number = int(input("Guess Again: "))
	else :
		print("You have finally guessed number right!!")
		
	```

- ### For
```
for i in range(0,10):
	print(i)
```
![[Screenshot 2025-11-21 at 6.42.05 PM.png]]

---
# Logic & Bitwise operator
- and
- or
- not
	- ![[Screenshot 2025-11-21 at 7.06.00 PM.png]]

---
# Lists
- `list = ["US", "UK", "IN"]`
- `print(list[0])` ==> US
- `list[0] = CN` == > `["CN", "UK", "IN"]`
- `del countries[1]` ==> `["CN", "IN"]`
- `print(list[-1])` ==> IN 
### List Methods
- ![[Screenshot 2025-11-21 at 8.28.24 PM.png]]![[Screenshot 2025-11-21 at 8.30.26 PM.png]]
- ![[Screenshot 2025-11-21 at 8.31.41 PM.png]]
- `list.sort()`
- `list.reverse()`
---
### Iterating Through For Loop
```
ages = [10, 20, 30, 40]

sum = 0

for age in ages:
	sum = sum + age
	
print(age)
```

### Enumerate
```
fruits = ["apple", "banana", "cherry"]

for index, fruit in enumerate(fruits):
    print(index, fruit)
```

```
0 apple
1 banana
2 cherry
```

### Slicing
```
letters = [1, 2, 3, 4, 5]
newLetters = letters[0:2] #==> [1,2]
```

### Check in list
`list = ['a', 'b', 'c', 'd']`
`print('a' in list)` ==> true
`print('a' not in list)` ==> false

### Find index of element
```
my_list = [0, 3, 4, 1, 2] print(my_list.index(1)) # ==>3
```


---
# Function
```
def sum(num1, num2):
	return num1 + num2
	
sum(5, 10)
```

- Parameters or variables defined in the function are scoped to that function only
```
num = 10

def square():
	print(num)
	
square()
```
==> This will print 10 because it looks for nearest declaration which is outside function

```
num = 10

def square():
	num = 20
	print(num)
	
square()
```
==> This will print 20, because it looks for nearest declaration which is inside function

If you want your function to define functional globally then use keyword global ==> `global num = 20`

---
## Tuples
- Lists are mutable, but tuples are not
- `tuple1 = (1,2,3)`
- `tuple1 = 1, 2, 3`
- Both can be used
- We can't modify it's data
- Usecase: Useful for storing constant data like configuration values, coordinates, or fixed options

---
## Dictionaries
```
usernames = {
	'Abhishek': 'abhishek123',
	'Gawade': 'gawade123'
}
```
- key: value pairs
- `usernames["Abhishek"]` ==> abhishek123
- `usernames.keys()` ==> will print all keys list
- `usernames.values()` ==> will print all values list
- `usernames.items()` ==> will print all items **Tuple**
### Modifying Dictionaries
- `usernames["Abhishek"] = "abhishekNew123"` ==> this will modify existing username
- `usernames.update({"prajakta": "prajakta123"})` ==> this will add new user
- `del usernames["Gawade"]` ==> this will delete key:value pair
- `usernames.clear()` ==> clears dictionary
- `usernames.popitem()` ==> Deletes last key-value pair
---
### List vs Tuples vs Set
- Please note, here Ordered means whatever order data was added in and not as sorting order

| Feature            | List                  | Tuple                 | Set                        |
|--------------------|-----------------------|-----------------------|----------------------------|
| Syntax             | `[1, 2, 3]`           | `(1, 2, 3)`           | `{1, 2, 3}`                |
| Ordered            | ✅ Yes                | ✅ Yes                | ❌ No (unordered)          |
| Mutable            | ✅ Yes (can change)   | ❌ No (immutable)     | ✅ Yes (can add/remove)    |
| Allows duplicates  | ✅ Yes                | ✅ Yes                | ❌ No (unique elements)    |
| Indexing           | ✅ Supported          | ✅ Supported          | ❌ Not supported           |
| Use case           | General collection    | Fixed collection      | Unique items, set ops      |

---
# Errors and Exceptions

```
try:
	print("abc")
Except e:
	print("Exception occured" + e)
```

Type of Exceptions: ![[Screenshot 2025-11-24 at 7.23.55 PM.png]]

Raise Exception - `raise ZeroVisionError`

---
## Internals
- Python is a interpretar language
- It takes the code & writes it line by line for machine
- Python (CPython) ==> It's python that was written in programming language C
- Cython ==> Translates python to C for fast execution
- Jython ==> Python written in java
---

# Some common python packages/modules for DevOps
- Ansible
- PyTest
- Docker SDK for Python
- Requests
- Paramiko (SSH & SFTP)
- TensorFlow / pyTorch
- Transformers
- Openai
- os
```
import os
print(os.getcwd())   # Shows current working directory
```

```
import os
os.chdir("/path/to/your/folder")   # Change to desired directory
print(os.getcwd())                 # Verify change
```
---
# Modules i.e custom packages

```
# my_module.py
def greet(name):
    return f"Hello, {name}!"

# main.py
import my_module

print(my_module.greet("Alice"))  # ✅ Works
```

- Import specific functions/classes from a module
```
# main.py
from my_module import greet

print(greet("Bob"))  # ✅ Works directly
```