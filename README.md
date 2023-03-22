# JSClass Bind Method Event Trigger
JS Class Bind method event triggered, where method triggered with Event or EventListener once it is invoke. 

```HTML
<form id="user-input">
 <div class="form-control">
  <label for="username">Username</label>
  <input type="text" id="username" />
 </div>
 <div class="form-control">
   <label for="password">Password</label>
   <input type="password" id="password" />
 </div>
 <button type="submit">Create User</button>
</form>
```

```JS
class RequestForm {
 
 constructor() {
    this.form = document.getElementById('user-input');
    this.userNameInput = document.getElementById('username');
    this.passwordInput = document.getElementById('password');
    
    // "this.methodName.bind(this)"
    // It means this "class" and it's method named "dataHandler"	
    // will execute once the button submit triggered!
    this.form.addEventListener('submit', this.dataHandler.bind(this));
  }
   
  // execute this method as callback function once the event is triggered! 
  dataHandler(event) {
    event.preventDefault();

    const enteredUserName = this.userNameInput.value;
    const enteredPassword = this.passwordInput.value;

    console.log('User_name' + enteredUserName + ' password' + enteredPassword );
 
  }
}

new RequestForm();
```

```JS
// Console.log() | Result
User_name: niel password: 143
```

FUNCTION BIND

```JS
const Developer = {
  firstName:"Jhon",
  lastName: "Doe",
  getFullName: function() {
    return this.firstName + " " + this.lastName;
  }
}

const frontEnd = {
  firstName:"Niel",
  lastName: "Zednanref",
}

let getfullName = Developer.getFullName.bind(frontEnd);
console.log(getfullName());

// Demo 1B 
// Inherit the all method and propertiest of Primary method
frontEnd.__proto__ = Developer;
// OR 
// Is Developer Prototype of frontEnd?? 
// Is Developer give something to frontEnd?? // Result YES 
console.log(Developer.isPrototypeOf(frontEnd)); // True < Developer give all methods and properties >
console.log(frontEnd.getFullName()); // Niel Fernandez 
console.log(frontEnd.advancetage); // true

// Demo 2 
function multiply(a,b) {
  return a*b;
}

let multiplyByTwo = multiply.bind(this, 2);
console.log(multiplyByTwo(4)); // Result 8

let multiplyByTen = multiply.bind(this, 10);
console.log(multiplyByTen(10)); // Result 100

// DEMO 3
function dataTester(data,requirement) {
   if(Array.isArray(data)) { return data +' are a plural store in array ' + requirement; } 
   else { return data +' is a singular not array ' + requirement; }
}

let dataTesterUsers = dataTester.bind(this, ['one','tine']);
console.log(dataTesterUsers('Correct!'));

let dataTesterUser = dataTester.bind(this, 'Tame');
console.log(dataTesterUser('Correct!'));
```

```JS
 // Console.log() | Result 
 Niel Zednanref
-----------------------------------------------------
 Niel Zednanref
 True
----------------------------------------------------- 
 8
 100
----------------------------------------------------- 
one,tine are a plural store in array Correct!
Tame is a singular not array Correct!
```

```JS
// Similar to Borrowing Method Object 
https://github.com/nielsoffice/JSBorrowingMethod_Object
```

```JS
// Master Object
const primaryObjectName = { ... };

// child Object
const childObjectName = { ... };

// Inherit childObject from MasterObject
// this methodName();
// Once they click eventListerner methodName will run to childObject as it is inherit from
// the master object the method name methodName();
element.eventListener('click', primaryObjectName.methodName.bind(childObjectName));
```
