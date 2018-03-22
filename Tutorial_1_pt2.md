# Thesis Tutorial 1, part 2

After some feedback, some people asked me what ways we could use this approach to randomness in their creative coding practices. This isn’t just a fair question for me to answer, but for many tutorials and example code. When you are already working on a project and just need an answer to a specific technical question, you will take what you need from the lesson and continue on your merry way. However, when you are learning for a general mastery, it may be hard to imagine how or why these things may be put into practice.

Which is actually a bit of an issue when you are learning, in my opinion. I can tell you that you can use the random function on more than just numbers, and you may say, “...ok.” I could tell you to copy and paste what I have, and then challenge you to replace the numbers with strings.  You might also say, “...ok…” and then proceed to haphazardly throw in some gibberish, perhaps a swear word or two. You stop the sketch, change some of the text to double check your competency, and when the program runs as you expect you will proceed to the next coding exercise.

I’ve been there. My problem was, when it actually came time to be creative with code… the blank white screen made me realize I didn’t know how to *use* what I *knew*. Figuring out ways to actually use the examples in a manner that was interesting to me, resulted in me using those concepts more. Which not only helped me make interesting programs (ok, ok, interesting *for me*), but helped me solidify those concepts in my head.

This is a guide for *creative* coders.

But being creative can be hard. Especially when brought into the technical realm. Everything seems possible, which is too much to think about. But a beginner-to-mid level skill level slows you down and limits the scope of your ambition, which is discouraging. These are not fertile conditions for the creative mind. Which could be just enough to drive people away from creative coding altogether.

And what kind of programming guide would this be if you don’t come out the other side ready to make awesome programs? No kind of guide at all, I say.

This means that I am going to try and be like that cool history teacher in college who told you, “You won’t need to memorize dates!”. I’m going to eschew the quizzes, challenges and pure technical focus that other programming guides have. Don’t get me wrong, they have their place. But here we are going to try and pair technical practice and information with creative practice and information. This is in the hope to make you a better creative coder, not just programmer.

## What next?

So how can we take the concepts and code from part one and kick things up a notch? Well, since I’m on such a kick about randomness, maybe randomness will help me with some inspiration.

What do I do? What next? What does the future hold? Randomness has helped answer the big questions throughout the history of humanity. Runes, I-Ching, Tarot cards. A certain kind of artistic divination was developed by Brian Eno in 1975, with a card set called “Oblique Strategies”. Oblique Strategies is a set of cards with instructions for people who are running up against a creative block or looking for new inspiration.

<img src="https://www.enoshop.co.uk/images/products/prod/ObliqueStrategies3.jpg" width="400">

From Brian Eno’s online shop:
https://www.enoshop.co.uk/product/oblique-strategies.html


How do I use it? Example: as a complete amature, non-professional writer, I am currently experiencing writer's block. Totally at a loss as to what to type next. What to do? I might pull a card from an Oblique Strategies deck and use it as a creative prompt or design constraint. Sometimes they are more specific, other times very abstract. The card I pulled was:

“Try faking it!”

Hmmm. Not sure why I would want to fake anything. Being the commensurate professional writer that I am, I shouldn’t have to. With all these ideas brimming in my head, just waiting to burst out on the page?

Maybe you can try a card and see what comes up. You can find my deck here:

https://alpha.editor.p5js.org/dbarrett/sketches/ryXGukwFz

<img src="https://github.com/dombarrett/Tutorial-Testing/blob/master/lesson2_images/oblique_strats_screenshot.png" width=400>

## A little story on this sketch

I had found the text file for Oblique Strategies online. I put it into a txt file, knowing that p5js would be able to parse it. But I don’t know how it works off the top of my head, so I went to:

https://p5js.org/reference/

If I’m coding in an environment or language, I always have the reference handy. First, I clicked on the “IO” section link. Why did I think IO would give me the information I needed, and not something like the “Data” section? “IO” stands for input and output. Yes, a text file contains data. But more importantly, from the perspective of documentation, it is an external file that needs to be loaded. Hence “Input”.

Then inside of “IO”, I clicked on “loadStrings()”. Why did I think that had what I needed? Because I’m dealing with a txt file. This is typically the most basic way that we are going to store characters on a computer. At the end of the day, things like JSON, XML, CSV, are just a specific way of organizing text. P5js, and plenty of other languages and environments will give you built in functionality to parse JSON, XML, and CSV.

But the basic file type for text is txt, and the basic data structure for text is a string. I have enough experience to expect that the function “loadStrings()” is what I’ll be needing.

You most likely know most of these facts by now if you have completed an intro class or book. Well, that is to say, you’ve been exposed to them. Perhaps this jogged your memory. But the more you are actually using these things in your practice, the more you’ll be digging into your programming reference documentation. And mental linkages like what I’ve outlined above will start to become second nature. You will build this instinct as well, over time.


<img src="https://raw.githubusercontent.com/dombarrett/Tutorial-Testing/master/lesson2_images/p5js_IO_reference.png" width=700>

Reference. Use it!



## The plot thickens

I’m currently using the alpha version of the online p5js editor. I uploaded the file into my sketch directory. However, when I clicked on the file, I didn’t see any of the text inside of it. All blank. What gives? To be honest, I don’t know. I had seen some behavior like this before, and knew it might be a while before the glitch was fixed. I simply opened up a copy of the file on my machine, and pasted the contents into the blank text file inside of the online editor.

Then I output the entire files contents into a console log to make sure it worked, and up came… HTML? My txt file didn’t have any HTML in it. Something had gone wrong. I saw “amazon” and “aws” tucked away inside of the HTML. This must be where the online editor is hosting the txt file, and things had gone screwy on the backend. Another glitch.

So what to do? I looked at the example code from the loadStrings() reference entry. All of the lines loading the txt files would put them in a folder called “assets” first; ‘assets/test.txt’. Perhaps this assets folder was some kind of requirement. So I created an assets folder, created a new txt file inside of it and pasted my content into it.

I used the loadStrings function, and it worked like a charm. Then in an effort to document this bug in order to show it to you, I attempted to recreate it. I made a text file in the root directory again, put content in it, and attempted to read from it. And succeeded. No HTML, no error.

I have absolutely no clue why this works now.

## WOW what a boring and tedious story!

I couldn’t agree more! But it illustrates an important point. Sometimes when we’re coding or building circuits or making anything amazing with technology, you hit hurdles like these before you even get started. You updated your development environment and now the code that worked yesterday is broken. Re-installing a library doesn’t work for some mysterious reason. The microphone input works on Android browsers, but not iOS.

All these tasks are things that have to get done before you can start “working”, even though this “not work” is costing you plenty of time. Sometimes this is called “yak shaving”; all the little dumb tasks and problems that have to get solved in order to solve your bigger problem. You can and will be able to solve these problems. They will happen again and again however, no matter how experienced a programmer you become. Perhaps even when you are writing a programming tutorial, for example.

Take solace knowing that the pros are toughing it out in the trenches, throwing error messages into Google just like the rest of us.

## Let us consider

Imagine Claude Monet, looking out his window when he is suddenly struck by inspiration. He excitedly opens his drawer of paintbrushes, only to have a screw pop out of the sliding hinge and have the entire drawer crash onto the ground. Of course, the only brush he was actually looking for was the one that broke. Right in half.

He puts on his coat and walks down to the art supply store. “That thing was creaking, should have fixed it *before* something happened. Or at least been more gentle opening the drawer up. Come on Claude, you’re better than this!” He finishes silently scolding himself as he arrives at the door of the store. A “Closed” sign dangles on the other side of the glass.

“Damnit! They close *Mondays* I always forget… what to do what to do…”

The hardware store isn’t *too* far away. Maybe some heavy duty tape will make do as a temporary fix. He goes into the store, and grabs some tape. Oh! And while he is there, why not get some new screws with fresh threads on them so he can fix the drawer? Up and down the aisle he goes, doubling back again to find the display of screws he missed. But the only box of phillips heads left is a pack of 100. Ugh, come on.

So he finds a store employee and asks if they have any packs of phillips heads with less than a hundred screws. The employee goes back with Claude to the screw section and takes a look at the stock shelves above the customer display.

“We got a 24 pack, but they’re flat head screws.”

“No phillips heads?”

“No, but the flat heads are the same thread and length. You have a flat head screwdriver?”

Claude sighs and closes his eyes. He thinks. Does he have a flat head screwdriver? He *should*, but he can’t really remember for sure. Phillips head? Totally. No question. But flat head, flat head, flat head...

“...no… no I don’t think so.”

“Well we got a flat head screwdriver for sale right here, if you want that and the 24 pack.”

“nah... together that’d cost more than the hundred pack of phillips head screws. Is there any way I can break up the hundred pack? Honestly I only really need three or four.”

“Sorry sir, can’t do it. Store policy.”

“Not even if I bought like, fifty?”

“No, sorry.”

“It's fine, had to ask. I guess I’ll take the 100.”

And so, Claude Monet bought a roll of that cloth-type gaffer tape and an absurdly large box of phillips head screws. He walked down the street, past the closed art store, back to his home. The wreckage of the spilled drawer lay on the ground and he got to the task of cleaning the mess. One by one he put each brush back, until he came across a flat head screw driver and he thought, “At least I didn’t buy another one”.

---

We don’t think about this when we look at Monet’s painting “Water Lilies”, but maybe we should. 

<img src="https://upload.wikimedia.org/wikipedia/commons/3/35/Monet_-_Seerosen_1906.jpg" width="700">
https://en.wikipedia.org/wiki/File:Monet_-_Seerosen_1906.jpg

<br><br>
Yak shaving.


## Alright

We have had our own “Monet’s trip to the hardware store” moment, and can finally get down to the business of starting. It could be easy to be in a sour mood having spent so much time, but perhaps also a feeling of relief. You’ve finally arrived to your medium, ready to move forward. What do you have for us, Oblique Strategies?

I ran the program and came up with:
“Spectrum analysis”

Hmmmm, ok.

Brian Eno made Oblique Strategies with music at the front of his mind, so there are going to be some entries that may be more oriented specifically to music and sound. You don’t have to use the first card you draw if it doesn’t make sense to you (I promise, I won’t tell anyone). But this isn’t a half bad prompt. I have an idea.

## Let use some audio!

Lets analyze the audio spectrum.

Copy and run the following code in the p5js online editor:

```
var mic;

function setup() {
  mic = new p5.AudioIn();
  
  // start the Audio Input.
  // By default, it does not .connect() (to the computer speakers)
  mic.start();
  
  createCanvas(400, 400);
}

function draw() {
  background(220);
  
  var vol = mic.getLevel();
  console.log(vol);
}
```

This is a basic use of the AudioIn functionality in the p5.sound library. You may need to give your browser permission to access the microphone. If everything is set, you should be seeing some floats scrolling down in your console. This is the measured volume of what your microphone is hearing.

If I’m adding a new feature into a program, I like to have a separate running example like what we have above. I can make sure it works, test out solutions to issues, and start yak shaving again without messing with the pretty code that works. Then, once I know it works (is the mic working? Is it on? Do I even *have* a microphone??) I will do a transplant into my main project. Today, we’re doing an ear transplant so our p5js sketch can hear.

Lets flex our muscles a bit, and perhaps establish a bit of a rapport with one another. I’m going to describe how you should perform this code transplant surgery, but not show you the actual code. 

“But you said there would be no programming challenges!”

I know, I know. Maybe it is better to think about this as a stretching exercise. You aren’t a total beginner, but we just need to get a little flexible and start the blood flowing.

I would like you to take the program from the end of part one and add this example microphone code into it. How?
* The mic variable should be created outside both functions because it is a global variable. 
* Assigning the mic variable as a new AudioIn(), and the start() method should go in the setup function.
* Get the mic level by assigning it to a new variable called ‘vol’,
* and console logging ‘vol’ should happen in the draw loop so we can see the changes.

Did it work? Great! Did it not work? It happens. Maybe take a look at the errors you get and try moving things around. Did you copy and paste things that weren’t code? Did you not copy and paste the entire code snippet? Did you miss the last } at the end? If you’re still having issues, you can use this code:

```
var mic;

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
  
  mic = new p5.AudioIn();
  
  // start the Audio Input.
  // By default, it does not .connect() (to the computer speakers)
  mic.start();
  
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
  
  var vol = mic.getLevel();
  console.log(vol);
  
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


Alright, now we have our random visuals and we’re detecting sound. How can we incorporate these sound values into our sketch?

<img src="https://raw.githubusercontent.com/dombarrett/Tutorial-Testing/master/lesson2_images/snow_words1_screenshot.png" width="700">

## Before we dive in

This can be a very open ended question. There are tons of other variables that we can replace with our ever changing “vol” variable, resulting in a reactive piece of programming art. My broader instinct is that I want to play, and try out a bunch of different things. Color, size, position, and on and on.

I’m immediately thinking about how I am changing the volume number into a new number that makes sense for any of these potential fields. Easily and quickly. Our sketch size is 400 by 400, or rectangles are 10 by 10, and rgb color values go from 0-255. The volume returned to us is a floating point number between 0 and 1.

It would be easy to simply multiply our volume value by any of these maximum numbers. Half volume could yield a position on the canvas that is somewhere in the middle. A quiet microphone could create a darker background color. But you don’t always get input values from 0-1, and sometimes you want to change the way the translation works. What if we wanted our sketch to get *brighter* as it got quieter? Then instead of 0 input:0 color and 1 input:255 color, it would be 0:255 and 1:0. And what if we’re kind of close to what we want, but we want to tweak the details just a little bit? Maybe not *too* bright, or just a hair bigger, perhaps scoot it to the left a bit more.

In order to facilitate an open ended discovery, I instinctively use the map() function. This takes a number, that numbers range, and then a new range. You have probably used this before. And in other languages, sometimes it can be called something different, like “scale”. But it will make this kind of experimentation much quicker.

We have our vol, and we can add a new variable called mappedVol.

```
  var vol = mic.getLevel();
  var mappedVol = map(vol,0, 1, 0, 255);
  console.log("Vol_____:" + vol);
  console.log("Mapped:" + mappedVol); 

```


This could be used for brightness correlating to noise. But if we wanted the inverse? Just flip your mapping

```
var mappedVol = map(vol,0, 1, 255, 0);
```

Playing around with the mic example (you are playing around with it, right? Always take a moment to make funny noises when you are testing noise detection code) you may notice that vol never really seems to hit “1”. You could always just change the 255 to something higher. If you wind up going past 255, the color code will still be treated as if it was 255. If its 256, 257, 5000, whatever. You’re good.

Using map() lets us quickly test these linkages we want to make between our input and what that input effects. I don’t want you to technically know map() and use it, but I want you to think map(). I want you to feel map() and look through the world with map() tinted glasses.

## Synesthesia and other strategies

I will always encourage plugging one input into another output just for curiosity’s sake. Why not? Who knows what strange system will result from it? If you get something that works, roll with it.

But if you are failing to come up with good random linkages, what else can you draw upon? Synesthesia is a condition experienced by some people where two senses can be linked via specific experiences. A common example is experiencing some musical notes as specific colors. Other senses and topics can be tied; numbers, space, months or days of the week. People experience many variations of these, though the specific pairing can change from person to person.

This general concept can be a jumping off point for coming up with interactive concepts. You may have thinking this way already. But in the case of people who experience synesthesia, each relation between senses is different from one person to the other. A subjective experience amongst specific people.

Let's also consider the phenomenon that there is a human tendency to naturally associate certain things with each other. This can be seen in the Bouba/Kiki effect.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e7/Booba-Kiki.svg/500px-Booba-Kiki.svg.png" width="700">

https://en.wikipedia.org/wiki/Bouba/kiki_effect

Question: these two forms each have a name. One is “Bouba” and the other is “Kiki”. Which shape has which name?

Vast majorities of people agree that the rounder shape is Bouba and the sharper shape is Kiki. Across multiple cultures and languages, from children as young as 2 ½ years old. Experiments in 1929, 1947 and 2001 replicated the phenomenon.

Even if you didn’t pick the same names, these are points of leverage when we think about our audience. We could play into people’s expectations, or perhaps subvert them, in order to make a compelling experience. A performance, an interactive sculpture, a UX experiment, or interface.

So I encourage you to think in this manner if something doesn’t leap to mind immediately. Taking a subjective linkage that is interesting, or investigation a widely held association. Sometimes these type of linkages will even be your first thought, a sort of obvious choice that your mind immediately leaps to. I was thinking about noise volume and size.

```
var vol = mic.getLevel();
  var h = map(vol, 0, 1, 0, 20);
  
  console.log(vol + " " + h);
  
  for(i=0;i<1000;i++){
  	//fill(color1);
  	fill(random(colors));
    noStroke();
  	rect(random(width),random(height),10,h+1);
  }
```

What if the “static” blocks we drew every frame were very thin, and only grew to their full size when there was a loud noise? Conceptually, this may play into a straight, “one to one” style mapping. A louder, thing is larger. Feels right, doesn’t it? But there also may be another way to consider the metaphor; a visual noise that grows when there is more sonic noise.

## Side note: TV static, noise, and the case against Kiki and Bouba


http://freestockfootagearchive.com/dark-tv-static-black-glitch-vhs-layer/

A bit of a diversion, but bear with me. My instincts about “noise” are perhaps generationally biased. I grew up with analog TVs, broadcasting over UHF/VHF frequencies. If you tuned into a station or frequency that wasn’t broadcasting, you would see the “snow” of visual white noise and hear an auditory white noise.

https://en.wikipedia.org/wiki/Noise_(video)

Even if you had cable instead of over the air antennas, perhaps you might have switched input channels on your TV set to your VHS tape machine or your Nintendo video game console. Blank input channels would give you white noise.

This noise does exist today when you are attempting to tune into digital HD broadcasting on the ATSC or DVB standard. However it is less prevalent. “Static-y” signals with poor reception now visually glitch in unexpected ways, instead of fading in the visual noise on top of your desired programming. Tuning into channels without a strong signal may be intercepted by your HDTV tuner and given to your TV screen as clean, “No Signal Found” user interface messages. And all of this is avoided by the prevalence of cable TV, which is also passed over for increasing preference towards streaming video internet services like Netflix. Static, snow, or noise of the 21st century is looking more like a ‘404’ page than black and white dots.

I thought of “noise”, considered a double meaning of word and ran with the concept. But my aesthetic mapping might be less “Kiki and Bouba” and more “Analog TV”. Something subjective that would not cross a cultural or generational boundary, but not necessarily as unique and specific as someone who experiences synesthesia. Not that there is anything inherently wrong with one approach over the other, but it is good to meditate on when you are building these links in your head.

A conceptual leverage point. A cultural touchstone. A future obscure reference. Use these things, but be aware of what they are. Are they universal, or are they telling little bits about who you are?

## And we’re back

Ok, so lets play with this noise.

I’ve incorporated the following into my version of the code:

```
var vol = mic.getLevel();
  var h = map(vol, 0, 1, 0, 20);
  
  console.log(vol + " " + h);
  
  for(i=0;i<1000;i++){
  	//fill(color1);
  	fill(random(colors));
    noStroke();
  	rect(random(width),random(height),10,h+1);
  }
```

Running this on different machines, sometimes it was smooth and on others there was some lag. Adding the mic input and drawing 1000 squares to the screen per frame might be harder on certain machines. Feel free to change the amount of squares drawn in your for() loop for whatever runs best.



Initial impressions: I like where this is going. Resizing the squares into small little lines makes the text more readable. Though now I’m thinking about TV static and snow after my tangent above. Its stuck in my head, can’t get it out. My nostalgia is pulling at my brain: TV static never looked this sharp. Lets blur things.

```
//old background
//background(75);

//new, blurry background
background(75,75,75,25);
```

Adding two more integers to our background function lets us use color instead of black and white. A fourth integer specifies the alpha channel, making the color more see through. So you can see a bit of the previous frame as well as the new one. As the background draws over and over again, the previous frames will fade. But the combined effect creates a kind of motion blur.

Try playing around with the alpha value to see what feels good to you. One thing that I noticed is that with smaller alpha values (lots of blur), the scene looked like it had way more static than before. Now I can feel free to drop the amount of squares that I am drawing in my for() loop, if so desired. Feeding my nostalgia not only scratched an aesthetic itch but also introduced a possible way for my sketch to run a little faster. When these types of moments occur, take a moment to appreciate the artistic synchronicity. Maybe you’re onto something.


## What next?

If you have some inspiration by now… go off! Be free! Those moments don’t just come any old time, you know. This tutorial will be here waiting for you after your wild artistic excursions. Good luck, and take plenty of screenshots!

However, you might be sitting at your computer wondering what you would even want to do next. Or more specifically, looking at what I’ve given you and thinking “...so what?”. I feel this way sometimes about example code I see online. Perhaps you’ll think it looks cool, sure. But how are you really going to *use* it? How do I make this piece into a “thing”?

Habit guides me towards putting in some kind of music as the sound source and making a visualizer. But that feels a little… eh, I don’t know. Been there, done that, right? What is something that could give me something *new*, right *now*? Something that might be mine?


I’m going to propose a kind of conceptual framework for the rest of this series. When I’m trying to push an idea forward into something more fully realized, I’m going to encourage you to put a part of yourself into the piece. This is easier said than done, so I’ll put my money where my mouth is and “walk the walk” with you along the way.

I’ve done plenty of creative projects that have been tastefully removed from my own person. Simple shapes, straightforward color pallets and clean lines. Abstract geometry. Bleeps and bloops, clicks and whistles. It's all good fun, and I will most certainly draw from that well again. But it isn’t directly “me”, is it? And to be honest I’ve been a feeling a little uninspired lately. Haven’t you? Or maybe just a bit worn out.

Also, I have to admit sometimes I feel like I have a bit of a chip on my shoulder about this whole “art with computers” thing. Once, in a conversation with a painter, a mutual friend of ours mentioned that I was an artist. He asked what kinds of things I painted, and I said my medium was the computer.

A quizzical look crossed his face. “I use pixels, not paint,” I clarified, feeling pretty clever with myself having made the phrase up on the spot. “Ah, alright.” His facial expression read, “oh, you’re one of *those*”. That ended the conversation pretty quickly.

And it doesn’t help that technology is starting to feel a bit cold and impersonal. Or that people outside of our art and technology bubbles only seem to be drawn to the whiz-bang spectacles without thinking of the potential humanity behind them.


Something needs a shake up. Feels like now is just a good a time as any to incorporate ourselves into our work.

We need noise. So let us use our voices.

If we are going to speak, perhaps we will want to use a script. Good thing we’re already putting text on the screen. The size is a little big for longer pieces of text, so we’ll need to go smaller. Text in the string variable will get cut off if there isn’t enough space for it on the screen. So always double check your visual output to make sure all your expected text is there.

Now because we’re making a script for ourselves, we won’t want random text. We want text in a sequence. Good thing our array can be used either way. There may have been other ways to write the code that we have here, but I’ve set myself up for this kind of flexibility and experimentation. Random text? Ask for a random array entry. Changed my mind, I want something sequential. Then step through the array incrementally. Backwards? Instead of ++, use --. Like my map() habits, I’m setting myself up to improvise and quickly iterate.

Maybe you’ll find different structures that make more intuitive sense to you. In any case, invest time into making sure you can keep coding when inspiration strikes.

In order to track our progress through our script, we will need a global variable. Also, since we’re changing the functionality and making a new version of our program, it might be a good time to rename some of our existing variables. Instead of “textChoices” as our text array name, I’m going to switch it to “textScript”. That way we can wind up with lines of code that look like this:

```
displayText = textScript[scriptProgress];
```
Do you *need* to rename these things now? No, I guess not. But if you are trying to advance your practice, these little organizational things are going to go a long way. Tomorrow when you come back to this program, you won’t confuse it with the previous version that does random text. If you want to show the code to a friend, they’ll be able to read it a little easier and not ask you as many questions. And next year when you look back on all of your amazing progress, you’ll maybe, kind of, almost remember how and why the code works.

## Our new input

I’ve changed my keyPressed() function to the following:

```
function keyPressed(){
  if(keyCode===37){
    console.log("left key detected");
    if(scriptProgress==0){
      scriptProgress=textScript.length-1;
    }
    else{
      scriptProgress--;}
  }
  if(keyCode===39){
    console.log("right key detected");
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  }
  
  if(key==1){
    console.log("keypressed 1");
    colors = equalColors;
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  
  }
  if(key==2){
    console.log("keypressed 2");
    colors = mostlyColor2;
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  
  }
  if(key==3){
    console.log("keypressed 3");
    colors = mostlyColor3;
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  
  }
  if(key==4){
    console.log("keypressed 4");
    colors = mostlyColor4;
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  
  }
  
}
```



## Just checking in:

Adding a global variable. Renaming variables. Changing a function. Have I lost you? If you don’t feel fluent yet, just take each instruction one by one. Make the change, run the program and analyze any errors that come your way. I’ll be giving you a full program later to reference, contrast and compare. But give troubleshooting a shot.

Being able to read these types of instructions isn’t just about throwing a pop quiz at you. Knowing this kind of language will let you digest more advanced material quickly, parse out those cryptic “help” posts on programming message forums, and pass your knowledge along to the people you will someday teach.

## ASCII Keys

The first noticeable change in our new function is using keys that aren’t 1, 2, 3, or 4. The left and right keyboard keys appear to be 37 and 39. These are the ASCII key codes. You may have gone over this in your introductory programming material. I don’t actually have to use the key codes, as p5js builds in constants for you. Meaning, this line of code:

```
if(keyCode===37){
```
Should operate the same way as this line of code

```
if (keyCode === LEFT_ARROW) {
```

There are several other constant names that should work this way. You can kind them in the p5js reference. Which you have open… *right*?! Right.

If you want to use these constants instead, feel free to do so. I like to keep my mind in ASCII land, just in case I decide I want to use a keyboard key that doesn’t have one of these constants. The “Home” key, for instance. So lonely, the Home key. Depending on the keyboard you are using, you might not even have one. And I don’t get in impression that people use it very much, even when it is available.

Strikes me as a little depressing, actually. An abandoned Home, permanently locked into the ASCII neighborhood. While Unicode Consortium pushes forward with all kinds of shiny new emojis, no one wants to go to the older parts of town anymore.

Seems like an artistic opportunity to me. So many potential heartfelt metaphors! Did you know you can search for idoms online? I just went to https://idioms.thefreedictionary.com to look up phrases that use the word home. Oh man guys, there are so many good ones: Home is where the heart is. Nothing to write home about. A man’s home is his castle. Hammer something home. Home away from home. You can’t go home again.

There is poetry lurking inside of our machines, I tell you.

These are all free art ideas, by the way. Maybe I’ll get around to doing something with this concept. For right now, it will stay in my notes app on my phone as an entry stating, “Home Key is depressing”. There is a moderate chance I will totally forget what that means by the time I look at it next. You should have a similar note taking system that logs all of your bizarre art ideas. Anyways, feel free to take this idea and run with it. I won’t show up to your gallery opening after you get famous, causing a scene, all yelling about how you stole my genius. No, I’m classier than that. The free wine will suffice. I’ll make do with a wink and a knowing nod as we catch each others glance from across the room.

The Home key ASCII code is 36.

## Triple Equals

The triple equals sign could also be a bit of a head scratcher. You know the difference between = and ==, but what's the deal with ===? This is a strict check. This makes sure that not only is the value on both sides equal, but also the *type*. For example, booleans are not the same as integers. But boolean conditions can be interpreted as true;1 and false;0.

This means that the statement

```
if(true==1)
```
Evaluates to true, while


```
if(true===1)
```
Evaluates to false, because these are two totally different types of things (the essence of  truth itself, and numbers).

You don’t see this all the time, but pay attention when it comes up. If it is present in any code you come across, it usually means it is *very* needed. I’m using it here because that is how it was written in the reference documentation.

Not too big of a deal, but I didn’t want you to be confused or thrown for a loop if you didn’t recognize it.

## Modulo
Oh, modulo. That's what we call the % sign in our code. Honestly, I’m a huge fan of modulo. Modulo is the best. I’m thinking I might need some kind of modulo branded clothing, a pin or sticker.

Modulo gives you the remainder of the division of two numbers.

That’s it? That’s what all the commotion is about? Yes. But it lets us do really useful things, and I have fully incorporated it into my mental programming toolkit. You see it repeated in these lines:

```
scriptProgress++;
scriptProgress=scriptProgress%textScript.length;
```

Say we come up with a textScript array with 4 entries. If we want to keep track and advance our progress through the script, we want that number to go from 0 (because array index locations start at 0) to 3 (the last entry in the array). Trying to reference an entry outside of the length of the array will either yield nothing, or crash your program depending on what your program is doing. Don’t want that. To make everything work nicely, you could do something like this:

```
if(scriptProgress==textScript.length){
     scriptProgress=0;
     }
else{
     scriptProgress++;
     }
```

But the modulo method does the same thing, in fewer lines. Cleaner, perhaps a bit more readable. How is it working? When progress variable is 0, the returned remainder is 0. When the progress is 1, returned remained is 1. In fact, whenever your first modulo number is smaller than your second modulo number, you will be given your first number back. This is true for our length of 4, or 100, or 1,000.

When the numbers are the same, you get zero. 4/4=1, with no remainder left over. 100/100, no remainder. 1000%1000? Zero.

Next is when the number on the left is larger than the right. 5%4 will return 1. 6%4 returns 2. 7%4 returns 3.

Lastly, 8%4 returns 0. Because four goes into 8 twice with no remainder. 9%4 returns 1, and so on.

This means that modulo is a good, quick way to develop conceptual structures that increment, sequence, and/or loop. And further, these loops start at 0 as opposed to 1. Making them a perfect pair with arrays, which also start at 0.

However, my modulo crush might be a little over stated. I still had to use the if/else structure for the left button decrementing functionality. Try using my modulo method with a -- instead and see how the program breaks. Don’t worry, I won’t take it personally.

## Keys 1 through 4

You’ll notice I kept the 1 through 4 key press detection. They all seem to advance the slides just like the right arrow key does. Seems a little redundant. But each one of them has the additional functionality of changing the color, each in their own way.

This is more of a conceptual example. When we’re building interfaces, sending and receiving messages, and designing interactivity, there is opportunity in using multiple ins and outs while throwing in little bits of variation.

What if, when you write your script, you want to have a passage about diving underwater? “SPLASH!” is the next piece of text in your array. You can then press 2 to have your splash arrive with a cool blue wash over the screen.

But then you go to perform your piece at a tech poetry reading in Chelsea, and the vibe is all different than you expected. The bright blue and yellow suddenly strikes you as a bit gauche. And water paired with blue, isn’t that a little on the nose? It all felt so different rehearsing at home. Magenta, that's the one for this room. A bit darker, more mellow. But warm. A playful, dim romance. Press 3.

These are all programming questions and technical scenarios. If you want your art to seem less mechanical, if you want your performances to have more room for improvisation, consider introducing these little differences to identical functionalities. Walking “naturally” is a repeating of steps, but the speed, stride and direction can all vary in little ways. Even with something a simple as words, colors and shapes, we can introduce little bits of our artistic gait.

## Make your own

Now is the time to make your own piece. Perhaps this can be projected ten feet wide, while you stand in front of it. Or you could just do a screen recording while you speak the words. Or, maybe you can just write something for yourself, say it once right here and now, and never repeat it every again. In any case, if you’re struggling for something to say, tell the program something about yourself.

If you are having technical issues with the code, or just want to see what I came up with, you can look at or use the code below:

```
//color choices
var color1;
var color2;
var color3;
var color4;

//an array to hold all of the colors
var colors;

var displayText;

var mic;

/*
"+
"
*/

var textScript = ['You probably could just say “lalalalala” into the microphone and test the functionality of the code just fine. But you don’t. For whatever reason you decide to speak the words on the screen aloud, like a speech. Perhaps even if just under your breath. At first this spares you from feeling funny about appearing strange, blurting out some rant into the multicolored mess on the screen. However, you start to wonder how much your soft muttering is really affecting the height values of the squares being drawn.',
                  'You draw closer to your microphone, hoping for more visible results without risking any more of your ego. Now closer to the screen, you notice you might be making some difference. Though getting closer to the microphone has also brought your face closer to the screen as well. The previously invisible black grid in between the pixels vaguely starts to emerge.',
                  'You are squinting now, face lit up by the neon slurry of the screen. There is no escaping it, you’ll need to speak louder. Gradually, you raise your voice. There is a noticeable difference. Or maybe that is just in your head. You are expecting the changes to happen so maybe you are more primed to think they are happening (even when they are not). The pauses between words seem to help. Abruptly raising your voice at the beginning of each word seems to make the static pop to life. A kind of strange rhythm emerges in your speaking, bouncing up and down between muttering and recognizable words.',
                  '“Thats me,” you think to yourself. Perhaps a bit of a journey, but yes, you feel like the statement is right. Out of your mouth, into the microphone, through the hardware, into the operating system, flying through layers of drivers and system utilities, landing into your browser. Its you. You are looking at yourself, in a way. Certainly a strange mirror. But they aren’t really your words. Should you write your own?',
                 	'You were a shy child. Well, at first. Shy until certain occasions came up where your family and school mates were surprised to see you perform so boldly in front of so many people. Book reports, dance recitals, school plays. But after these outbursts, you would return to a more introverted and calm disposition. As these social surprises became more common, the unexpected became expected and people thought of you differently. You had changed, though not entirely sure where or when. Or how much.',
                 	'Eventually you stopped performing from scripts and started making your own things. Perhaps some music. A painting. Bad poetry. Oh wow, so much bad poetry. In fact, as you became an adult you started looking back at all the things you made with a little bit of embarrassment. Its ok, though. You have to start somewhere. Practice makes perfect. But now you always consider how what you make is going to look, going to sound. Why make something you’ll be unhappy with tomorrow? Best to think a bit first. Especially when so many people you know are making and doing so many amazing things.',
                 	'Of course, you have indulged this habit a bit too much lately. Thinking only a bit turned into thinking a lot. A whole lot. Inspiration comes in fits and starts, usually away from your gear and during busy occasions where you can’t spare a moment. You DO want to write your own words into the tutorial. But you simply don’t have any good ideas. You want to be able to write something amazing, something real. Something you wouldn’t feel strange about speaking out loud, at full volume.',
                 	'“Maybe later,” you think. A moment passes. “I’ll come back to it,” you half heartedly insist. You’re tired, anyways. And the flashing colors and static have made your eyes a little sore. How long have you been squinting for? What time is it? You roll your shoulders backwards and straighten out your spine. Aching back and neck, again. You close your eyes for an extended moment, seeing the multicolored snow dancing on the inside of your eyelids.',
                 	'“That’s enough for now,” you confidently decide. You eat a snack while watching some TV, then take a shower before going to sleep. You dream of filling up ice trays with cubes that take the shape of words and letters you can’t quite make out. Tray after tray after tray you pour water and load into the frosty machine. But your freezer doesn’t seem to run out of space. The water from the sink is never turned off, and becomes a singular source of white noise. A moving, rushing blankness. It feels good. You delve into a deeper, dreamless sleep.',
                	'end of the array',];

var scriptProgress;


function setup() { 
  createCanvas(400, 400);
  
  mic = new p5.AudioIn();

  // start the Audio Input.
  // By default, it does not .connect() (to the computer speakers)
  mic.start();
  
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
  
  
  //textScript = ['part1','part2','part3','part4'];
 	scriptProgress = 0;
  
  displayText = textScript[scriptProgress];
} 

function draw() { 
  background(75,75,75,25);
  
  var vol = mic.getLevel();
  var h = map(vol, 0, 1, 0, 20);
  
  //console.log(vol + " " + h);
  
  for(i=0;i<500;i++){
  	//fill(color1);
  	fill(random(colors));
    noStroke();
  	rect(random(width),random(height),10,h+1);
  }

  displayText = textScript[scriptProgress];
  
  fill(255);
  textSize(18);
  textFont('Helvetica');
  stroke(255);
  noStroke();
  //strokeWeight(1);
	text(displayText, 25, 25, width-35, height-25);
  
}

function keyPressed(){
  if(keyCode===37){
    console.log("left key detected");
    if(scriptProgress==0){
      scriptProgress=textScript.length-1;
    }
    else{
      scriptProgress--;}
  }
  if(keyCode===39){
    console.log("right key detected");
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  }
  
  if(key==1){
    console.log("keypressed 1");
    colors = equalColors;
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  
  }
  if(key==2){
    console.log("keypressed 2");
    colors = mostlyColor2;
   	scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  
  }
  if(key==3){
    console.log("keypressed 3");
    colors = mostlyColor3;
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  
  }
  if(key==4){
    console.log("keypressed 4");
    colors = mostlyColor4;
    scriptProgress++;
    scriptProgress=scriptProgress%textScript.length;
  
  }
  
}

```
