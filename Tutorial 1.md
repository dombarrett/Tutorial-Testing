# Dominic's Test Tutorial 1

Hi! You’ve chosen to do this tutorial because you are either interested in upping your creative coding skills, need a little bit of review, or want some fresh coding ideas to get the creative juices flowing. Maybe all three!

Today we’re going to be working in p5js, with the online editor that can be found here:
http://alpha.editor.p5js.org/

These concepts can be brought to other coding languages and environments. But for the sake of quickness and ease of access, we’ll stick with p5js’ online editor for now.

# Lets talk about randomness

One way to spice up your creative coding routine is to utilize randomness. You have most likely gone over randomness if you’ve done an intro class on p5js. To review, lets run the following sketch in the editor:

```
function setup() { 
  createCanvas(400, 400);
} 

function draw() { 
  background(220);

console.log(random(10));
}
```

## Casting

What do you see in the console log below? If you are like me, it probably wasn’t what you expected. Numbers like 4.175331827086781, 3.897960047946547, 9.28875200600597, and so on. We do a basic review of what we already know, and already we are getting curve balls!? What gives, p5js?

p5js is giving us floats, that's what gives. You know this one: a float is a number that has a decimal point in it. But if we wanted to make a game that guessed your lucky number, we probably wouldn’t want those crazy fractions. Unless your lucky number happens to be 9.28875200600597.

For the rest of us normal, boring people, we want numbers without decimal points. We can force p5js to convert this number into a whole number, or integer. This is called “casting”, as in, “You cast the incoming number as an integer.” This terminology is not unique to p5js or Javascript, and as a general programming term.

So to “cast as an int” (all the cool kids say int instead of integer), you would wrap our random call around the int() function like so:
```
console.log(int(random(10)));
```
Now lets move that line up into the setup function, which only runs once. Before you run the code, you think of your lucky number between 0 to 10. Your press the run button and… you didn’t get your lucky number!

Unless you did. But most of you probably didn’t, and maybe for a brief second you thought I was reading your mind. Nope. Just playing the numbers. Also, if your lucky number was 10, you definitely didn’t get it. That’s because when we cast a float as an int, we are simply discarding everything after the decimal point. No rounding up or anything like that. Try putting the following into your sketch:
```
console.log(int(9.9));
```
You’ll see “9” come up in your console. The .9 is simply discarded. So, to compensate for this, we could change our line to:
```
console.log(int(random(11)));
```
We’ll see some 10s come through on the console. But also some zeros. And if your lucky number is zero, I commend your edgy gothness. However if we were framing our question as, “Pick a number 1 through 10”, we would want to make a range. In this case, you add an extra argument to the random function.
```
console.log(int(random(1,11)));
```
This picks a random number starting at 1, leading all the way up to 11 as the limit that never gets touched. So, you could get 10.999999999, but because you cast it as an int it still turns into 10.


But this isn’t good enough for you. You don’t sit through life *waiting* for your lucky number to come through. You are a programmer. You *make* your own luck. But how, you wonder?

## Random Arrays

Try this:
```
function setup() { 
  createCanvas(400, 400);
  
  oneThroughTen = [1,2,3,4,5,6,7,8,9,10];
} 

function draw() { 
  background(220);
  
  console.log(random(oneThroughTen));
}
```
No floats, no int casting, no 11’s. Otherwise, similar functionality of the last number picker. But it looks different to you. What’s going on?

The p5js function random() doesn’t just pick random numbers. Nor is it limited to picking random numbers within a range. It also picks randomly from an *array* of numbers. This means that you can weight the scales in your favor. Try this:
```
oneThroughTen = [1,2,3,4,5,6,7,7,7,7,7,7,7,7,7,8,9,10];
```
There are nine other numbers besides 7, so if you put in nine 7’s you should be seeing a 7 show up around 50% of the time.


“How can I use this besides create an extremely unethical gambling startup?” you wonder. Well, today is your lucky day. And if it isn’t, just throw a few more 7s into that array. Because random() doesn’t just pick randomly from an array of numbers, but can pick randomly from an array of *anything*.

Take colors for instance. Let’s start our program like this:
```
//color choices
var color1;
var color2;
var color3;
var color4;

//an array to hold all of the colors
var colors;

function setup() { 
  createCanvas(400, 400);
  
  color1 = color(255,255,255);
  color2 = color(0,255,255);
  color3 = color(255,0,255);
  color4 = color(255,255,0);
  
  equalColors = [color1,color2,color3,color4];
  
  mostlyColor2 = [color1,color2,color2,color2,
            			color2,color2,color2,color2,
            			color2,color2,color3,color4];
  
  mostlyColor3 = [color1,color2,color3,color3,
           				color3,color3,color3,color3,
            			color3,color3,color3,color4];
  
  mostlyColor4 = [color1,color2,color3,color4,
            			color4,color4,color4,color4,
            			color4,color4,color4,color4];
  
  colors = equalColors;
  
} 
```

You have four colors: white, cyan, magenta, and yellow. You’ve made four arrays with randomness in mind: even odds, mostly cyan, mostly magenta, and mostly yellow. Now you can add the second half of the program:
```
function draw() { 
  background(75);
  
  for(i=0;i<4000;i++){
  	fill(random(colors));
    	noStroke();
  	rect(random(width),random(height),10,10);
  }

}

function keyPressed(){
  if(key==1){
    console.log("keypressed 1");
    colors = equalColors;
  }
  if(key==2){
    console.log("keypressed 2");
    colors = mostlyColor2;
  }
  if(key==3){
    console.log("keypressed 3");
    colors = mostlyColor3;
  }
  if(key==4){
    console.log("keypressed 4");
    colors = mostlyColor4;
  }
  
}
```
Here we are drawing 4,000 squares on the screen every frame. The squares are 10 pixels in size and placed in random locations within the bounds of the width and height of the sketch. Press the 1,2,3, and 4 buttons on your keyboard to cycle through the different modes of probability.


## Random *Anything!*

And it doesn’t stop at colors. You can have randomized text as well, because you can put strings into an array just as easily.

You’ve done a good job following along so far. So I’m going to give you an example sketch to play around with instead of talking you through everything again, except with text. Needless to say, you’ll see some of the same strategies being employed. Take this time to change the variables, colors and text to something that you like and has your artistic vision.

```
//color choices
var color1;
var color2;
var color3;
var color4;

//an array to hold all of the colors
var colors;

var displayText;

var textChoices = ['good ','smart ',"really hoping this will be useful."+
"Or, not useful, but maybe just something that turns out to be inspiring."+
"Something that resonates, ya know?"+
"I keep having this compulsion to make art with technology."+
"But how great has it been, *really*?"+
"Maybe this will be it, or the start of the it, that gets me to that level."+
"Or, place."+
"I should say place."+
"Level implies something else."+
"\n"+
"Just like the word useful implies something else."+
"Hierarchy, merit, productivity."+
"Thats not why I wanted to make things with computers."+
"But… maybe if I had focused on the more practical things, I’d be a better coder."+
"And then I wouldn’t have to look to books to help me."+
"Why didn’t I pay more attention in math class?"+
"Why didn’t I have parents that pushed me too hard to be good at math?"+
"\n"+
"But then some of those math people say the same thing to me about knowing other things."+
"Now that I think of it, most thoughtful people I know will at least occasionally wonder things like that."+
"Grass is greener on the other side, I suppose."+
"Its just a shame to think that my friends would think that their talents aren’t ",'good ','smart ','good ','smart ','good ','smart ','\n\n'];

function setup() { 
  createCanvas(400, 400);
  
  color1 = color(255,255,255);
  color2 = color(0,255,255);
  color3 = color(255,0,255);
  color4 = color(255,255,0);
  
  equalColors = [color1,color2,color3,color4];
  
  mostlyColor2 = [color1,color2,color2,color2,
            			color2,color2,color2,color2,
            			color2,color2,color3,color4];
  
  mostlyColor3 = [color1,color2,color3,color3,
           				color3,color3,color3,color3,
            			color3,color3,color3,color4];
  
  mostlyColor4 = [color1,color2,color3,color4,
            			color4,color4,color4,color4,
            			color4,color4,color4,color4];
  
  colors = equalColors;
  
  displayText = "I am " + random(textChoices) + "enough";
} 

function draw() { 
  background(75);
  
  for(i=0;i<4000;i++){
  	//fill(color1);
  	fill(random(colors));
    noStroke();
  	rect(random(width),random(height),10,10);
  }

  
  textSize(100);
  textFont('Helvetica');
  stroke(255);
  strokeWeight(5);
	text(displayText, 25, 25, width, height);
  
}

function keyPressed(){
  if(key==1){
    console.log("keypressed 1");
    colors = equalColors;
    displayText = "I am " + random(textChoices) + "enough";
  
  }
  if(key==2){
    console.log("keypressed 2");
    colors = mostlyColor2;
    displayText = "I am " + random(textChoices) + "enough";
  
  }
  if(key==3){
    console.log("keypressed 3");
    colors = mostlyColor3;
    displayText = "I am " + random(textChoices) + "enough";
  
  }
  if(key==4){
    console.log("keypressed 4");
    colors = mostlyColor4;
    displayText = "I am " + random(textChoices) + "enough";
  
  }
  
}
```
