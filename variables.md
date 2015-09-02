
## variables
There are three things you can do with a variable:

#### 1. declare it

    int redLED = 13;
    
In a declaration there are three parts. On the left of this line we have `int`. This tells us the variable's **type**. The `int` says that this variable will contain an integer. Other types include `float` for decimal numbers (12.25) and `char` for characters (a, b, c, as examples).

The next item on the line is `redLED` and this is the variable's name. We can make up any name we want. (There are some limitations like the variable should start with a letter.)  The name really doesn't matter to the computer. So

    int redLED = 13;
    int blueLED = 7;
    
and 

    int x = 13;
    int y = 7;
    
and 

    int led13 = 13;
    int led7 = 7;
    
and 

    int myCoolVariableName = 13;
    int myOtherCoolVariableName = 7;
    
are all fine. The convention is to pick a name that helps you, the human. So, `redLED` and `blueLED` might be the best bet.

The final component on the line


    int redLED = 13;
   
is the value we are setting the variable to. 13 in this case. So this line might be said in English *Remember that the name redLED refers to the integer 13*. 

We can declare a variable without setting a value:

    int currentLED;
    
What this does is to tell the computer to remember the variable name currentLED and that it will contain an integer and later in the code we will set its value (more on that later)


#### 2. get a variable's value
We can get the value by just using the variable's name:

    int redLED = 13;
    pinMode(redLED, output);
    digitalWrite(redLED, high);

So where ever the computer sees `redLED` it looks up the value (13 in this case) and replaces `redLED` with its value. So

    pinMode(redLED, output);

is replaced with

    pinMode(13, output);
    
##### scope
Here are a few other things you need to know.

##### global scope
If you declare a variable at the top of your file (before the function setup, for example), those variables can be used anywhere in your program.

So in:

    int blueLED = 7;
    int redLED = 13;
    int dot = 300;
    
    void setup()
    {
       pinMode(blueLED, OUTPUT);
       pinMode(redLED, OUTPUT);  
    }
    
    void loop()
    {
     
      digitalWrite(blueLED, HIGH);   // Turn on LEDs
      digitalWrite(redLED, HIGH); 
      delay(dot);                    // wait 
      digitalWrite(blueLED, LOW);    // Turn off LEDs 
      digitalWrite(redLED, LOW);    
      delay(dot);                    // Wait 
    }

we declare blueLED at the start of the program and it can be used in both the `setup` and `loop` functions. That means the the computer will know that `blueLED` refers to the integer 7 throughout the code. (and will know that `redLED` refers to integer 13 throughout the code, and `dot` to 300)
    
##### local scope
The other rule is that if you define a variable within a code block (meaning a set of instructions within braces {} ), the variable is only remembered within that code block.

So if we do something like


    
    
    void setup()
    {
       int blueLED = 7;
       int redLED = 13;
       int dot = 300;
       pinMode(blueLED, OUTPUT); // the computer knows that blueLED = 7
       pinMode(redLED, OUTPUT);  // the computer knows that redLED = 13
    }
    
    void loop()
    {
     
      digitalWrite(blueLED, HIGH);   // The computer never heard of 
      digitalWrite(redLED, HIGH);    // blueLED or redLED
      delay(dot);                   // nor dot
      digitalWrite(blueLED, LOW);   // and will complain
      digitalWrite(redLED, LOW);    
      delay(dot);                    // complain 
    }


When you run this you will get the error

    'blueLED' was not declared in this scope
    
It is good programming style to follow a **need to know** frame of mind. If you are only going to use a variable in `setup` for example, it is best to declare it there since `loop` doesn't need to know about it. We will see an example of this shortly.

#### 3. setting the value of a variable

Once we declare a variable we set its value by using the syntax:

     currentLED = 7;
     
This should look familar from math classes where you might have something like:

    x = 5
    
 and the instructor would say something like *let x equal 5*. So with the `currentLED` example we might say *let currentLED equal 7*
 
 The example that started this page:
 
    int redLED = 13;
   
 is equivalent to
 
    int redLED;
    redLED = 13
    
   
 We can do things like
 
     int redLED;
     redLED = 9 + 3;
 
 and
 
  
     int redLED;
     int blueLED;
     redLED =7;
     blueLED = redLED + 2;  

and even

      int wait = 100;
      wait = wait + 10;

Now the new value of wait is 110. This might seem odd so let's look at an example:

	int led = 13;
	int waitTime = 100;
	int adjust = 50;
	
	// the setup routine runs once when you press reset:
	void setup() {                
	  // initialize the digital pin as an output.
	  pinMode(led, OUTPUT);     
	}
	
	// the loop routine runs over and over again forever:
	void loop() {
	  digitalWrite(led, HIGH);   
	  delay(waitTime);         
	  digitalWrite(led, LOW);   
	  delay(waitTime);          
	  waitTime = waitTime + adjust;
	}


What do you think that code does? Take a moment and puzzle it out.


###### the answer
It blinks the led slower and slower.

The first time through the loop `waitTime` is 100 and `adjust` is 50 and when we execute

    waitTime = waitTime + adjust;
    
the waitTime and adjust variables get replaced by their values
    
    waitTime = 100 + 50; // wait time is now 150

So the new value of waitTime is 150. 


