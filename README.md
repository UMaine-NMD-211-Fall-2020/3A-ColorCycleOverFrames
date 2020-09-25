# 3A-ColorCycleOverFrames
In this lab we track the passage of time by looping colors over changing frames.

## Goals:
- Understand that each frame is one loop through draw
- Use frame changes to measure passing time
- Change colors at certain times
- If statements
- (Optional) Make colors change over an object

## Turn In
A variation of my code, that shows you played with the values. This variation should include
- color changing background over time ... need not be continuous
- some sort of color changing shape, not synchronized with the background and shape. This may mean you need a second rate of change
- some sort of color changing outline, not synchronized with the background, can be synchronized with the shape
- extra (disappearing or appearing elements, such as a square that is only around part of the time)

It's probably a good idea to use objects/ classes for parts of this.
## Constructing Code
### Setup Code
1. Start your file
```processing
/*  Lab 3A - NMD 211
    FirstName LastName
    September 23, 2020
    
    
    Color Cycle Lab
    - Systematically loop through colors over frames, changing one value at a time
*/
```
Add whatever else you think is relevant to your introductory comment section.
This includes: what your code does, anything special, what you didn't understand, if you referenced certain code
2. Initialize your file, with a setup function and a draw function.
``` processing
/*  Lab 3A - NMD 211
    FirstName LastName
    September 23, 2020
    
    
    Color Cycle Lab
    - Systematically loop through colors over frames, changing one value at a time
*/
void setup(){
    size( 500 , 500 );
}

void draw(){
    background( 0 , 0 , 0 );
}
```
### About passage of time
One way to count time in processing is by the number of frames that has passed. 
Each run through draw is one frame. 
We will make a counter that counts the number of runs through draw, to show the passage of time. 

3. We need to add a variable that keeps track of time.
``` processing
/*  Lab 3A - NMD 211
    FirstName LastName
    September 23, 2020
    
    
    Color Cycle Lab
    - Systematically loop through colors over frames, changing one value at a time
*/

// --- CHANGE HERE
int framesSeen = 0;
// --- END CHANGE

void setup(){
    size( 500 , 500 );
}

void draw(){
    background( 0 , 0 , 0 );
}
```
4. Increment the counter (add one to the counter each pass through draw).
``` processing
/*  Lab 3A - NMD 211
    FirstName LastName
    September 23, 2020
    
    
    Color Cycle Lab
    - Systematically loop through colors over frames, changing one value at a time
*/

// --- CHANGE HERE
int framesSeen = 0;
// --- END CHANGE

void setup(){
    size( 500 , 500 );
}

void draw(){
    background( 0 , 0 , 0 );
    
    framesSeen += 1;            // increase the number of frames seen
    print( framesSeen , "\n");  // show number of frames seen
}
```
### If Statements & Color changes
Using an if statement, along with else if and else, we can have colors change once we reach a certain number of frames seen.
5. When we have seen more than 500 frames,  change the background color.
``` processing
/*  Lab 3A - NMD 211
    FirstName LastName
    September 23, 2020
    
    
    Color Cycle Lab
    - Systematically loop through colors over frames, changing one value at a time
*/

// --- CHANGE HERE
int framesSeen = 0;
// --- END CHANGE

void setup(){
    size( 500 , 500 );
}

void draw(){
    
    if (framesSeen < 500 ){
        background( 0 , 0 , 0 );
    }
    else {
        background( 255, 255, 0 );
    }
    
    framesSeen += 1;            // increase the number of frames seen
    print( framesSeen , "\n");  // show number of frames seen
}
```
### Cycling Through Colors
We use a combination of if statements and incrementing variables to cycle through the colors. 
6. 
``` processing
/*  Lab 3A - NMD 211
    FirstName LastName
    September 23, 2020
    
    
    Color Cycle Lab
    - Systematically loop through colors over frames, changing one value at a time
*/

// --- CHANGE HERE
int framesSeen = 0;

int backgroundRed = 0;
int backgroundGreen = 0;
int backgroundBlue = 0;

// --- END CHANGE

void setup(){
    size( 500 , 500 );
}

void draw(){
    
    if (framesSeen < 500 ){
        background( backgroundRed , 0 , 0 );
    }
    else {
        background( 0 );
    }
    
    // incrementations
    framesSeen += 1;            // increase the number of frames seen
    backgroundRed += 1;         // increase the red value each run
}
```
This increments us through red, but it goes past the maximum value of red, so we may have problems later if we want to decrease the red value.
Therefore, we construct a function that only increases red to the maximum of 255, and use that. 

## FURTHER STEPS TO BE ADDED TOMORROW
## Katarina's Example 2 End Code
This code only shows how to loop through colors. 
```processing
int r;
int g;
int b;

int timeT;

int[] changeArray= {  0, // black 
                  255, // red r
                  510, // orange yellow- rg
                  765, // green g
                  1020,// green blue gb
                  1275, // blue b
                  1530, // magenta rb
                  1785, // white rgb
                  2040 // grey
                };

void setup(){
  size( 500 , 500);
  
  // initialize colors
  r = 0 ;
  g = 0 ;
  b = 0 ;
  
  timeT = 0;
  
}
void draw(){
  background( r , g , b);
  
  if ( timeT % changeArray[8] < changeArray[1] ){
    // black -> red
    redUpCycle();
  }
  else if ( timeT % changeArray[8] < changeArray[2] ){
    // red -> orange -> yellow
    greenUpCycle();
  }
  else if ( timeT % changeArray[8] < changeArray[3] ){
    // yellow -> green
    redDownCycle();
  }
  else if ( timeT % changeArray[8] < changeArray[4] ){
    // green -> turquoise
    blueUpCycle();
  }
  else if ( timeT % changeArray[8] < changeArray[5] ){
    // turquoise -> blue
    greenDownCycle();
  }
  else if ( timeT % changeArray[8] < changeArray[6] ){
    // blue -> magenta
    redUpCycle();
  }
  else if ( timeT % changeArray[8] < changeArray[7] ){
    // magenta -> white
    greenUpCycle();
    blueUpCycle();
  }
  else if ( timeT % changeArray[8] < changeArray[8] ){
    // magenta -> white
    redDownCycle();
    greenDownCycle();
    blueDownCycle();

  }
  else{
    r = 0;
    g = 0;
    b = 0;
  }
  
  timeT += 1; // increase time
}

/* Helper Functions */

void redUpCycle(){
  if (r < 255){
    r += 1 ;
  }
}
void redDownCycle(){
  if (r > 0){
    r -= 1 ;
  }
}
void greenUpCycle(){
  if (g < 255){
    g += 1 ;
  }
}
void greenDownCycle(){
  if (g > 0){
    g -= 1 ;
  }
}
void blueUpCycle(){
  if (b < 255){
    b += 1 ;
  }
}
void blueDownCycle(){
  if (b > 0){
    b -= 1 ;
  }
}
```

## Submit Via Github
For those of you who want to submit this lab via Github, submit below by adding a link to your github repository for the lab. 
- [Lab3A-FirstNameLastName](http://example.com)

