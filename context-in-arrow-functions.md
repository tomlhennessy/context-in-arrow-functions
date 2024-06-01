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
