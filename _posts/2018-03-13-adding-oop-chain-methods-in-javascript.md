---
layout: post
title:  "Adding OOP chain methods in Javascript"
author: "Shalitha Suranga"
---


[Method chaining](https://en.wikipedia.org/wiki/Method_chaining) is very useful when you have several setter type methods in a class. This technique can be used to simplify codings and reduce number of lines in the code.

For an instance see `Car` class below

```Javascript
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

If we need to create new `Car` object with several properties. We usually write like this.

```Javascript
let car = new Car(233);
car.setMake("Honda");
car.setModel("Civic");
car.setFuelType("Petrol");
console.log(car.getCarInfo());
```

Here the setter methods are called seperately. Thus if we have more setter like methods, eventually we will end up with more lines `car.set..`, `car.set..` etc.

Now we will modifiy our `Car` class by adding chain trick.

```Javascript
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

 `return this` statement is added to all setter methods to return the reference of current object. Therefore we are able to use all setter methods of `Car` classa again and again.
 
 Therefore now we can do the same thing just by using one line.
 
 ```Javascript
 console.log(new Car(233).setMake("Honda").setModel("Civic").setFuelType("Petrol").getCarInfo());
 ```


Happy coding!!





















