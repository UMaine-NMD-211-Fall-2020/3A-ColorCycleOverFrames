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
## Setup Code
1. Start your file
```processing
/*  Lab 2B - NMD 211
    FirstName LastName
    September 23, 2020
    
    
    Color Cycle Lab
    - Systematically loop through colors over frames, changing one value at a time
*/
```
## FURTHER STEPS TO BE ADDED TOMORROW
## End Code
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


