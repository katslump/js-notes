# Advanced Javascript Notes

## OBJECTS 
    In javascript, it is said (almost) everything is an object.

    You have 1) primitives and 2) everything else

    Primitives:
    + Numbers
    + Strings
    + Booleans
    + Undefined
    + Null

    ^^^ NOT OBJECTS

    Everything Else:
    + Arrays
    + Functions
    + Objects
    + Dates
    + Wrappers for Numbers, Strings, Booleans

    ^^^ ALL OF THESE ARE OBJECTS

## CONSTRUCTORS AND INSTANCES

    Person 
    - name
    - yearOfBirth
    - job
    - calculateAge()

    In other languages... "class". In js they are CONSTRUCTORS
    You create instances of this constructor for Jane, John, and Joe.

## INHERITANCE
    When an instance inherits traits from another instance. 

    Athlete
    - olympics
    - olympicMedals
    - allowedOlympics()

    An athlete is also a person, so it INHERITS traits from the Person constructor when the instance is created.

    Athlete
    - olympics
    - olympicMedals
    - allowedOlympics()
    + name
    + yearOfBirth
    + isMarried
    + calculateAge()

## PROTOTYPES
    Inheritance works by using prototypes. JS is a prototype-based language.

    Each and every object has a prototype PROPERTY.
    The prototype property is where we want to store the properties and methods we want other objects to inherit.

## PROTOTYPE CHAIN
    john -> Person object -> Object object
    Null has no prototype.



## !!! IMPORTANT !!!!
    + Every JS object has a prototype property, which makes inheritance possible in JS.

    + The prototype property of an object is where we put methods and properties that we want other objects to inherit.

    + The Constructor's prototype property is NOT the prototype of the Constructor itself, it is the prototype of ALL instances that are created through it.
    !!!!!!!!!!!!!!!!!!!


    var john = {
        name: 'John',
        yearOfBirth: 1990,
        job: 'teacher'
    };

## FUNCTION CONSTRUCTORS

    var Person = function (name, yearOfBirth, job) {
        this.name = name;
        this.yearOfBirth = yearOfBirth;
        this.job = job;
    };

## INSTANTIATION

    Use the function constructor above to create a new John object

    var john = new Person('John', 1990, 'teacher');

    First an empty object is created (when NEW is called), then the function constructor is called. Then the "this" variable is pointed towards the new object that was created and sets them to the new variable.


## USING THE PROTOTYPE PROPERTY

    Person.prototype.calculateAge = function () {
        console.log(2018 - this.yearOfBirth);
    };
    
    john.calculateAge();
    
    Any instances created from the Person object will now have access to the calculateAge function.
    
    You can check this in the console. You will be able to see john -> Person -> Object
    
    
## CREATING OBJECTS using Object.create()
    
    Not used as much as the prototype property in JS.
    
## FIRST CLASS FUNCTIONS - passing functions as arguments

    Example:
    
    var years = [1990, 1965, 1937, 2005, 1998];
    
    function arrayCalc(arr, fn) {
        var arrRes = [];
        for (var i = 0; i < arr.length; i++) {
            arrRes.push(fn(arr[i]));
        }
        return arrRes;
    };
    
    function calculateAge(el) {
        return 2018 - el;
    };
    
    var ages = arrayCalc(year, calculateAge);
    console.log(ages);
    
    
## IMMEDIATELY INVOKED FUNCTION EXPRESSIONS (IIFE)
    
    Regular Function:
    
        function game() {
            var score = Math.random() * 10;
            console.log(score >= 5);
        }
        game();
    
    IFFE: 
    
        (function () {
            var score = Math.random() * 10;
            console.log(score >=5);
        })();
        
        
        How it Works:
            Tricks the parser into thinking we have an expression and NOT a declaration. If we werre to create a function without a name, the parser would through an error. The solution is to wrap the entire thing in paranthesis. Whats inside of paranthesis cannot be a statement in JS.
        
        Pros: 
            + Great for data privacy b/c of scope
            
## CLOSURES
    
    Rule
        The inner function always has access to the variables and params of its outer function, event after the outer function has returned. This has to do with the execution stack and scope chain.
        
    Example
        function retirement(retirementAge) {
            var a = ' years left until retiremenet.';
            return function(yearOfBirth) {
                var age = 2018 - yearOfBirth;
                console.log((retirementAge - age) + a);
            }
        }
        
        var retirementUS = retirement(66);
        retirementUS(1990);
        
    Result
        40 years left until retirement
        (2016 - (2016-1990))
    
    
## BIND, CALL, APPLY
    
    
    
    
    

    

    
    





















*/
