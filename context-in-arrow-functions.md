# Arrow Functions Review

1. Arrow Function Syntax:
    • More concise than traditional function declerations
    • Introduced in ES2015

2. Defining an Arrow Function:

    • Traditional Function:
    ```js
    let doubleNum = function(num) {
        return num * 2;
    };
    ```

    • Arrow Function:
    ```js
    let doubleNum = num => num * 2;
    ```

3. Anatomy of an Arrow Function:

    • Multiple statements:
    ```js
    (parameters) => {
        statement1;
        statement2;
        return value;
    }
    ```

    • Example:
    ```js
    function fullName(fname, lname) {
        let str = `Hello ${fname} ${lname}`;
        return str;
    }

    let fullNameArrow = (fname, lname) => {
        let str = `Hello ${fname} ${lname}`;
        return str;
    };
    ```

4. Single Parameter:

    • Parentheses can be omitted if there's only one parameter
    ```js
    param1 => {
        statement;
        return value;
    };
    ```

5. No Parameters:

    • Parentheses are required
    ```js
    () => {
        statements;
        return value;
    };
    ```

6. Single Expression Arrow Functions:

    • Implicit return without curly braces and return keyword
    ```js
    argument => expression;
    // equivalent to
    (argument) => { return: expression; };
    ```

    • Example:
    ```js
    const multiply = (num1, num2) => num1 * num2;
    ```

7. Multiple Statements:

    • Explicit return is needed
    ```js
    const halfMyAge = myAge => {
        const age = myAge;
        return age / 2;
    };
    console.log(halfMyAge(30)); // 15
    ```

8. Arrow Functions are Anonymous:

    • Cannot be used without assigning to a variable
    ```js
    const sayHello = name => console.log("Hi, " + name);
    sayHello("Curtis"); // => Hi, Curtis
    ```

* Summary

    • Define an Arrow Function: `let func = (params) => {
        statements;
    };`

    • Implicit Return: For single-expression functions, omit braces and `return`
    ```js
    let func = param => param * 2;
    ```
    • Anonymous Nature: Arrow functions are anonymous and need to be assigned to a variable to be reused



# Context in Arrow Functions

Key Points

    1. Context Binding:
        • Arrow functions do not have their own `this`
        • `this` in arrow functions is lexically bound to the surrounding code (where it was defined), not where it is called

    2. Compatibility with Callbacks :
        • Arrow functions are useful as callbacks because they don't rebind `this`
        • This simplifies code, making it more readable and avoiding the need for `.bind()`

Example: Arrow Functions vs. Regular Functions

    * Regular Function with `setTimeout`:

    ```js
    class Dog {
        constructor(name) {
            this.name = name;
        }

        delayedBark() {
            setTimeout(function() {
                console.log(this.name);
            }, 1000);
        }
    }

    let dog = new Dog("Fido");
    dog.delayedBark(); // `undefined` because `this` refers to the `setTimeout` context
    ```

    * Using `bind`:

    ```js
    class Dog {
        constructor(name) {
            this.name = name;
        }

        delayedBoundBark() {
            setTimeout(function() {
                console.log(this.name);
            }.bind(this), 1000);
        }
    }

    let dog = new Dog("Fido");
    dog.delayedBoundBark(); // "Fido" after 1 second
    ```

    * Using Arrow Function:

    ```js
    class Dog {
        constructor(name) {
            this.name = name;
        }

        arrowBoundBark() {
            setTimeout(() => {
                console.log(this.name);
            }, 1000);
        }
    }

    let dog = new Dog("Fido");
    dog.arrowBoundBark(); // "Fido" after 1 second
    ```
    • Arrow functions simplify the code by lexically binding `this`


Defining Class Methods as Arrow Functions

    * Regular Function Method:

    ```js
    class Dog {
        constructor(name) {
            this.name = name;
        }

        bark() {
            console.log(`${this.name} barked at you`);
        }
    }

    const fido = new Dog("Fido");
    fido.bark(); // Fido barked at you
    const fidoBark = fido.bark;
    fidoBark(); // undefined barket at you
    ```

    * Arrow Function Method:

    ```js
    class Dog {
        constructor(name) {
            this.name = name;
        }

        bark = () => {
            console.log(`${this.name} barked at you`);
        }
    }

    const fido = new Dog("Fido");
    fido.bark(); // Fido barked at you
    const fidoBark = fido.bark;
    fidoBark(); // Fido barked at you
    ```
    • Using an arrow function ensures `this` always refers to the instance

* Memory Consideration:
    • Arrow functions create a new instance for each class instance
    • If there are many instances, it can increase memory usage
    • Use arrow functions for class methods only if necessary (e.g. frequent binding)

* Summary
    • Arrow Function Context: Lexically bound to the containing scope
    • Defining Class Methods: Use arrow functions for methods if you need `this` to always refer to the instance, especially in callbacks
    • Memory Use: Be mindful of memory usage with many instances
