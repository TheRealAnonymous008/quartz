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

5. In some cases, it is infeasible to plot all the vertices first. In which case, we can build the figure gradually. *Start with a "loop" two vertices connected to each other*.  Then, keep adding vertices in between, following the outline. adjusting as needed
	* It helps to have fill enabled for the shape to see the general figure better. Still, follow the lines and not the shape.
	* To make protrusions, remember to create three points. Two points are where the protrusion joins the main "stem", and the other is the point at the apex of the protrusion.

# Links
* [[Creativity]]