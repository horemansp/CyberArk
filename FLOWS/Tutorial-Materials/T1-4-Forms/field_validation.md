### Validate form field at input.
You can use javascript to validate for example an input field.
Enter the code beneath on the form field Data/Calculated field.<br>
This will verify the input against the regex list. If there is an unwanted character it will be removed from the input field.

```
function validateInput(theInput) {
       var regex = /^[a-zA-Z0-9 ]*$/;
        return regex.test(theInput);
}


if(!validateInput(data.firstName)){ //asuming the field API property name is 'firstName'
  value = value.slice(0,-1);
}
```

or 

```
const allowedList = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789.";


function charOk(inputString) {
    for (let i = 0; i < inputString.length; i++) {
        if (!allowedList.includes(inputString[i])) {
            return true;
        }
    }
    return false;
}


if(charOk(data.lastName)){ //asuming the field API property name is 'lastName'
  value = value.slice(0, -1)
}
```

> [!TIP]
> The above examples are showcased in the PH-Form_input_validation.json flows file
