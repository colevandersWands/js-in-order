# JavaScript in Order

Being able to accurately predict how JavaScript interprets your __source code__ to manage __program state__ is the most valuable skill you can develop as a new programmer.  This is also one of the most challenging things to learn, so be regular and be diligent in your practice. 

To learn the [JS notional machine](https://github.com/janke-learning/js-notional-machine) as effectively as possible, copy any code you are studying into [PythonTutor](http://www.pythontutor.com/javascript.html#) and carefully step through it's execution.  You will learn the most if you write down your prediction for each step before clicking the "forward" button.

This file is a light overview of JavaScript and PythonTutor, laid out in order based on how complex the notional machine is for each language feature.  ie. the nm for variables & hoisting is simpler than for block scope, and/or is required to understnad block scope.  


### Index:
1. [errors & program life cycle](#errors-and-program-life-cycle)
1. [variables & hoisting](#variables---hoisting)  
1. [primitives](#primitives)  
1. [operators](#operators)  
1. [expressions vs. statements](#expressions-vs-statements)  
1. [block scope](#block-scope)
1. [complex expressions](#complex-expressions)  
1. [truthiness](#truthiness)
1. [conditionals](#conditionals)  
1. [iteration](#iteration)  
1. [reference types](#reference-types)
1. [iterating over reference types](#iterating-over-reference-types)  
1. [functions](#functions)
1. [free variables](#free-variables)
1. [prototypical inheritance](#prototypical-inheritance)
1. [about python tutor](about-pytut)  


---


## [errors and program life-cycle](https://github.com/janke-learning/errors-and-life-cycle)

* there are [two types of errors](https://wci.llnl.gov/codes/basis/manual/node53.html) in programming
    * __syntax errors__: "bad spelling", the machine can't understand ("parse") what you've written
    * __semantic errors__: the machine was able to parse your code, but you asked it to do something that is not allowed
* js programs have 2 stages: [creation phase & execution phase](https://www.youtube.com/watch?v=YID-HIdy1bk)
* _creation phase errors_ - some errors are caught by JS when it is compiling your code in the _creation phase_
    * creation phase errors can be identified because pythontutor will not go to the code visualization page
    * [_syntax errors_](https://goo.gl/1Psxu7): "bad spelling", the machine can't understand ("parse") what you've written
    * [_semantic errors_](https://goo.gl/68af7H): the machine was able to parse your code, and you made a mistake that JS is designed to catch before the program starts
* _runtime errors_ - some errors are not caught until JS executes it in the _execution phase_
    * runtime errors can be identified because pythontutor will throw the error when it reaches that line of code
    * [_semantic errors_](https://goo.gl/WzbmNE): the machine was able to parse your code, but you wrote an invalid that JS wasn't designed to or able to catch until the program was running.  these can be much harder to track down than creation-phase errors
* js will sometimes give you warnings as well, these are not the same as errors. your code will still work but maybe with bad practices or with certain risks.  you can ignore these for now
  
  
  
> logic errors (or "bugs") are when your code does not do what you expected, this is unrelated to language errors (writing invalid commands for JS).  Bugs and errors are often taught together, but are actually [completely different things](https://www.youtube.com/watch?v=tV0tQisuxPo). Fixing language errors requires only a solid understanding of the JS notional machine, while debugging also requires an understanding of program dynamics, tracing execution, debugging strategies & testing.  Debugging will be covered in depth later on.
    
  
 

[TOP](#pythontutor-for-javascript)

---

## [variables & hoisting](https://github.com/janke-learning/variables-and-hoisting)

* [helpful link](https://github.com/janke-learning/hoisting-variables)
* variables are not a very complicated topic, but they are tricky and crucial to understanding the relationships between:
  * the code you write
  * the javascript notional machine / program execution phase
  * and program state
* a good and simple way to check your understandign of variables is [the value swap](https://github.com/janke-learning/value-swap)
* there are two things you can do with variables
  * [__Declaration__](https://goo.gl/dGfhNj): this statement tells JavaScript to set create a new variable that can be used to store values later on, but does not assign it a value. 
  * [__Assignment__](https://goo.gl/PJNF5x): also known as "Defining", this expression tells JS to assign a new value to a variable
* [__hoisting__](https://goo.gl/Ruc4gB): JS declares (but not defines) "var" variables durring the _creation phase_ of a program
  * in the creation phase, your code is processed and the _global frame_ is prepared
  * "var" variables are __declared__ but not defined, this is called "hoisting"

 

[TOP](#pythontutor-for-javascript)

---


## [Primitives](https://github.com/janke-learning/primitives)  

* [helpful link](https://developer.mozilla.org/en-US/docs/Glossary/Primitive) 
* are stored [_by value_](https://github.com/janke-learning/reference-vs-value) directly in a variable
* modifying one variable will not effect any other primitive values
* are "things that don't hold other things"
* can be one of 6 types: undefined, number, string, null, boolean & symbol - [primitive types examples](https://goo.gl/n8mwWT)   
* primitives have both a type and a value: [numbers example](https://goo.gl/Mv2wjc), [strings example](https://goo.gl/2x6rPs)  
* you can convert primitives to different types with [explicit type casting](https://goo.gl/RgZ7gF)  
    * there is no way to cast something to null    
    * the rules for these conversions are tricky and will be covered in detail later on  


[TOP](#pythontutor-for-javascript)

---

## [operators](https://github.com/janke-learning/operators)

* [helpful link](https://javascript.info/operators)
* operators take two values and _evaluate_ (or "collapse", or "resolve") to a new value
* every operator works according to rules that you can learn & understand (even if they don't always make sense)
* you can think of operators as "maps" from one type+value to another type+value
    * [the typeof operator](https://goo.gl/hp9sN9) maps from all type+values to a helpful string
* automatically mapping from one type to another is known as "implicit coercion"
    * [equality example](https://janke-learning.github.io/equalities-coercion/)
    * [arithmetic example](https://janke-learning.github.io/arithmetic-coercion/) 
* [pytut example](https://goo.gl/dznTAS)  


[TOP](#pythontutor-for-javascript)

---

## [expressions vs statements](https://github.com/janke-learning/expressions-vs-statements) 

* [helpful link](https://en.hexlet.io/courses/intro_to_programming/lessons/expressions/theory_unit)
* there is a very easy way to begin learning the difference between statements and expressions:
     * how many steps does PythonTutor take to execute your script?
* _Statements_: each step in PythonTutor corresponds to one statement in your code. 
    * semicolons can be used to mark the end of a statement
    * when you don't write semicolons, javascript will assume that new lines are new statements
    * [using semicolons will help find errors](https://goo.gl/evBwmZ)
* _Expressions_: each operator in a statement corresponds to an expression or sub-expression
* [basic example](https://goo.gl/jWCALS)
* [commas vs. semi-colons](https://goo.gl/ZyWQtk)
    * variable __declaration__ is a _statement_
    * variable __assignemnt__ is an _expression_
  

[TOP](#pythontutor-for-javascript)

---

## [Block Scope](https://github.com/janke-learning/block-scope)  

* [helpful link](https://www.youtube.com/watch?v=kw-mqezU4Dk)
* [basic block scope example](https://goo.gl/uZMQfd)  
* tricky bit: the [_temporal dead zone_](http://2ality.com/2015/10/why-tdz.html)  
    * the [lifecycle of a variable](https://dmitripavlutin.com/variables-lifecycle-and-why-let-is-not-hoisted/) is actually a bit more complicated than just _declaration_ & _assignment_, but before encountering block scope this was not relevant.  
    * [a basic tdz example](https://goo.gl/sKcs9K)  
    * [the tdz over-writes outer vars](https://goo.gl/DkoHGo)  
* [block scope & hoisting](https://github.com/janke-learning/block-scope-let-vs-var)


[TOP](#pythontutor-for-javascript)

---

## [complex expressions](https://github.com/janke-learning/complex-expressions) 

* [helpful link](https://github.com/janke-learning/expanding/blob/master/1-expressions.md)
* you can use many operators (sub-expressions) in a single expression
* they will all be _evaluated_ in [a predictable order](https://www.google.com/search?client=safari&rls=en&q=javascript+order+of+operations&ie=UTF-8&oe=UTF-8)
* to study and debug complex expressions, you can [expand](https://github.com/janke-learning/expanding/blob/master/1-expressions.md) them until there is only one operator per statement/line:
    * [hard-coded example](https://goo.gl/4X2Tt6)
    * [example with variables](https://goo.gl/GTXwyB)
    * [equality & coercion](https://github.com/janke-learning/equalities-coercion)
    * [arithmetic & coercion](https://github.com/janke-learning/arithmetic-coercion)  
* after some practice you may find that the [AST explorer](https://astexplorer.net/#/gist/e22d33e10f7c29268d5074803e35ced5/b63bf508b027cb7be2a27e8c6e841e12eac2fad4) helps you to expand and understand complex expressions


[TOP](#pythontutor-for-javascript)

---

## [truthiness & boolean operators](https://github.com/janke-learning/truthiness-boolean-operators)

* [helpful link](https://github.com/janke-learning/boolean-by-example)
* truthiness can be thought of as casting any value to boolean and checking if it's true or false  
      * [reference on pytut](https://goo.gl/jBTLFD)  
      * [exercise on pytut](https://goo.gl/YNqGJN)  
* this concept is necessary to understand _conditionals_ and _iteration_
* comparison operators:  
      * [&&, ||](https://goo.gl/BBXea6)  
      * [>, <, >=, <=](https://goo.gl/aZ3eKL)  
      * [==, ===](https://janke-learning.github.io/equalities-coercion/)  
      * [!](https://goo.gl/N2Eexv)  
* a big gotcha: [assignments where you meant comparisons](https://goo.gl/FK3U3q)


[TOP](#pythontutor-for-javascript)

---

## [conditionals](https://github.com/janke-learning/conditionals)

* [helpful link](https://javascript.info/ifelse)
* conditional statements allow you to execute different _blocks of code_ depending on the __truthiness__ of a given expression
* pythontutor snippets
    * [basic example](https://goo.gl/PfHDn2)
    * [with explicit type casting](https://goo.gl/v3W9SC)
    * [if, else if, else](https://goo.gl/xBTEfF)
    * [nested conditions](https://goo.gl/G71ecH)  
    * [conditional statement vs conditional expression](https://goo.gl/SJFCB5)
* consider using flow control visualization as well: [bogdon-lyashenko](https://bogdan-lyashenko.github.io/js-code-to-svg-flowchart/docs/live-editor/index.html) or [code2flow](https://code2flow.com/app)  (they're both good, but only code2flow has link-sharing. use the one you prefer)
    * [basic example](https://code2flow.com/sUE7zq)  
    * [with explicit type casting](https://code2flow.com/y6ulSm)  
    * [if, else if, else](https://code2flow.com/qWMjJY)  
    * [nested conditionals](https://code2flow.com/JNubrt)  
    * [conditional statement vs conditional expression](https://code2flow.com/40mM0c)
* [in-depth resource on boolean expressions & statements](https://github.com/janke-learning/boolean-by-example)
    

[TOP](#pythontutor-for-javascript)

---

## [iteration](https://github.com/janke-learning/iteration-with-primitives) 

* [helpful link](https://javascript.info/while-for)
* iteration allows you to execute the same block of code multiple times until a condition is truthy
* there are 3 types of loops in JavaScript:
    * [while loops](https://goo.gl/DBKR5u) 
    * [for loops](https://goo.gl/gr2XPX) 
    * [for vs while]()  
    * [do while loops](https://goo.gl/LdmLah)
    * [while vs do while](https://goo.gl/Gh3tEc)
* _for loops_ and _while loops_ are often talked about as though they are fundamentally different, but they're not:
    * you can always convert for's to while's & while's to for's: [equivalent for & while loops](https://goo.gl/vmpVJN)
    * notice that it takes the same number of steps (or statements) to complete one iteration for both loop types
* for-in & for-of loops are ordinary for loops, it's the "in" and "of" that are special.  more on that in [iterating over reference types](#iterating-over-reference-types).
* consider using flow control visualization as well: [bogdon-lyashenko](https://bogdan-lyashenko.github.io/js-code-to-svg-flowchart/docs/live-editor/index.html) or [code2flow](https://code2flow.com/app)  (they're both good, but only code2flow has link-sharing. use the one you prefer)
    * [while loops](https://code2flow.com/2sHaAP) 
    * [for loops](https://code2flow.com/8v3APb)  
    * [do while loops](https://code2flow.com/8CXmP9)  
    * [while vs do while](https://code2flow.com/K89RWz) 

[TOP](#pythontutor-for-javascript)

---

## [Reference Types](https://github.com/janke-learning/reference-types) 

* [helpful link](https://gist.github.com/colevandersWands/bb2ed4c61ba29c4b93ed7214797ecf60) 
* are stored [_by reference_](https://github.com/janke-learning/reference-vs-value).  variables _point_ to them in memory
* modifying one reference variable will effect all variables pointing to the same object in memory
* are "things that hold other things"
* functions, objects, arrays.  we'll cover functions later
* __objects__: data structures storing information with key-value pairs. item "name" will always be accessible by obj.name
    * [object properties](https://goo.gl/SctNHB) (for now we'll only consider objects storing primitives)
    * [objects and reference](https://goo.gl/vq38qx)
    * [dots vs. brackets](https://github.com/janke-learning/dots-vs-brackets) - this is conceptually very similar to reference vs value
    * object "methods" (functions stored in objects) will be covered in [free variables](#free-variables)
* __arrays__: data structures that store information in order. the first item is always arr[0], no matter what has happened 
    * [array entries](https://goo.gl/SoSRMA)
    * [arrays and reference](https://goo.gl/CG6uc6)
    * (you'll read about _array methods_ everywhere online - .slice(), .map(), .filter(), .reduce().  we'll cover those later.  right now the interest learning how arrays are managed in memory.)
* when to use arrays or objects is covered later in _data modeling_. 
* [a tricky example](https://goo.gl/wbBVSN)  
* [arrays, object & equality comparisons](https://goo.gl/EXJa4e)


[TOP](#pythontutor-for-javascript)

---


## [Iterating over reference types](https://github.com/janke-learning/iteration-over-reference-types)

* _for in_ and _for of_ loops are fundamentally the same as basic for loops, they just have more convenient sytax.  to make this point, these examples show how to convert from in/of to regular for loops:
    * [for-in loops (objects)](https://goo.gl/xhS36u) - notice that "in" is the same operator used to [check for properties in objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in)
    * [for-of loops (arrays)](https://goo.gl/dJ3gwS) - "of" is not an operator outside of for loops 



[TOP](#pythontutor-for-javascript)

---

## [Functions](https://github.com/janke-learning/functions)
* a new _frame_ is created each time a function is executed
* and closes when that function returns
* contain their own variables: args, local, free (not for now)
* have access to variable in parent (higher) frames
* cannot access variables in lower frames
* as: data (objects to pass & store with), routines


[TOP](#pythontutor-for-javascript)

---

## [Free Variables](https://github.com/janke-learning/free-variables)

* JS is a functional programming langague, and is easiest to understand if you learn it with FP vocabulary
    * JS is flexible enough to use OOP design patterns
    * and to talk about js programs in OOP vocabulary
    * but the notional machine is best understood functionally
* pull from https://github.com/janke-learning/comparadigms/

[TOP](#pythontutor-for-javascript)

---

## prototypical inheritance

* pull from https://github.com/janke-learning/comparadigms/



[TOP](#pythontutor-for-javascript)


---

to fit error handling.  
* after reference types? the first time you'll really have runtime errors
* after functions? than callstacks will make sense
* or twice? once to learn try/catch & errors.  and again to go deeper in errors?
    * or are erros better covered after prototypes?

___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
