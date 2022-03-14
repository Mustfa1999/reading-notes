# Reading: Class 07

> [Back to the main](./README.md)

---

## Scopes

- Global scope: The names that you define in this scope are available to all your code.

    Like when we define a variable outside a functions, classes, and loops.

- Local scope: The names that you define in this scope are only available or visible to the code within the scope.

    Like when we define variables inside an indented scope.

---

## LEGB Rule for Python Scope

- Local (function) scope - functions

    it is the code block or body of any Python function or lambda expression. This Python scope contains the names that you define inside the function. These names will only be visible from the code of the function

        def local():
            print("I'm inside a local scope, you can't reach me from outside !")

    ---

- Enclosing (nonlocal) scope - nested functions

    it is a special scope that only exists for nested functions. If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function. This scope contains the names that you define in the enclosing function. The names in the enclosing scope are visible from the code of the inner and enclosing functions.

        def local():
            print("I'm inside a local scope, you can't reach me from outside !")

            var = 0

            print("(var) can be reached here !")

            def enclosing():
                print("I'm inside an enclosing scope, you can't either reach me from the function (local) or outside it !")

                nonlocal var 

                print("(var) can be reached here too, since it is nonlocal!")

    ---

- Global (module) scope

    it is the top-most scope in a Python program, script, or module. This scope contains all of the names that you define at the top level of a program or a module. Names in this scope are visible from everywhere in your code.

        print("I'm inside a global scope, you can reach me from anywhere !")

        var = 0

        print("(var) can be reached here !")

        def local():
            print("I'm inside a local scope, you can't reach me from outside !")

            global var

            print("(var) can be reached here too, since it is global !")

    ---

- Built-in scope - builtins

    it is a special Python scope that’s created or loaded whenever you run a script or open an interactive session. This scope contains names such as keywords, functions, exceptions, and other attributes that are built into Python. Names in this Python scope are also available from everywhere in your code. It’s automatically loaded by Python when you run a program or script.

    abs(-15)    # It can be accesed since it is imported

    abs = 10    # we changed the reference of it
    abs(-15)    # error raised, it is not a function anymore because it got out of its scope

---
