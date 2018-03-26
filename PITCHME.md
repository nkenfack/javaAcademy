# Welcome

---

## Primitive Obsession

> When an object can represent a domain concept better than a Primitive Type

``` 
Int age = person.age()
if (isAdult(age)) {
  // do something
}
```

+++

### Primitive Obsession Solution

Move the method into the appropriate class

``` 
Age age = person.age()
if (age.isAdult()) {
  // do something
}

class Age {
	public bool isAdult() { ... }
}
```

---

## Duplicated Code

> When code fragments are repeated

```                                        
if (creditCard.Number.length() > 16) {      
  // do something because it's valid       
}                                          
...                                        
if (creditCard.Number.length() > 16) {     
  // do something else because it's valid  
}                                          
```

+++

### Duplicated Code Solution

Don't Repeat Yourself! Extract method

```                                        
if (creditCard.Number.isValid()) {      
  // do something because it's valid       
}                                          
...                                        
if (creditCard.Number.isValid()) {     
  // do something else because it's valid  
}                                          
```

---

## Long Method

> When methods are so long and do so many things that you can't keep it in your mind while reading

### Solution

Split the method into multiple sub methods, each one with one single purpose

---

## Large Class

> When a class solves too many problems or has too many fields/methods/lines of code

### Solution

Restructure the class to identify different classes to create, or move methods into other more appropriate classes

---

## Long Parameter List

> When the number of parameters increase the complexity exponentially

### Solution

Aggregate parameters into objects or reduce parameters by moving logic into smaller methods

---

## Switch Statements

> When too many switch and ifs are used instead of polymorphism

```
class DataPlan {
  int limit() {
    switch (type) {
      case BASIC:
        return baseLimit();
      case PRO:
        return baseLimit() * 3;
    }
  }
}
```

+++

### Switch Statements Solution

Replace Type Code with Subclasses and Polymorphism

```
abstract class DataPlan {
  abstract int limit();
}

class Basic extends DataPlan {
  int limit() {
    return baseSpeed();
  }
}
class Pro extends DataPlan {
  int limit() {
    return baseLimit() * 3;
  }
}

...

limit = plan.limit();
```

---

## Data  Clumps

> When more parameters or fields usually goes around together

``` 
verify(String cardNumber, String cvv, Date expiration, Date paymentDate)

pay(String cardNumber, String cvv, Date expiration)
```

+++

### Data Clumps solution

Don't be shy! Extract a class...

``` 
class CreditCard {
    public String cardNumber() { ... }

	public String cvv() { ... }

	public Date expiration() { ... }
}

verify(CreditCard creditCard, Date paymentDate)

pay(CreditCard creditCard) 
```

---

# Thank you!

## References
 - [8th light post by Georgina](https://8thlight.com/blog/georgina-mcfadyen/2017/01/19/common-code-smells.html)
 - [Source Making](https://sourcemaking.com)