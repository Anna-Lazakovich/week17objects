# week17objects

1. Что такое объекты в JavaScript?
Это набор свойств и (или) функций, собранных в одной переменной. Объекты состоят из пар «ключ — значение». 

2. Как создать объект в JavaScript?
С использованием конструктора или фигурных скобок {}.
let user = new Object() или let user = {};

3. Как создать класс в JavaScript?
Необходимо использовать ключевое слово class, после которого пишется имя класса с заглавной буквы, опрелеляются свойства объекта, методы. Пример:
class Square {
  constructor(color, size) {
    this.color = color;
    this.size = size;
  }
}

4. Как добавить методы в класс?
class Square {
  constructor(color, size) {
    this.color = color;
    this.size = size;
    this.draw(); //Вызываем метод draw при создании объекта
  }

  draw() {
    this.element = document.createElement('div');
    this.element.style.width = this.size + 'px';
    this.element.style.height = this.size + 'px';
    document.body.appendChild(this.element);
  }
}

5. Как создать экземпляр класса?
С помощью ключевого слова new, используя конструктор класса и задавая значения параметров.
const redSquare = new Square('red', 100); 

6. Что выведет код?
const person = {
  name: "Алиса",
  age: 25,
};

console.log(person.name);	 //Алиса

7. Что выведет код? Почему именно так? 
const person = {
	name: 'John',
	age: 25,
};

let city = person.city;
city = 'Moscow';

console.log(person); //
Выведет
{
	name: 'John',
	age: 25,
}
, потому что у объекта нет свойства city.


8. Что выведет код? Почему именно так? 
class Animal {
  constructor(name) {
    this.name = name;
  }

  sound() {
    console.log("Animal sound");
  }
}

class Dog extends Animal {
  sound() {
    console.log("Woof!");
  }
}

const dog = new Dog("Buddy");

dog.sound(); //
Выведет 
Woof!
, потому что новый класс наследует от исходного все его свойства и методы, но при этом ему можно присвоить уникальные значения свойств.


9. Что выведет код? Почему именно так? 
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  introduce() {
    console.log(`Hi, my name is ${this.name} and I'm ${this.age} years old.`);
  }
}

class Student extends Person {
  constructor(name, age, major) {
    super(name, age);
    this.major = major;
  }

  study() {
    console.log(`I'm studying ${this.major}.`);
  }
}

const person = new Person("John", 25);
const student = new Student("Alice", 20, "Computer Science");

const introduceFunc = person.introduce;
introduceFunc(); //?

Ничего не выведет, потому что метод нужно вызывать со скобками, то есть const introduceFunc = person.introduce()


10. Что выведет код? Почему именно так? 
function sayHello() {
  console.log(`Hello, ${this.name}!`);
}

let name  = "Nina";

const person1 = {
  name: "Alice",
  greet: sayHello
};

const person2 = {
  name: "Bob",
  greet: sayHello
};

sayHello();      //? Hello, !
person1.greet(); //? Hello, Alice!
person2.greet(); //? Hello, Bob!

В первом случае при вызове функции имя еще не задано, поэтому вывод "Hello, !"