* A good design starts with a great **silhouette**. This makes the art more recognizable.
* A general principle: Break down the desired object into simpler shapes -- cones, spheres, and cubes.

# Lines and Curves 
* *To achieve smooth curves:* 
	* Vary the lengths of the segments in a continuous manner. This prevents Jaggies 
	* No right angles. This prevents Doubles 

* Given a straight line to span a width $w$ and a height $h$, we can determine how to draw it [^1].
	* When $w > h$ we want to favor drawing horizontal runs of pixels. When $w < h$ we favor vertical runs. 
	* Say that the line grows is to be extended vertically, the line grows starting from the centermost pixel. In increments it goes half, third, fourth, and so on until all runs of pixels have the same length.  *This makes the line appear smoother since the "irregular pixels" appear at regular intervals*. 

* The following rules apply to curved lines. 
	* The curve can be approximated using tangent lines. A less curvy line will have a longer middle segment (that is just roughly a straight line) [^2]


[^1]: Using the line tool is a shortcut for this 
[^2]: The less curved a line is, the better the [[Differential Calculus|derivative]] approximates it so the more the points around the line follow the 45-degree line. 

* One technique to make a smooth curve is not necessarily to follow a strict 1-2-3 progression. Rather, we can do 1-2-1-2-1-3  instead.  That is, simulate the smoothness by "staggering" the rows of pixels. 
# Shading and Coloring
* Consider *shading techniques*
	* **Flat Shading** - involves stacking colors. Fewer colors = crisper object. We can texture this by varying the shadow's edges.
	* **Dithering** - involves creating a gradient (i.e., for diffused lighting or see through-effects). We then apply a repeating pattern on the boundary between colors.
* Consider *outlines*: 
	* *Softer outlines = object looks out of focus*.
	* Having a border makes the object pop.
	* Imperfect outlines look more natural. Achieve this by *selective coloring for different parts*.
		* Note: Maintain contrast between the base color and the outline to make it pop out of the background.
* *Pixel art can be thought of as sculpting with color* - we assemble the forms through blobs of color.
* [[Color Theory]] would be really helpful to apply. 
* *No lone pixels*. Colors should occur in clusters (or in dithering).

# Texturing 
* The following principles apply (from [Sylnyrd](https://www.slynyrd.com/blog/2018/2/15/pixelblog-2-texture)) 

* *Simplify* - pixel art isn't about being too detailed. Simplify the texture details. 
* *Repetition* - repeat clusters in a distributed pattern. This further simplifies the texturing work 
* *Balance* - make sure that the texture feels balanced 
* *Contrast* - vary the texture at interesting points to highlight areas. This also helps guide the audience's eyes so that the work doesn't feel cluttered
* *Avoid orphan pixels* - the exception is if they are not obviously floating alone. 

# Links
* [[Make Your Own Pixel Art -- Create Graphics for Games, Animations, and More by Dawe and Humphries]]
* [Lines and Curves](https://opengameart.org/content/chapter-2-lines-and-curves)
* [Pixelblog by Slynyrd](https://www.slynyrd.com/pixelblog-catalogue) 

* [[Creativity]]
* [[Illuminating Rendered Objects]] - more on principles for shading.