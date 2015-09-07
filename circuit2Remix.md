# cs 110 Circuit 2 remix challenge

### we are practicing
* using a potentiometer
* wiring multiple LEDs
* using if-else statements

### hint
Consider the following code

     if (grade > 90){
         digitalWrite(blueLED, HIGH);
      }
      else if (grade > 80){
          digitalWrite(greenLED, HIGH);
      }
      else {
          digitalWrite(redLED, HIGH);
      }


when we get to the

     else if (grade > 80)
     
line one thing we already know is that the grade is less than or equal to 90. If it was greater than 90 we would have turned on the `blueLED` and skipped over the else.   Knowing this greatly simplifies our code. 

There is no need to write something more complex like *if grade is less than 90 and greater than 80* or in code

     if ((grade < 90) && (grade > 80)){
     
 that && means *and*
 
 Okay here are the challenges.  When you code, start with remix 1 and make sure that works before going on to remix 2. When you demo, just demo the last one you accomplish.
 
 
 For all these you will have 2 LEDs.

NOTE: when you turn the potentiometer to switch patterns it may not have an immediate effect but take a moment to change.

### Remix 1 (20xp)
When the potentiometer is in the lower half of its range the lights are in the *alternatingly blinky* pattern and when it is in the upper half  the lights are in the waltz pattern.

### Remix 2 (+15xp)
The potentiometer range is in thirds. The three patterns are
* alternatingly blinky
* waltz
* slow n fast

### Remix 3 (+15xp)
The range is in fourths. Add you own pattern as an addition to the three in remix 2.

### 50 xp possible

### Bonus  remix (+25xp)
Can you have the potentiometer control 3 LEDs  (and invent some 3 LED patterns). 

