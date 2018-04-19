Colors. Sound. Considering how we can break down our concepts into discrete elements and objects. This may have been a review for some of you, but hopefully there have been some novel ways of approaching creativity that are useful for everyone.

## To review:
So far I’ve talked about how to spice up simplistic examples you have come across in your introductory materials. There has been some discussion about “mapping”, “scaling” or general translating of values for various purposes. I’ve done a brief review of objects. I’ve talked about the importance of reading documentation, encouraged you to write and read code comments, and tried to push you to copy/paste/modify without strict step-by-step instructions.

I’m now going to recap these themes with another small program. This should be similar to something you may have made already in your intro programming courses. Now we’re going to make bouncing balls. In the previous review of objects, we might not have *really* needed to make the ball an object. But this time we definitely need one.

We want to make lots of bouncing balls. We want things to happen every time each individual ball bounces. We want them to each to live a certain amount of time, and then disappear. We want gravity to affect them. We never expected some bouncing balls to demand so much! This is a classic use case for an object.

Instead of going through piece by piece or building this from scratch again, I’m just going to give you a fully functioning sketch. The comments will serve as a guide to what is going on:


```javascript
/*
duplicated with much love from the bouncing ball example
in my Introduction to Computational Media class

re-worked, extended, and otherwise mangled the ball object to add;
constructor, sounds, lifespan, etc.
*/


var balls = [];   //array to contain ball objects
var gravity = 0.1;   //gravity

function setup() {
  createCanvas(400, 300);
  
  //start with a single ball
  //i've set up a for loop for you in case you want more
  
  for (var i=0;i<1;i++){
  	balls[i] = new Ball(random(width),random(height),24);
    //a sized 24 ball is placed in a random position
  }
}

function draw() {
  background(0);
  
  /*every frame, we need to:
  		1) show
  		2) move
  		3) check for a bounce
  		4) decide whether to remove the ball
  	For every ball in the array of balls
  */
  
  for (var i = balls.length-1; i>=0;i--){
    balls[i].display();
    balls[i].move();
    balls[i].bounce();
    
    if(balls[i].isFinished()){
    	console.log("finished: removing a ball");
    	balls.splice(i,1); 
    }
    
  }
}

function mousePressed(){
  //When we press the mouse button
  
  //we add a new ball object to the balls array
  //at the location of the mouse, with a width of 24
  balls.push(new Ball(mouseX,mouseY,24));

  //How many balls do we have?
  console.log("length="+balls.length);
}



//The Ball object
function Ball(_x,_y,_size) { //<-- "_x,_y,_size" are construction arguments
  //in order to create a ball, these three things have to be defined
    
  //Position, size, and speed of the ball
  this.x= _x;
  this.y= _y;
  this.size= _size;
  this.speed= 0;    //some object properties can be set by default
  //(they don't have to be required constructor arguments)
  //in this case, all balls start with a speed of zero
  
  //How long should the ball exist
  this.lifespan=10*60;
  //Time will be measured in frames
  //assuming 60 frames per second
  //10*60 = 10 seconds
  
  //volume of the sound
  this.volume=1;
  //level of transparency
  this.alpha=255;
  
  //the sound file
  this.ballSFX = loadSound('piano.mp3'); 
  
  //the speed at which we will play back the sound file
  //this number is linked to where the ball is inside of the sketch:
  //bounces on the left side are deeper, slower
  //bounces towards the right are higher, shorter
  this.sfxSpeed=this.x;
  this.sfxSpeed=map(this.sfxSpeed,0,width,0.01,4);
  
  //show us the ball (will be called every frame)
  this.display = function() {
    //the alpha transparency will fade until the ball is destroyed
    this.alpha=map(this.lifespan,0,300,0,255);
    fill(255,this.alpha);
    ellipse(this.x, this.y, this.size, this.size);
    
    //the speed of the sound playback
    //is assigned to the sound file
    this.ballSFX.rate(this.sfxSpeed);
  };
  
  //move the ball (will be called every frame)
  this.move = function() {
    //The ball moves and is effected by gravity
    this.y = this.y + this.speed;
    this.speed = this.speed + gravity;
    
    //the volume of the sound effect gets quieter as is fades out
    this.volume=map(this.lifespan,0,this.lifespan,0,1);
    console.log("mapped vol:" + this.volume);
		this.lifespan--;
  };
  
  //bounce the ball (will be called every frame)  
  this.bounce = function() {
    //is it time to bounce the ball?
    if (this.y > height) {
      //slow down the speed of the ball over time
      this.speed = this.speed * -0.97;
      
      //play the sound effect when we bounce
      this.ballSFX.play();
      
      //change the volume of the sound
      this.ballSFX.setVolume(this.volume);
      /*In theory, we could call this every frame, right?
     	  Though, we are only hearing the difference in volume
    	  every time the ball bounces.
        So why make changes to each object more times than we have to?
        We will set it here in the bounce function.
      */
      
      console.log(this.volume);
    }
  };
  
  //is it time for the ball to go?
  //this will be checked every frame
  this.isFinished = function(){
    if (this.lifespan<0){
      return true;
    } else{
     	return false; 
    }
  };
    
}
```

You can find this p5 sketch online here:
http://alpha.editor.p5js.org/dbarrett/sketches/rkqd5uT9M

If you want to re-create this yourself or run it locally, you will need to have a sound file named “piano.mp3” in the same directory as the sketch.

### Things you can do:

**Casual:** Read through the code, then run it. Does it do what you expected it to do? Can you copy and paste the code somewhere else and have it run? In the online editor? What about the offline editor? Have you tried using text editors (Atom, Sublime, etc) to develop p5 sketches? Now could be a good time to practice.

**Curious:** Sure are a lot of variables. You could change all of them! And I made the balls plain ol’ white. How boring. You certainly would want to change that. And what's the deal with the piano noise? Surely something else could go in there.

**Creative:** You’ve changed the variables. Always fun. How about adding variables? What if you made each ball a *different* color by giving them their own color variables? Or change the functions. Could the creation of a ball and the destruction of a ball trigger new functionality? Maybe add a function. Setting multiple variables at once could done with one function (new color, size, and sound all in one command).

**Challenge:** But you said there’d be no challenges! Well, there are no *required* challenges. But I know some of you. You want to be pushed. You want something specific. All this artsy feel good mumbo jumbo just isn’t doing it for you. Ok ok, I get it.

How about the following as a challenge? I probably could have made the lifespan a variable that was set in the Ball constructor, like the x, y, and size variables. Make lifespan a required variable when creating a ball object. Then, when creating a ball, give it a random lifespan. And how would you double check that the lifespans were actually different?





## The Next Step

You want to make more involved and innovative programs. You are a creative technologist. An artist. You want software, you want hardware. You want performance, interaction, synchronicity. Magic.

The optimism and excitement of a good idea, or even just a fresh sense of motivation, is a special thing to have. Next I’ll be outlining a multi-step process that will perhaps start off a little dry, and could sap some of that excitement and motivation. There is arcane technical history. There is installation of new libraries. And configuring system settings. Not exactly spicy stuff.

But what I’m going to be sharing is a setup and approach that helps me *quickly* and *easily* iterate on new ideas. It allows me to work on multiple platforms. It allows multiple programs, made with different languages, to talk to each other. It helps me use cheap, pre-made hardware to interact with my programs. It helps me make my own hardware that can easily work, with no fussy installation, with the programs I make.

First there are the boring things, like wrestling with system settings and application preferences. No one likes that stuff. However, this is an investment. It has helped me get to a place where I can make stuff fast, and be flexible enough that I can improvise easily when inspiration strikes. 

What I’m doing here may or may not be your perfect way of making. But the broader lesson is that you should invest in programming languages, systems, libraries, hardware, software, and so on, that let you *create as seamlessly as possible*. This may involve a bit of research. Just knowing about what kind of technology is out there can be hugely beneficial. Technology is your artistic canvas. Knowing your materials and using what works best for you will make you a better artist.

So even if this doesn’t wind up being “your way”, the following exercise will help you practice “a way”.

### Adding another library

This far we have been working with p5js, which is a library for Javascript. A library is really just other people’s code. Sometimes it's Javascript, other times C++, or any other programming language. The important part is that someone made something for *you*. They made a bunch of functions and objects. If they’re really nice, they also documented those functions and objects kind of well. If they’re really, *really* nice they documented them *very* well and given you good examples of how to use them.

Thanks Lauren McCarthy! Thanks Processing Foundation! You made my life easier.

I have another library that I have simply been *loving* lately. It’s called WebMidi.js:

https://github.com/cotejp/webmidi

It lets you use the MIDI communication protocol in your browser based programs. In order to use it, we need to include the library in our sketch. We are going to build off of our previous bouncing ball object sketch. If you go to your standard p5js index.html file, you’ll see the following lines:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.2/p5.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.2/addons/p5.dom.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.2/addons/p5.sound.min.js"></script>
```

This pulls the most recent version of the p5 library, the p5 DOM library, and the p5 Sound library from a web server. If you needed to use a local copy of the library (like if you were running a browser based program on a machine without internet), you would do something like this:

```html
<script src="p5.min.js"></script>
```

And then you would make sure that p5.min.js file (or whatever it is you want to run locally off of your machine) was in the directory that your other index.html and sketch.js files were in. I want to add my new favorite library, which will look like this:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.2/p5.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.2/addons/p5.dom.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.2/addons/p5.sound.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/webmidi"></script>
```

After that, we’re going to initialize the library inside of our setup function. The setup function will look like this:

```javascript
function setup() {
  createCanvas(400, 300);
  
  //start with a single ball
  //i've set up a for loop for you in case you want more
  
  for (var i=0;i<1;i++){
  	balls[i] = new Ball(random(width),random(height),24);
    //a sized 24 ball is placed in a random position
  }
  
  ////
  //Adding MIDI functionality
  ////
  
  //Enable the WebMidi Library
  WebMidi.enable(function (err) {

    if (err) {
      console.log("WebMidi could not be enabled.", err);
      //What happens when there is an error
    } else {
      console.log("WebMidi enabled!");
      //What happens if there isn't an error
    }

    console.log("---");
    console.log("Inputs Ports: ");
    for(i = 0; i< WebMidi.inputs.length; i++){
      console.log(i + ": " + WebMidi.inputs[i].name);
      //Listing all of our MIDI input ports
    }
    
    console.log("---");
    console.log("Output Ports: ");
    for(i = 0; i< WebMidi.outputs.length; i++){
      console.log(i + ": " + WebMidi.outputs[i].name);
      //Listing all of our MIDI output ports
    }
	});
  
  var output = WebMidi.outputs[0];
  
}
```

If everything has gone right, when you run your program it will work as usual. Except that you will see something like this in your console log:

```
WebMidi enabled!
---
Inputs Ports:
---
Output Ports:
```

### What is MIDI?
<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/midi_logo.png" width=300>

https://en.wikipedia.org/wiki/MIDI

MIDI stands for Musical Instrument Digital Interface. You may have heard about it in different contexts. Maybe you think of old school Nintendo soundtracks as “MIDI music”. Or perhaps there is a dusty MIDI keyboard in your parent’s closet. You may have seen a MIDI cable, or downloaded a MIDI file.

Kind of confusing. MIDI is described as a “technical standard”, which consists of a standardized communications protocol, and physical standard for interfaces, connections and cables. 

Created in 1983, it was mainly a way to get different pieces of musical gear to talk nice to each other. One machine might say to another machine, “I want to send this note, for this long, right now”. The first machine is controlling the second. The second machine has a voice that creates the sounds according to the MIDI message, while the the first machine has no voice at all. It just sends commands.

The piano keys that you may see on a synthesizer are the interface to the machine that makes the sounds. Just like our computer keyboards are not one and the same as our computers, MIDI controllers (like a musical keyboard) are not the same as the things that make the noise (a synthesizer). With this new standardization, one musical keyboard was able to work with synthesizers from all kinds of different companies. Additionally, one keyboard could send the same message to multiple synthesizers at the same time. You use MIDI cables to connect this hardware to each other.

And then the messages could be manually programmed and played back if desired, making a kind of digital sheet music. These are MIDI files. And since the live MIDI messages and MIDI files are digital, all of this technology was implemented into computers not too long after MIDI was released. Composition of musical scores could be played back on computers with the right hardware and software, which is what you might associate with simplistic “video game MIDI music”.

All of this continued to be implemented in new musical gear, new computers, and new operating systems as the years went on. Most importantly, virtual versions of the physical elements were made. A program that generates MIDI messages can send those messages to a program designed to receive them and makes sound accordingly. The computer has a virtual port that facilitated a connection between the MIDI output of one program to the MIDI input of another. You can think of this like a virtual cable that connects the two.

It is this virtual nature that is going to help us create some really cool stuff.

...but where are we virtually plugging in?

### Enabling Virtual Ports

MacOS has the ability to make virtual MIDI ports using system settings:
https://support.apple.com/guide/audio-midi-setup/set-up-midi-devices-ams875bae1e0/mac

Do a spotlight search on your machine for the application “Audio MIDI Setup”

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/audio_midi_setup_search.png" width=400>
<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/audio_midi_setup_icon.png" width=100>

Inside of Audio MIDI Setup go to Window>MIDI Studio. Double click on the IAC Driver box. A properties window will open.

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/macOS_midi_system_settings.png" width=800>

Click on the Plus icon to add a “MIDI Bus”. You can come back here to add more later, but for now one is fine.


Windows does not have this ability natively. However, there is an excellent free program that has worked well for me called loopMIDI:
https://www.tobias-erichsen.de/software/loopmidi.html

It functions and feels very similar to the MacOS’s MIDI setup. Once running, you can add or remove MIDI buses using the “+” and “-” buttons in the lower left hand corner.

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/loopMIDI_screenshot.png" width=400>

Once you have made a virtual MIDI port, run our bouncing ball program again. You should see something like this in your console log:

```
WebMidi enabled!
---
Inputs Ports:
0: loopMIDI Port
---
Output Ports:
0: loopMIDI Port
```

That means that our program can send and receive on this port.

Send and receive… what?

A single MIDI port can send lots of things, but to keep things simple we’re going to focus on only a few specific elements.

### Notes
A piano keyboard has different keys you can play. A musical score can have notes printed on a staff. A MIDI message can tell a MIDI instrument to play a note in the same way. There are two kinds of notes: a note on and a note off.

### Velocity
Imagine hitting that piano key as hard as you could. Imagine a violinist tenderly pulling their bow across the strings of their violin. A single note can be hard, or soft. Generally, this affects the volume of a particular note. Every note is paired with a velocity. In many instances where a velocity is not given, the default maximum value (127), is used.

### Control Changes
Control Change messages are usually referred to as CC messages. This is a kind of “general purpose” communication. Imagine a synthesizer with lots of knobs and sliders. Maybe they don’t send note messages, or the velocity of the notes. But they could control other aspects of the sound or the function of the system. Things like bending the pitch of a note can be assigned to these types of controls.

### Channels
Within any given MIDI connection, we might be sending note ons, note offs, all kinds of velocities and throwings all sorts of CC messages around. Imagine all of that communication going through a MIDI cable, and then multiply it by 16. There are 16 channels available on any given MIDI connection. These channels can be dedicated to things like multiple instruments. For example, a piano on channel 1, channel 5 could be guitar, and usually channel 10 is drums. However, this isn’t set in stone and the channels can go to wherever you want.






Let start by sending a note message. Add the following code inside of your Ball object’s “bounce()” function:

```javascript
//Setting the MIDI output of the Ball object
this.output = WebMidi.outputs[0];
//play the note on that output
this.output.playNote("C5");
```

This will mean that a C5 note is sent through the webmidi output 0. When we saw “0: loopMIDI Port” or “0: IAC Driver IAC Bus” or whatever you named your virtual MIDI port, this is what we are referring to. The inputs and outputs are arrays, and 0 is the first output that is available.

Now we’re going to save this sketch, and set it aside for a moment.



-----






Next, we’re going to make a whole new sketch. Don’t despair! It’s a quick, easy little guy. You can find it here:

http://alpha.editor.p5js.org/dbarrett/sketches/HkUhtS7PM

With the code below:

```javascript
//background color variable
var bgColor;

function setup() { 
  //starting background color
  bgColor= color(220,220,200);
  createCanvas(400, 400);
	
  ////
  //Setting up MIDI
  ////
  
	WebMidi.enable(function (err) { //check if WebMidi.js is enabled

  if (err) {
      console.log("WebMidi could not be enabled.", err);
    } else {
      console.log("WebMidi enabled!");
    }

    
  //name our visible MIDI input and output ports
  console.log("---");
  console.log("Inputs Ports: ");
  for(i = 0; i< WebMidi.inputs.length; i++){
     console.log(i + ": " + WebMidi.inputs[i].name);
  }
  
  console.log("---");
  console.log("Output Ports: ");
  for(i = 0; i< WebMidi.outputs.length; i++){
  		console.log(i + ": " + WebMidi.outputs[i].name);
    	
    }  
    
  //Choose an input port
  inputSoftware = WebMidi.inputs[0];
    
  ///
  //listen to all incoming "note on" input events
  inputSoftware.addListener('noteon', "all",
  	function (e) {
 		 	//Show what we are receiving
  		console.log("Received 'noteon' message (" + e.note.name + e.note.octave + ").");

	  	//change the background color variable
 		 	var randomR = random(0,255);
  	 	var randomG = random(0,255);
  		var randomB = random(0,255);
  		bgColor = color(randomR,randomB,randomG);
  	}
  );
    //
    //end of MIDI setup
    //
	});
	
	
} 

function draw() { 
  //draw background with background color variable
  background(bgColor);
}

```

What this says is: whenever I receive a “note on” MIDI message on input port 0, I am going to console log information about the message I received. Then I am going to change the background color variable to something random. Then when I draw to the screen, I’ll use that background color.

Now run this sketch. In the console log you will hopefully see the successful initialization messages. If you got errors instead, and you are copying and pasting this code into a new document… did you remember to include the *library* in your HTML?

If everything is working, you’ll just see a pale square. Keep that sketch running in one window. 


<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/midi_color-bounce_window-1.png" width=800>


Now go back to your MIDI enabled bouncing ball sketch. Run that as well, where you can see both windows. Now click to create a ball.




<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/midi_color-bounce_window-2.png" width=800>






When the ball bounces on your first sketch, you should see the color change in your other sketch.

Next, copy the URL for the color change sketch and open a new browser window. In the p5 online editor, you can go to File>Share and copy the “Fullscreen” link if you want to only see the sketch output and not the code. If you bounce a MIDI ball again, you’ll see that it changes both windows.

MIDI is being sent out of one program; the bouncing ball with MIDI p5 sketch. Another program is listening for MIDI messages on the same port; the random color p5 sketch. Multiple instances of the same program can hop onto one MIDI port. These pairs of MIDI inputs and outputs can sometimes be called a “MIDI Bus”.

The great thing about MIDI Buses is that lots of things can hop on the bus, sending and receiving to their heart's content. And this is all built into the way that MIDI works. You don’t need any servers to set up or coordinate the messaging. It just works.

Try opening three browser windows of the random color sketch. Four. Five. Fill the screen with small versions of them. Plug in a monitor, drag over another instance of the sketch and full screen it. They’ll all receive the MIDI messages from the ball sketch, all at the same time.

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/midi_color-bounce_window-3.png" width=800>




### But that’s not all

There are all kinds of different programs that can work with MIDI messages. You have just made a browser based interface that can interact with them. Simplistic, perhaps. But certainly a start. Imagine being able to divide a collaboration up into two parts: you work on a visual half while a musician works on the audio half.

Totally possible. But how would we go about testing it before handing it off to your collaborator?

Ableton Live is a popular music making application, and it uses MIDI! You can install it here:

https://www.ableton.com/en/trial/

When you install Ableton and open it, you will be presented with a window that looks like this:


<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/ableton_first_session_view_1.png" width=1000>


If you then go to File>Preferences, you’ll see different settings for how Live works. If you click on the “Link MIDI” tab on the left, you will see the current MIDI setup for the program.

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/ableton_midi_preferences.png" width=600>

Oh, look! It’s the MIDI bus I made! Click “On” for Track and Remote for both Input and Output MIDI Ports. This will allow Live to receive MIDI messages that are sent to this MIDI bus, and also send messages out to that MIDI bus.


Once you have your MIDI bus enabled inside of Ableton, you will want to add a MIDI instrument. If you use the browser on the left hand side of the Ableton screen, you can select Instruments>Simpler>Piano & Keys and find a piano instrument that you like. Click and drag it to the work area to the left, onto the “MIDI 1” instrument slot. Now the slot will be re-named to whatever instrument you chose, like “Simplest Piano”.

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/ableton_added_instrument.png" width=600>

Now, to get our Simplest Piano to be able to listen to our p5 sketch, we will need to make sure that the specific instrument is listening to the MIDI bus we have made for ourselves. For every MIDI instrument in Ableton, you will see a “MIDI From” section with a drop down menu. On your new piano, choose MIDI From your new MIDI bus (in my case right now, “IAC Bus 1”).

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/ableton_midi_track_setting.png" width=600>

Now when you use your original ball bouncing sketch, the MIDI instrument should detect the “bounces”. Out of the browser, into Ableton Live. Amazing. But you can see in our ball’s bounce function that it is just sending the same note, “C5” over and over again. Lets replicate the functionality of the pre-made piano sound we were using before.

First, to clear things up let’s remove the sound from the p5 sketch. Comment out your play and set volume commands inside of the bounce function.

```javascript
//because we're moving to MIDI, lets
//disable sound playback inside of p5

//play the sound effect when we bounce
//this.ballSFX.play();
      
//change the volume of the sound
//this.ballSFX.setVolume(this.volume);
```

The way that the sketch was making lower and higher pitched sounds was by affecting the speed of the sound playback. You may have noticed that the lower notes stretched on for longer. Making the left side of the screen play lower tones and the right side play higher tones was accomplished with the following code:

```javascript
this.ballSFX = loadSound('piano.mp3'); 
...
this.sfxSpeed=this.x;
this.sfxSpeed=map(this.sfxSpeed,0,width,0.01,4);
…
this.ballSFX.rate(this.sfxSpeed);
```

This can be read as, “The rate of the playback of the file is set to a variable called sfxSpeed. This variable is set by determining the ball’s X position in the sketch. If the ball is all the way left the rate is 0.01, if it is all the way right the rate is 4. All the X positions inbetween are mapped accordingly.”

This means a ball in the middle will be played at a rate of approximately 2, where as a ball one quarter away from the left side of the sketch should play at a rate of approximately 1. This is fine when we are working with numbers. But “C5” isn’t a number. How can we map for MIDI values?

Luckily, each specific note value has a corresponding number. The lowest note C0 can also be referred to as note number 0, and the highest note is G10 is 127.


### 127

127. We will see this number a lot when we are working with MIDI. Why? A MIDI event can be sent as a byte, which is 8 bits. The way the MIDI standard is implemented, the first bit is used to identify the kind of MIDI message the byte describes. This leaves 7 bits left to describe a value. Considering a binary counting system, 2 to the power of 7 is 128. Meaning the range of a sent MIDI value is 0-127, since we will start at zero instead of one.

You don’t need to know all this. There are plenty of great resources online if you want to get into the nitty gritty of how MIDI messages are created at the lowest level. But for our purposes, not necessary. Just didn’t want you to think we picked 127 out of thin air. And you’ll be seeing it come up repeatedly when working with MIDI.

### A new map() for a new territory

Our old playback rate was mapping our ball’s position on a scale from 0.01 to 4.0. Now we need a new map for using MIDI values instead.

```javascript
//creating a mapped MIDI note instead of a mapped audio playback rate
this.midiNote=map(this.x,0,width,0,127);
```

And then in place of triggering a playback event with our audio, we want to playback MIDI

```javascript
//because we're moving to MIDI, lets
//disable sound playback inside of p5
      
//play the sound effect when we bounce
//this.ballSFX.play();
      
//change the volume of the sound
//this.ballSFX.setVolume(this.volume);
      
      
//Setting the MIDI output of the Ball object
//using the this.midiNote number as determined by ball position

//set output
this.output = WebMidi.outputs[0];

//play note
this.output.playNote(this.midiNote);
//this.output.playNote("C5");
      
//console.log(this.volume);
console.log(this.midiNote);
```

If you now use the ball sketch, you’ll hear different notes being played by the piano inside of Ableton. There is a bit of a quirk, however. Might be hard to notice, depending on what kind lovely piano you have loaded up. When we use WebMidi.js’s “playNote” function, we are creating a midi “note on” event. But a note on is a whole different beast than a note *off*. It makes sense, when you think about it. Maybe you want to hold down a piano key shorter or longer, depending on how you want to play.

When we send a lot of note on events without corresponding note off events, sometimes our MIDI enabled software can act a little funny. A note on that stays past its welcome might be called a “stuck” or “hung” note. With the bouncing ball sketch, it didn’t really matter. In Ableton, it might result in unpleasant sound or glitches. If you are experiencing a stuck note in Ableton, click the “stop” button at the top of the program.

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson4_images/ableton_stop_button.png" width=400>

### Stopping and Softness

Sending a corresponding note off message would be a good idea, just to keep things clean. While we’re at it, we can set a note velocity (a “volume” of sorts). And that way that WebMidi.js works, will also require us to set our MIDI channel.

```javascript
this.output.playNote(this.midiNote, 1, {duration: 100, velocity: .95});
```

All that work in one line?! WebMidi.js you gotta be kidding me that is amazing. Thank you!

In one line we:
Sent a midi note number (this.midiNote, determined by ball position)
Set the channel this message is to be sent out on (1)
Scheduled a note off event in the future (100 milliseconds after the note on)
Set the velocity of the note (on a scale of 0 to 1)

The note off stops the current note from playing, and the velocity describes how hard we are hitting the note. This affects the volume of playback.

Volume of playback, volume of playback… hmmmm. Aren’t we already working with that for our old sound file? We are! What is that again?

```javascript
this.volume=map(this.lifespan,0,600,0,1);
```

It is already being mapped on a scale of zero to one. Nice. Lets just drop it in for our velocity value:

```javascript
this.output.playNote(this.midiNote, 1, {duration: 100, velocity: this.volume});
```

You should now be able to hear pianos playing not only while bouncing, but also the notes will get softer and softer as the bouncing ball disappears.


If you have made it this far, congrats! I told you there’d be some fairly boring stuff to get through. All those preferences, configuration screens, setup windows. Yeesh! So many tedious little things just to get to this point.

But now if you have this working, you’ll be able to do a lot of interesting things with a bunch of different programs. Thank you for being patient with me. Before we dive into more things we can do, you should take a break. Try selecting some new instruments from the left hand side of the Ableton Live window. Pianos, so traditional! Did you see there are tons of crazy synthesizers inside of this program? So cool. They sound great. Load up some new instruments in your first MIDI track and then play with the bouncing ball sketch.

Jam out for a bit. You’ve made an instrument, after all. When you try new sounds, take note of what works and what doesn’t. Why are certain instruments not as satisfying for use with the bouncing ball sketch as other ones are?



In fact,



now that I think of it,



How about we hold up for a second.



In the next sections, I’ll be outlining how to implement the other parts of the MIDI protocol I talked about: CC messages and using different channels. I’m even going to push you a little bit by introducing some new programs and languages: Processing and Max MSP. But what about using what we have? What about our bouncing ball? What about the Note On and Off messages? And don’t forget Velocity!


It is really easy to get caught up in ALL the things that a program or language can do. And why not? If you want to learn it, you want to know the whole thing so you can use it to your advantage. How are you going to make something awesome if you aren’t leveraging all of these amazing features?

It is that last sentence where I have a bit of a problem. There are *plenty* of cool and compelling things you can do with very simple features of programming languages and programs. And afterall, we’re not just programmers- we’re artists! We’re designers. “Creatives”.  Constraints are great for creating new work. How many amazing images have you seen that have been drawn just with charcoal? What about Bauhaus? WHAT ABOUT DEITER RAMS?!

Sure, there is more to learn. But what if what you have *right now* is enough for you to make your perfectly elegant minimalist browser based MIDI enabled debut in the world of creative coding? I know, I know. You aren’t ready for that. You wouldn’t know what to make. You don’t even know about CC messages yet! (It’s not that hard, I promise)

It is true that there is more to learn. But it isn’t true that you know nothing.

I’ve aimed this tutorial series at people who have already done some introductory programming work. When was the last time you thought about the things you made when going through your old beginner material? The bouncing balls, the buttons, the sliders. Color, shape, time. Letters, words, weights. Mice, microphones, webcams. Image, video, sound. Perhaps an API call here and there. Or even linking it to hardware, like an Arduino.

With what you have learned in previous Javascript classes or books, you can now take any one of those things you have made and have it send or receive a note or notes, knowing the difference between on and off, each with varying velocity values. One p5 sketch in one browser window can send to multiple other browser windows. Multiple browser windows can each send notes to a single window. And then all of that, back and forth, in and out, can also include Ableton Live.

When was the last time you played with your old programming projects? You left them in a folder, somewhere. What did you name it? “Projects”? “Programming?” How deep down inside of the Documents folder did you hide them? Or they are backed up on some cloud storage somewhere. Google Drive. Or Dropbox. Did you ever share it with someone? Or did you keep it private? Perhaps they are still sitting on an online editor. What was the login? The password? Maybe it will autocomplete when you go back. Oh, these small miracles.

All that work you did. Sure, a lot of example code. But you worked through it, its *your* example code. You changed the colors, the sizes, the speed. It didn’t go to waste, and it wasn’t “just” tutorial stuff. It has been waiting, diligently, to be picked back up again. Don’t worry, your programs weren’t loney. They don’t have feelings. But they’ve been ready to be picked back up this whole time. Ready to be re-worked, tweaked, and incorporated into something new.

The mouse X, Y tutorials. The “onClick()” function examples. They all can have MIDI inserted into them.

I propose we take a technical break, and pick up an artistic task.

Go into your back catalog of work, or re-create an example from one of your previous programming tutorials, and “MIDI”-fy it. Make a MIDI version of and old piece. Incorporate the WebMidi.js library and the Note and Velocity MIDI messages in the way that I’ve done to the bouncing ball sketch. This can be a good technical review for you to do on your own, without explicit guidance:

* Add the library
* Initialize it in your program’s setup
* Setup to listen for incoming MIDI notes, and/or
* Send MIDI notes

There will be other useful programming life lessons, as well. You’ll look through your old code and wonder what you were thinking. How does this thing even run, anyways? Get reacquainted with your program, and this time write detailed code comments before you forget again. Your future you will thank your past you.


But even more so, this is a chance to meditate on simple interactions and concepts for a piece. They could be complete on their own, or perhaps satisfying fodder for something bigger. How many different ways can you use MIDI?

What is obvious? What is the *opposite* of that? What is weird or nonsense? What is best suited as a “sending” program and what is best suited as a “receive”? What could work as both? Do you like using Ableton Live with these? Do you like the music it makes? Record that and listen to it for a few days.

Instead of plowing through the rest of the MIDI specification and throwing more code at you, how about we take some days to think of how we can use what we already have? Every day this week, come up with a new idea for a small MIDI program idea. Simple stuff that you can jot down in your smartphone’s note app. Right now we have one: “Ball bounces, makes sound and changes other window’s color”. So you can’t take that one. What else can be done?

You don’t always have the motivation to program. So I highly encourage this method of writing down strange, vague project ideas into your smartphone. Also, bizarre diagrams with weird labels, penciled inside of a small notebook is also a very good look. When you actually do have time to code a bit, after work, after the laundry, and after doing your dishes… you’ll have something to start on. Instead of wondering, “...what do I do now?” You’ll open your phone and see your half-baked prompt from Wednesday: “Magenta Triangles - growing / tones”

And with any luck, you won’t remember what you even meant at the time. But you’ll somehow be motivated with a new idea, nonetheless.
