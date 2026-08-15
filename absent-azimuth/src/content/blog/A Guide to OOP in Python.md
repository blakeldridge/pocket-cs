---
title: 'OOP in Python'
description: 'An comprehensive guide to coding Object Oriented Programming in Python'
pubDate: 'Aug 13 2026'
board: 'all'
level: 'a-level'
learningTime: '30 min'
---

### Creating a Class

brief description what a class is

```python
# A blueprint for a Bank Account Object
class BankAccount:

	# Initialisation Function
	def __init__(self, pName, pSurname, pAccountNumber):
		self.name = pName
		self.surname = pSurname
		self.accountNumber = pAccountNumber
		self.money = 0
```

So things to note
- explain what initialisation function does
- explain what self is
- explain the "pVariable"
- explain what self.variable is doing (attributes)

```python
# Instantiation
account1 = BankAccount("Blake", "Eldridge", 1)

print(account1.name) # Blake
print(account1.money) # 0
```
Explain what instantiation is and the parameters

### Methods

brief description what a method is

```python
class BankAccount:
	def __init__(self, pName, pSurname, pAccountNumber):
		self.name = pName
		self.surname = pSurname
		self.accountNumber = pAccountNumber
		self.money = 0
		
	# Method 1 : putting money into the account
	def deposit(self, amount):
		self.money += amount
		
	# Method 2 : taking money out (we pretend that is a return)
	def withdraw(self, amount):
		if self.money < amount:
			print("You do not have enough money!")
			return
		
		self.money -= amount
		return amount
```

- indent + def + self means we have a method
- explain briefly what deposit and withdraw do
- now all objecst of bank account have this

```python

print(account1.money) # 0

account1.deposit(1000)

print(account1.money) # 1000

account1.withdraw(250)

print(account1.money) # 750

```
- explanation of code

### Getters and setters

- quick explanation of both with accordance to public/private

```python
class BankAccount:
	def __init__(self, pName, pSurname, pAccountNumber):
		# Notice the "__" in front of the variable name now
		# Private Variable
		self.__name = pName
		self.surname = pSurname
		self.accountNumber = pAccountNumber
		self.money = 0
		
	# Getter (for name)
	def getName(self):
		return self.name
		
	# Setter (for name)
	def setName(self, newName):
		self.name = newName
		
	...

```

- explanation what they do in this context
- explanation of python public vs private

### Inheritance

explanation of inheritance

```python
# This is going to be our parent class
class BankAccount:
	...
	
# This is how we inherit a class.
# SavingsAccount is now a "child" of BankAccoung
class SavingsAccount(BankAccount):
	def __init__(self, pName, pSurname, pAccountNumber):
		# Call the initialisation of the parent class
		super().__init__(pName, pSurname, pAccountNumber)
		self.interestRate = 0.05
	
	# new method	
	def addInterest(self):
		interest = self.interestRate * self.money
		self.money += interest

```

- explain what it means to inheirt, the methods and attributes it got
- explatin super etc
- explain new methods

```python

s = SavingsAccount("Blake", "Eldridge", 5)

s.deposit(200) # inherited method from parent class

s.addInterest() # new method only seen by savings accounts

```
- brief code explanation

### Overiding and Overloading

- what they are, they only occure in inheritance

```python

class HighInterestSavingsAccount(SavingsAccount):
	def __init__(self, pName, pSurname, pAccountNumber):
		super().__init__(pName, pSurname, pAccountNumber)
		self.interestRate = 0.
		# new variables
		self.withdrawLimit = 3
		self.currentWithdraws = 0
		
	...
		
	# Overriding the withdraw function
	def withdraw(self, amount):
		if amount > self.money:
			print("Not enough money!")
			return 0
		
		self.currentWithdraws += 1
		if self.currentWithdraws > self.withdrawLimit:
			print("You have withdrawn too many times, interest rate reduced!")
			self.interestRate = 0.05
			
		self.money -= amount
		return amount
```

- explain the point of this function
- explain how overriding works with it

```python

b = BankAccount("Arthur", "Dent", 1)
b.deposit(1000)
b.withdraw(100) # simply just subtracts 100

s = HighInterestSavingsAccount("Ford", "Prefect", 2)
s.deposit(1000)
s.withdraw(100) # uses high interest accounts one

print(s.currentWithdraws) # 1
```

- overloading does not exist in python
- explain meaning

### Association - Aggregation and Composition
- association


```python
class Human:
	def __init__(self, pName, pSurname):
		self.name = pName
		self.surname = pSurname
		self.age = 0
		
		self.bankAccount = BankAccount(pName, pSurname, 1) # Composition
		
class Car:
	def __init__(self):
		self.passengers = []
		
	def addPassenger(self, passenger):
		self.passengers.append(passenger) # this will lead to aggregation
		

c = Car()
h = Human("Captain", "Beatty")

c.addPassenger(h) # this is aggregation
```

- explain differences between aggregation + composition and how they play their part here

### Final Buzzwords
- encapsulation
- polymorphism


### Practise Questions

1. Create the class definition (none of its methods) for the following outline of the VendingMachine. This stores all its items in a 2D array of 5 rows x 5 columns. Each item is an object itself, and if there is nothing in the cell, then the cell contains "None".

VendingMachine
+Items : Array<Array\<Item>>
+CashInserted : Float
-machineId : Int
-isOperational : Bool
_______________________________
+isEmpty() returns Bool
+isFull() returns Bool
+getStatus() returns Bool
+setStatus(status)

+PurchaseItem(row, col) returns Item
+AddItem(row, col)

```python

# Answer here

```


2. Each item has the following structure :

Item

-itemId : Int
-itemPrice : Float
+itemName : Str
+isAgeRestricted : Bool

+getPrice() returns Float
+setPrice(price)

Create the class definition along with the getters and setters of the Item Class

```python

# Answer here


```

3. Write out the code for the VendingMachine PurchaseItem method
```python

# Answer here

```

4. Write out the code for the VendingMachine AddItem method

```python

# Answer here

```

5. One example of an item is a snickers bar of chocolate. Create a class definition of snickers bar that inherits from the Item class.

```python

# Answer here

```

6. Instantiate a VendingMachine object and add 2 snickers bars to the top left and bottom right position of the vending machine.

```python

# Answer here

```

### Conclusion