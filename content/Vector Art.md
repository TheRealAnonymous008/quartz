1. *Drawing with only the Pen Tool is like a [[Puzzle]].* 
	* The goal is to draw a desired shape, possibly matching one of the reference shapes or one visualized.
	* The constraints are  not only the shape, but also the handles that move the Bezier curves and line segments around.
	* Additionally ,we  want to minimize the number of vertices that we use. 

2. Like [[Pixel Art]], we can think in layers. Layers comprise shapes that are found in the figure, so we should decompose the image into its constituent components. *Think in terms of silhouettes.* 

3. We can separate the outline from the fill. 
	* Doing so allows us to structure the layers as  bg > content > fg 
	* We can also add finer details on top of the coarser layers. This is preferable compared to making the coarser layers more complicated than they need to.

4.  *Handling symmetric figures* is both easy and difficult -- 
	* On one hand we can simply draw one part of the symmetry and apply repeated reflections.
	* On the other hand, placing the copies relative to each other to maintain symmetry requires the use of guides and careful fine tuning.
	* Alternatively, use coordinates to do the positioning.

5. Prefer to draw a coarse outline in one pass rather than starting with a blob and "sculpting it".
	* It is much easier to visualize the figure when you can see the outline itself. 
	* When doing this, remember the three kinds of transition points that exist on a Bezier curve.
		* **Corner points** - are meant to join two segments together, but other than that the segments themselves are independent of each other.
		* **Smooth points** - the tangent lines from this point have a common angle and form a straight line.
		* **Symmetric Points** - the tangent lines from this point have a common angle, form a straight line, and have equal length. 



# Links
* [Intro to Bezier Curves in Krita](https://www.youtube.com/watch?v=cJUZDt1qNrg)
* [[Creativity]]