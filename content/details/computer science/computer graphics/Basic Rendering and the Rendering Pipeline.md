# Object Representation
* All objects in rasterized rendering are composed of **triangles**.
	* Every triangle has three vertices. The order of these vertices is important
	* **Vertices** are collections of arbitrary data (not necessarily limited to spatial data).
	* Collections of triangles form **meshes** or geometry which are then rendered by the renderer.
	* The **topology** of a mesh pertains to how its vertices are interconnected.
		* This also corresponds to how vertex attributes such as normals are connected.
# Rendering Pipeline
* Vertex coordinates are transformed in the following sequence using a series of [[Projection|projection]] matrices.
	* **Model Space** - the space that a particular object begins in.
		* Model spaces can be hierarchically arranged so that objects are positioned relative to other model spaces.
	* **World Coordinates** - relative to a globally defined origin.
		* This is usually determined by placing the camera in a convenient place.
	* **Camera Space** - relative to the perspective plane of the camera.
	* **Clip Space** - represented using **clip coordinates** as $(x,y,z,w)$. 
		* $w$ represents the visible range of the clip space for that vertex.
		* If $-w\le x_c \le w$, then the object's $x_c$ coordinate is in view.
	* **Normalized Device Coordinates** - an extension of clip coordinates but of the form  $(\frac x w,\frac y w,\frac z w,1)$..
		* An object's coordinate $x_c$ is in view if $-1\le x_c \le 1$
	* **Window / Viewport Coordinates** - relative to the active window or viewport.
* On rendering, *triangles are broken into fragments* by projecting the triangle on the screen and considering each pixel inside the projection. These pixels are then colored. 
	* **Color Space** - coordinates where each basis represents a reference color (i.e., RGB). 
* *All objects are rendered based on the order they are given by default*.
* **Face Culling** involves not rendering triangles that are not visible to the camera.
# Shaders
* *Programs that run on the renderer (GPU) to render graphics*.
	* **Vertex Shaders** handle vertex data, one vertex per invocation. *At the very least, they output a clip-space position of the vertex*.
	* **Fragment Shaders** handle fragment data based on vertex data (in window-space), one fragment per invocation, and potentially using interpolation from the vertex data.
* **Buffers** are lists used to transfer additional data from memory to the shader kernel. These are designed to be read quickly by the renderer.
* **Indexes** are used within buffers to index vertex positions to reduce the amount of space occupied by vertex data. 
* **Uniforms** are constants that are defined within the shader but set outside of the shader. *For efficiency, uniforms can be shared between multiple shaders*.
# Camera and Projection
* Cameras make use of **perspective projection** to render a 3D scene onto a 2D viewport.
	* This is done by projecting the 3D scene onto a **viewing frustrum**.
	* The dimensions of the inner rectangle of this frustrum must have the same **aspect ratio** as the target viewport to ensure proper proportions.
### Projecting Depth
* To render objects in depth properly, we use **depth-buffering**. *This helps ensure proper occlusion of objects in space* by providing a buffer containing depth information.
* The idea, then, is to not render fragments which are farther from the viewer on pixel positions that have already been rendered.
* *Depth is, by default encoded as the window-space $z$ value*.
### Clipping
* **Clipping** - the process by which a mesh partially outside of clip space gets broken into smaller triangles that are within clip space.
* Clipping also *solves the problem of dividing by zero* when computing for perspective projection by simply not drawing vertices that are clipping through the camera.
* The **clipping plane** cuts any objects passing through it so that they may be clipped.
* **Depth Clamping** - turns off the camera near / far plane clamping. Instead, it clamps the depths at $[-1,1]$. in NDC space.
	* Be careful with this as objects that are depth clamped and overlap may look wrong because both their depths are clamped.
	* Also, the triangle must not extend past $0$ in camera space.
# Orientations
* *The easy solution is through three rotations applied  in sequence* . These are represented via **gimbals** which control the rotation at certain predefined axes.
	* This may lead to **gimbal lock** where the axis of rotation for two gimbals are parallel, causing them to have the same effect permanently.
* *The preferred way is through quaternions*.
	* [[Complex Numbers and Quaternions|Quaternions]] have the bonus of being easy to renormalize, thus making them more numerically precise.
	* Any rotations are then relative to the current orientation of the model.
	* It is also easy to interpolate quaternions visa **spherical interpolation**.

# Links
* [Learning Modern 3D Graphics Programming Ch. 1 - 2](https://paroj.github.io/gltut/index.html)
