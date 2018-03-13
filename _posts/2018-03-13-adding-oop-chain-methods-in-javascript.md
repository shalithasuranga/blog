---
layout: post
title:  "Adding OOP chain methods in Javascript"
author: "Shalitha Suranga"
---

<img src="https://i.ytimg.com/vi/5rwuKH-zdos/maxresdefault.jpg" align="center" width="600">

[Method chaining](https://en.wikipedia.org/wiki/Method_chaining) is very useful when you have several setter type methods in a class. This technique can be used to simplify the structure of code and to reduce number of lines in the code as well.

For an instance see `Car` class below

```
class Car {
  
  constructor(id){
  	this.id = id;
  }
  
  setMake(make) {
  	this.make = make;
  }
  
  setModel(model) {
  	this.model = model
  }
  
  setFuelType(fuelType) {
  	this.fuelType = fuelType;
  }
  
  getCarInfo() {
  	return {
    	"id" : this.id,
      "make" : this.make,
      "model" : this.model,
      "fuelType" : this.fuelType
    };
  }
}
```

If we need to create a new `Car` object with several properties. We usually write like this.

```
let car = new Car(233);
car.setMake("Honda");
car.setModel("Civic");
car.setFuelType("Petrol");
console.log(car.getCarInfo());
```

Here the setter methods are accessed seperately. Thus if we have more these setter like methods, eventually we will end up with many lines `car.set..`, `car.set..` etc.

Now we will modifiy our `Car` class by adding chaining trick.

```
class Car {
  
  constructor(id){
    this.id = id;
  }
  
  setMake(make) {
    this.make = make;
    return this;
  }
  
  setModel(model) {
    this.model = model
    return this;
  }
  
  setFuelType(fuelType) {
    this.fuelType = fuelType;
    return this;
  }
  
  getCarInfo() {
  	return {
    	"id" : this.id,
      "make" : this.make,
      "model" : this.model,
      "fuelType" : this.fuelType
    };
  }
}
```

 `return this` statement is added to all setter methods in order to return the reference of current object. Thereafter we are able to use all setter methods of `Car` class again and again (That is why it is called methods chaining).
 
 Therefore now we can do the same thing just by using only one line.
 
 ```
 console.log(new Car(233).setMake("Honda").setModel("Civic").setFuelType("Petrol").getCarInfo());
 ```


Happy coding!!





















