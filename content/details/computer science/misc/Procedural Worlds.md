* A collection of notes and insights on how to procedurally generate a world (i.e., how Minecraft and Dwarf Fortress do it)
# Noise Based Generation
* Consider how we store map data.
	* All methods of storage revolve around discretizing the representation in some form and generating data based on this representation [^cg]
	* Some options for discretizing include using Voronoi maps (hard to manipulate but smoother) and Tiled Arrays (easier to manipulate but may look artificial)

[^cg]: Analogous to [[Computer Graphics]] which makes use of vertices. In fact, we may think of terrain as a mesh and the vertices as our sample points


* With regards to generating map data, we require some form of noise function.
	* *Complexity is achieved by stacking layers of noise on top of each other*.
	* Noise has a few parameters: 
		* **Frequency** - controls the level of "zoom" that the noise function exhibits. More specifically, it bounds the gradient at each point in the map. *Higher frequency means a finer level of detail*
		* **Wavelength** - inversely proportional to frequency. Dictates the distance between seemingly repeating patterns in the map / noise function used.
		* **Octaves** - the number of frequencies we stack on top of each other. Each generated frequency is weighted with a corresponding amplitude.  For example
		  $$
		  x = \sum A_i \cdot \text{noise}(f_i)
		  $$
		  $x$ can be normalized to be between $0$ and $1$. 
	* One thing to be wary of is any visual artifact due to the noise function used
		* *Each term in an octave may overlap with each other and produce artifacts*. 
	* Note: *Perlin Noise is not uniformly distributed*. It roughly follows a [[Probability Distributions Zoo|Gaussian Distribution]].


* [More Noise Functions](https://www.decarpentier.nl/scape-procedural-basics). These are typically build off of Perlin Noise

* For maps, we can make use of curves (i.e., exponentiation curves) to exaggerate differences between troughs and crests.
* Generate [[Climate|biomes and climates]] using multiple maps that are related to each other. 
	* Some examples of maps to use:
		* Temperature 
		* Atmospheric Pressure
		* [[Atmospheric Moisture|Moisture]]
		* Level of [[The Earth and Insolation|insolation]], including seasonal effects
		* Latitude / Longitude.
	* We use some form of thresholding to differentiate biomes based on the values of the  different maps and our rules for what biome corresponds to each combination of condition.

* *Map generation can be viewed [[Algorithms|algorithmically]] as a pipeline for transforming or interpreting noise map data*. Each transformation in this pipeline is some function

* Islands on the map can be generated by using a **shaping function**. It takes the distance between a center point. The output of the shaping function is then used to weight the value of the map. 
* We can also apply **redistribution functions** which act on the value in the map and remaps them to a new value. Some examples:
	* Create ridges by accentuating the middle.
	* Make the map more discretized (using a staircase function).

* If we want to have the *map wrap around*, in such a way that the map remains continuous at the wrap around points, we can generate the map with a cylindrical, toroidal, or spherical projection in mind. 
	* One approach is to [generate the map one dimension higher](https://ronvalstar.nl/creating-tileable-noise-maps), create a loop in this high dimensional space, and then project down to our desired dimension. 
### Key Algorithms
* Perlin Noise
* Wavelet Noise

## Simulation Based Approaches


# Links
* [Undiscovered Worlds](https://undiscoveredworlds.blogspot.com/2019/01/aims-and-methods.html) - Guidelines for Procedurally generated worlds
* [Red Blob Games Making Maps with Noise functions](https://www.redblobgames.com/maps/terrain-from-noise/)
* [Azgaar's Blog on Procedural Worlds](https://azgaar.wordpress.com/)