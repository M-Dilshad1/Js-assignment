                                          what is currying:

Currying in JavaScript is a functional programming technique where a function is transformed into a sequence of functions, each taking a single argument. Instead of taking all arguments at once, a curried function takes them one by one and returns a new function for each argument until all arguments are provided.

                                           How Currying Works:

In currying, if a function normally expects n arguments, it is rewritten so that it takes one argument and returns a function that takes the next argument, and so on, until all n arguments are passed.  

                                            Real world example:
                        
Form Validation with Currying:

const validate = rule => errorMessage => value => {
    if (!rule(value)) {
        return errorMessage;
    }
    return null;
};

const isRequired = value => value.trim() !== ''; 
const minLength = length => value => value.length >= length; 

const validateRequired = validate(isRequired)("This field is required.");
const validatePasswordLength = validate(minLength(6))("Password must be at least 6 characters long.");

const nameError = validateRequired("John"); 
const passwordError = validatePasswordLength("123"); 

console.log(nameError); 
console.log(passwordError); 

const anotherPasswordError = validatePasswordLength("secret123"); // No error
console.log(anotherPasswordError); 
