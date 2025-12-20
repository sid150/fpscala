Idea of FP -> build pure functions i.e no side effects eg, modifying variables, halting, reading or writing to and fro files.

```python
class Cafe:
    
    def buy_coffee(self, Creditcard, Coffee):
        return (Coffee.cup, Charge(Creditcard.ccno, Coffee.price))
        #return instance of the charge class, no side-effects

class Coffee:
    
    def __init__(self, cup, price):
        self.cup = cup
        self.price = price
    
    
class Creditcard:
    
    def __init__(self, ccno):
        self.ccno = ccno
        
        
class Charge:
    def __init__(self, ccno, price):
        self.ccno = ccno
        self.price = price

    def __str__(self):
        return f"CCNO = ({self.ccno}) , Cost = ({self.price})"


americano = Coffee('americano', 3.5)
usercc = Creditcard('123456')
stbks = Cafe()
info = stbks.buy_coffee(usercc, americano)
print(info[1])
```
```text
CCNO = (123456) , Cost = (3.5)
```
Pure functions in python?
Example addition of a number will return the integer value, that is it. Nothing else is processed thorughout its execution.

Pure functions in python generally occur on immutable data types, e.g strings, ints, tuples. 

Mutable types (e.g list) change a variable outside its scope.

Referential transparency - If an external function that is essentially pure and returns a class, then replacing a call to that function with the value it returns does not semantically change its behavior.