### Validate form field at input.
You can use javascript to validate for example an input field.
Enter the code beneath on the form field Data/Calculated field.<br>
This will verify the input against the regex list. If there is an unwanted character it will be removed from the input field.

```
function validateInput(theInput) {
       var regex = /[a-zA-Z0-9 ]*/; //note: don't use the ^ and $ as you usually would do with regex, for example /^[a-zA-Z0-9 ]*$/
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

###Make fields available based on selection
In the example Form-field-selector-valdiation.json flow you will see an example that shows certain fields based upon a dropdown selection.<br>
It will also verify the number format they have to enter with custom attributes to change the color.
