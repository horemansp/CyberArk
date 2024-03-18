### Validate form field entrance.
You can use javascript to validate for example an input field.
Enter the code beneath on the form field Data/Calculated field

```
function validateInput(theInput) {
       var regex = /^[a-zA-Z0-9 ]*$/;
        return regex.test(theInput);
}


if(!validateInput(data.firstName)){ //asuming the field API property name is 'firstName'
  value = value.slice(0,-1);
}
```
