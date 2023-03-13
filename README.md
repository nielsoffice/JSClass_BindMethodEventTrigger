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
