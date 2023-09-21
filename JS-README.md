# LWC-JS-Cheetsheet
LWC Cheatsheet:

DATATYPES:

var: having functional scope / change the value
let: having block scope / change the value
const: having block scope / constant value


// LWC JavaScript foreach:
const myArray = [{ name: 'Alice' }, { name: 'Bob' }, { name: 'Charlie' }];

myArray.forEach(item => {
    console.log(item.name);
});


// LWC JavaScript Map:
const numbers = [1, 2, 3, 4, 5];

const squaredNumbers = numbers.map(number => number * number);

console.log(squaredNumbers);


// LWC JavaScript SET:
const mySet = new Set();

mySet.add(1);
mySet.add(2);
mySet.add(2); // This won't be added, as it's a duplicate

console.log(mySet.has(1)); // true
console.log(mySet.has(2)); // true
console.log(mySet.size);   // 2


// LWC JavaScript Spread Operator:
const originalArray = [1, 2, 3];
const copyArray = [...originalArray];

console.log(copyArray); // [1, 2, 3]
console.log(originalArray === copyArray); // false (they are different references)


// LWC JavaScript Spread Operator:
const object1 = { name: 'Alice' };
const object2 = { age: 30 };
const mergedObject = { ...object1, ...object2 };

console.log(mergedObject); // { name: 'Alice', age: 30 }

// Arrow Function non parameterize:
const sayHello = () => {
    console.log('Hello, World!');
};

sayHello(); // Outputs: Hello, World!


// Arrow Function parameterize:
const double = (x) => {
    return x * 2;
};

console.log(double(5)); // Outputs: 10


// Arrow Function parameterize in one line:
const add = (a, b) => a + b;

console.log(add(3, 7)); // Outputs: 10



// Arrow Function LWC  :
import { LightningElement, api } from 'lwc';

export default class ChildComponent extends LightningElement {
    @api onbuttonclick;

    handleButtonClick() {
        this.onbuttonclick(); // Call the passed function
    }
	
	const onbuttonclick =()=>{
	return 1+2;
	}
}


Object in javascript lwc:
options = [
        { label: 'Docksta table', value: 'Docksta table' },
        { label: 'Ektorp sofa', value: 'Ektorp sofa' },
        { label: 'Poäng armchair', value: 'Poäng armchair' }
      
    ];
