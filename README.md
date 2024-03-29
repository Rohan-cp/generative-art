# generative-art

Usually, as a programmer, you have a bunch of specifications and you write code to fit them. Here, however, you take directive on what to do or make. The only rules for what's on the canvas are created by you. For me, it's a nice break to think of coding in this different paradigm (and trust me when I say it is different). For example, you can use the coordinates of a circle's origin (x, y) on a canvas to determine its color by RGB like (x, y, 0) for this case. You would almost never think about these kind of things with other programming. I thought this idea was really interesting and I wanted to share some of my explorations into generative art.

To give you a taste of what I'm talking about, this is one of the first sketches I ever made and it actually uses the idea mentioned above. Here, not only the color of the circle but its size is also dependent on its x-coordinate to create this interesting light funnel.


<img src="https://imgur.com/Do1H240.png"> </img>



There were two main aspects of visual generative art I wanted to explore: 
<ul>
<li> Using Math: leveraging math functions and models (like trig functions, fractals, bell curve) </li>
<li> Experimentation: being able to experiment with different aspects of a piece (colors, coordinates, radius, number of objects rendered) manually changing or randomising them (including pseudo-randomiser functions like Perlin Noise) and hit run to create a different variation every time. </li>
</ul>

## Using Math
For the first aspect, I ended up using the sine function to make the following piece. At first glance, do you think you can tell where or how the sine function is used here? 

Well, I use it to determine the radius of the circles generated. So you can see that the radii of the circles basically increase and decrease from the center to the edges of the image. The rate of change of the circle radii is waves like sine.

<img src="https://imgur.com/oYpcXmE.png"> </img>


In fact, I used the following code to also set the color of the circles in RGB. Here the blue part of the circle's color would follow the sine wave path (to increase and decrease with circle size) and the green part was dependent on the distance of circle from the center of origin. This is why you can see a nice gradient in the color of circles from the center of the sketch outwards to the edges.

```javascript
// (400, 300) is the center of the sketch and (x, y) is origin of the circle
var d = dist(x, y, 400, 300);

// determine red, blue and green part of circle's color
var r = 128;
var g = 255 * sq(sin(d));
var b = d;

// fill color in RGB format
fill(r,g,b);
```
The following is another piece that uses the bell curve for the distribution of circles rendered (won't dive much deeper into this).

<p align="center">
  <img src="https://imgur.com/QdzGyls.png" height="70%" width="70%"> </img>
<p align="center">

## Experimentation
So the following one is a lot simpler but very to fun to play with. I could tinker with the number of circles rendered and the color schemes and I'll share my favorite variation.

<p align="center">
  <img src="https://imgur.com/PDMTG3t.png" height="90%" width="90%"> </img>
</p>

This next one was by far the most fun exploration. I used Perlin Noise to translate each pixel in a grid of same-colored pixels to randomly move a certain amount vertically or horizontally (pretty basic right). The noise comes in to determine this shift and it does so by considering the neighbour pixel's shift creating this pattern. One of the best aspects of this is to hit re-run and see a different version of your sketch come to life. I'll share three variations here (I actually spent all day once trying out different color schemes and ended up liking the very first one I tried the most—sigh I guess).

<img src="https://imgur.com/pTIOKNi.png" > </img>

<img src="https://imgur.com/zfLej6F.png" > </img>

<img src="https://imgur.com/i494fda.png" > </img>

Ok one more.

<img src="https://imgur.com/xqHAMP4.png" > </img>

## Planned future explorations
<ul>
<li> Experiment with input from real world (like visualising sound, using weather or atmospheric data) </li>
<li> Work on making pieces dynamic (like following your cursor or just having rendered objects move or change in shape, size and/or color). 
<li> Specific instances of the above point basically: simulate water flow and fire (separately). Water because I've always been interested in turbulent flow and I have tried to capture it many times in my drawings and I think I'll fare better with code for this. Fire because it just seems like an interesting challenge.
</ul>

I also want to say that all of my sketches here were made on [OpenProcessing](https://openprocessing.org) and are inspired by youtube videos and online forums. If you're interested in generative art I highly recommend you check out [Algorithmic Art](https://www.youtube.com/channel/UCO6iBPzIvUdzxcf87BN24FQ). Feel free to reach out to me at rohancp9@gmail.com if you wanna play around with code for any of these.
