```js
/* Create a class for vehicle. Each vehicle instance should have the following properties:
    - make
    - model
    - year
*/

class Vehicle{
    constructor(make, model, year){
        this.make = make;
        this.model = model;
        this.year = year;
    }
    honk(){
        return "Beep.";
    }
    toString(){
        return `The vehicle is a ${this.make} ${this.model} from ${this.year}`;
    }
}

class Car extends Vehicle{
    constructor(make, model, year){
        super(make, model, year);
        this.numWheels = 4;
    }
}

class Motorcycle extends Vehicle{
    constructor(make, model, year){
        super(make, model, year);
        this.numWheels = 2;
    }
    revEngine(){
        return "VROOM!!!";
    }
}

class Garage{
    constructor(capacity){
        this.vehicles = [];
        this.capacity = capacity;
    }
    add(vehicle){
        if(this.vehicles.length >= this.capacity){
            return "Sorry we're full!"
        }
        else if(vehicle instanceof Vehicle){
            this.vehicles.push(vehicle);
            return "Vehicle added!";
        }
        else{
            return "Only vehicles are allowed in here!";
        }
    }
}


// Part One
let myFirstVehicle = new Vehicle("Toyota", "Sprinter Trueno GT-APEX", 1983);
console.log(myFirstVehicle.toString());
console.log(myFirstVehicle.honk()+"\n");

// Part Two
let myFirstCar = new Car("Toyota", "GR86", 2023);
console.log(myFirstCar.toString());
console.log(myFirstCar.honk());
console.log(myFirstCar.numWheels + "\n");

// Part Three
let myFirstMotorcycle = new Motorcycle("Honda", "Nighthawk", 2000);
console.log(myFirstMotorcycle.toString());
console.log(myFirstMotorcycle.honk());
console.log(myFirstMotorcycle.revEngine());
console.log(myFirstMotorcycle.numWheels + "\n");

let garage = new Garage(2);
console.log(garage.vehicles); // []
console.log(garage.add(new Car("Hyundai", "Elantra", 2015))); // "Vehicle added!"
console.log(garage.vehicles); // [Car]
console.log(garage.add("Taco")); // "Only vehicles are allowed in here!"

console.log(garage.add(new Motorcycle("Honda", "Nighthawk", 2000)));
// "Vehicle added!"
console.log(garage.vehicles); // [Car, Motorcycle]

console.log(garage.add(new Motorcycle("Honda", "Nighthawk", 2001)));
// "Sorry, we're full."
```