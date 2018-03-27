# GOING FORWARD
## A Creative Technologist's refresher and next steps

### Quick and Dirty Show: A brief review of objects

If you want to create more advanced programs as a creative technologist, you will want to be comfortable with making your own objects. Not physical (though that will come later), but digital. Objects inside of your programs. Instead of relying on things like strings, integers and floats, you’ll be making your own.

Which is something you will have most likely covered in your introductory programming classes. Lets review. Making your own “Ball” object class might include basic features:

* Position in space
* Size
* Speed
* Ability to move
* Ability to be seen

I like to think of these as adjectives and verbs.

Some things describe the state of the thing: It’s big, it’s slow, its off in the distance. These are adjectives. They are made by defining variables of an object.

This may start out looking like:

```
function Ball() {
  this.x = random(width);
  this.y = width/2;
  this.diameter = random(100, 400);
  this.speed = 1;
```

X, Y, diameter, speed. This is the start of our Ball constructor. And in Javascript, we use the “this.variable” convention when making our blueprints for a new object inside of our constructor.

This can be seen again as we continue on to the verbs. These are things that each instance of the object can do: it exists, it moves.

```
this.move = function() {
    this.x += this.speed;
  };

  this.display = function() {
    ellipse(this.x, this.y, this.diameter, this.diameter);
  }
```

To make the ball even be seen, we will wind up doing things like this when we are inside of our draw loop:

```
myShinyNewBall.move();
myShinyNewBall.display();
```

---

### A tour of my personal object

Creating the concept of a ball, and then making a shiny new ball for yourself. It reminds me of being a kid. You realize that there is such a thing as a ball. You find out what it is and what it can do. And then you want one for yourself. Naming an object, defining its qualities, and then making a variable with it.

But we know children will grow bored of their toys. No matter what, it seems that they always lose their luster. Or maybe it is us that changes, our way of looking. I’m not sure I always see the shine like I used to.

Things have changed, for better and worse. I would love to take a look at the world through those young eyes again, but only for a while. Who would *really* want to be a kid again permanently? It’s just concerning that the further forward you go, the more likely you are to forget what it was like back then. Can I go forward, and still remember how I felt way back when? I don’t want to be enamoured with the shiny ball, trapped by its allure. But I do want to remember the way it made me feel.

<br>

These are not the feelings I see in usual object constructors. Usually we see traditional taxonomies: A flock contains a number of birds, a bird has a color and speed and number of feathers, and so on. But our objects, their variables, and their functions can be named whatever we like. Maybe we can communicate more about ourselves instead.

---
### What would you like to do?

**Casual Activity:**
Below is a piece that is a representation of my life, as I feel about it in this moment. Feel free to take a look at the code to see how the object is created, used, and then modified by various functions.

**Curious Activity:**
If you would like to tell your own life story, take a look at how the diameter, speed, color, outsideColor, and ourWalls properties are changed. Feel free to make your own version. Let me know if you’d like to share it with me to use for my documentation, or simply just describe the thoughts behind your life objects to someone else here.

**Creative Activity:**
Or, change the whole narrative! Isn’t there more to life than just age? Why is time described as going from left to right? Do you feel like more of a square than a circle? Feel free to modify, remove, or add as much as you need to tell your life story.

<br>

Here is my story:
<br>
( Also, you can look at and run the code here: [my story's online editor link](http://alpha.editor.p5js.org/dbarrett/sketches/HJrgl6Uqz) )

```
/*
Originally inspired by
https://p5js.org/examples/objects-objects.html
*/


var me;  // Declare variable

function setup() {
  createCanvas(800, 400);
  
  // This variable type is that of the object we will create
  me = new You();
}

function draw() {
  background(10, 10, 100, 5); //R,G,B,A, with low alpha for blurring
  
  //We move. We exist.
  //(These are defined in the constructor after our draw loop)
  me.move();
  me.display();
  
  //We go through life.
  life(me);
  
}


//Creating our object
//a you
function You() {
  
  //
  this.diameter = random(10, 30);
  
  //Life has to start somewhere
  //In this case, the left side of the screen
  this.x = 0;
  //fixed to middle height, to lead a balanced life
  this.y = height/2;	
  
  //What is our color?
  //No, not on the surface. Deeper.
  this.color = color(255,255,255);
  this.outsideColor = color(255,255,255);
  this.ourWalls = 1;
  
  //The longer you live, the faster life seems to go
  //But time doesn't change, you do. How fast are you going?
  this.speed = 1;

  //And where are you headed?
  this.move = function() {
    this.x += this.speed;     //move x
    this.x = (this.x%width);     //limit x to size of the canvas
  };

  //It seems funny to me that "existing" needs to be a verb
  //But hey, sometimes life is more difficult than we like
  //Haven't you ever felt the most basic things were an effort?
  //Or "not all there?" 
  this.display = function() {
    strokeWeight(this.ourWalls);
    stroke(this.outsideColor);
    fill(this.color);
    ellipse(this.x, this.y, this.diameter, this.diameter);
  }
}




//Life.
//Life Function
//A thing that you go through
//You come in one side and come out the other
//It changes you


function life(people){
  //I'm thinking about a life time: Youth, Adolesence, Adulthood
  //If our position in life is in the first third, we are children
  //Second third, teenagers
  //Last third, adults
  
  if(people.x < width/3){
    youth(people);
  }
  else if (width/3<=people.x && people.x<2*(width/3)){
   	adolesence(people); 
  }
  else
  {
    console.log("We should be in adulthood. Right? What else is there, I guess...");
		adulthood(people);
  }
  //maybe these distinctions are out dated
  //or maybe they fit, but our concept of them should change
  
  //Having trouble with life? Try these debugging messages:
  //console.log("what is life telling us?");
  //console.log("Our position in life: " + people.x);
}


//But life isn't just "LIFE", ya know? Its made up of different things
//So each of those things needs to be defined

function youth(people){
  if(people.diameter){//are we dealing with a person?    
     people.diameter = 10;
    
     people.speed = 0.66;
     people.outsideColor=color(220,220,0);
     people.ourWalls = 0.5;
     return;}
  else{//if we're not dealing with a person, we don't use this function
    	//this prevents errors, as we're setting qualities unqiue to the object type "you"
    	//The number 17 didn't have a childhood, so this function doesn't apply to it
    	//Which sounds kind of sad for the number 17, but that is a bit of a distraction for right now
  return}
}

function adolesence(people){
  if(!people.diameter){//if we aren't dealing with a You class
    									//the "!" in this if statement means "not"
    									//Same type of results as above, we're just defining things in the negative
    									//Which sounds very adolesent to me
    	console.log("this isn't you, is it?");
     return}
  else{
    people.outsideColor=color(175,20,255);
    people.ourWalls = 2.5;
    
    //Our color on the inside. Our true color.
    people.color=color(22,22,100);
    
  	people.diameter += 0.2;
    //I grew over time
    
    
    
  	return people;
  }
}

function adulthood(people){
  //and all of a sudden I was an adult before I knew it
  
  if(people.diameter){//are we dealing with a person?    
     people.diameter = 125;
     people.speed=1.66; //where does the time go?
    
     people.color=color(188,188,255);
     people.outsideColor=color(255,11,175);
     people.ourWalls = 1;
    
     return;}
  else{
    
  return}
}

```
