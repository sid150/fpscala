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
