# Miscellaneous 
* Unity now supports [[Object Pool|object pooling]] out of the box using `ObjectPool<T>`. This allows for a stack based object pooling system. 
* Use `ScriptableObject` for objects that are not in the scene (i.e., they are not required to be game objects). Otherwise use `Prefabs`. See more [here](https://www.youtube.com/watch?v=E-vIMamyORg)

# Meshes
* **Mesh Filter** - stores information about the mesh itself.
* **Mesh Renderer** - responsible for rendering the mesh itself.
* All triangles in Unity are drawn in a clockwise manner.

# Compute Shaders
* Compute Shaders work with either `RenderTextures` or `StructuredBuffers`.
* Data is transferred from the CPU to the GPU via setting buffers, uniforms or textures. 
* The general flow for using Compute Shaders in Unity seems to be as follows:
	* **Initialize** any relevant data that is to be processed by the GPU.  
		* Construct any textures as `RenderTextures`. We may **blip** from a Texture2D object to a `RenderTexture` object as needed.
		* Construct any structured buffers for other data that needs to be sent to the shader.
	* **Pass all relevant data to the compute shader**. (i.e., via Setter methods on the shader object itself)
	* **Dispatch** the compute shader to signal to the GPU that it should run.
	* **Use** any outputted textures from the GPU in the program.
* *Prefer the use of structures*. It makes it easier to map to Structured Buffers.
* *Prefer the use of buffers when there is a need for precision*. 
* *Prefer outputting textures for grid-based data*. 
	* Keep in mind indexing operations require casting to `int2`.

# DOTS
## Use Cases 
* The game contains a lot of dynamic entities
* The game requires complex algorithms such as procedural generation, pathfinding, dynamic AI, and heavy physics.
* Competitive Multiplayer games that requires low latency and high accuracy 
* Large Scale Simulations
* Running simulations in performance critical devices. 

* *It is difficult to switch from MonoBehaviour to ECS. It is best to decide whether to use ECS early on in the project* 
## Packages 
* **Entity Component System** - uses data oriented design to separate data from game logic which leads to modular, performant, and robust code.
	* **Entities** - corresponds to data components that represent one thing or part of a thing. Treated as part of a [[Database]] as it has a version number and index (for identifying which object it corresponds to). 
	* **Component** - corresponds to the data associated with an entity stored in chunks which allows for fast [[Cache Memory|access]]. 
	* **System** - data transformations which modify values based on the gameplay. It runs on groups of entities with specified data components. It can be integrated with Jobs to allow for [[Multiprogramming|Multithreading]]

* **Entities Graphics** - used for rendering entities in the game world. 

* **Netcode for Entities** - multiplayer networking compatible with ECS. 
	* It allows for speed and accuracy when it comes to networked games 
	* It is server authoritative so the simulation can run on the server. 
	* Allows for client prediction to offset the latency caused by transferring data from client to server. 
	* Simulated Rollbacks allow for undoing the simulation when there is a discrepancy between client side and server side.
	* Allows for high multiplayer counts. 

* **DOTS Physics** - free package for Physics
	* Stateless physics system. 
	* No OnCollisionEnter or OnCollisionExit
	* Optimized for multiplayer (i.e., allows for simulated rollback)
	* Has built-in spatial querying to find entities in an area. 

* **Havok Physics** - paid package for Physics. Interchangeable with DOTS Physics. It is stateful but highly accurate. 

* **Job System** - allows for multithreading in Unity 
	* Automates scheduling and includes safety checks to avoid multithreading issues (i.e., deadlock and race conditions)
	* Allows for the benefits of multithreading and parallelization in Unity.
	* It is intended for work that needs to be completed within the same frame. 
	* It can only be used on unmanaged data types. 
	* It can be burst compiled. 
	* Compatible with both ECS and MonoBehaviour. 

* **Collections** - a list of unmanaged [[Data Structure|Data structures]] 
	* Has some garbage collection capabilities but still requires memory management. 
	* Has built-in safety checks (though there are unsafe variants that do not have these checks)

* **Burst Compiler** - compiles code into native CPU code. It supports SIMD code. 

* **Mathematics** - includes burst compatible types. 

## Using DOTS 
* Components should only contain data not behaviors (see [[Clean Code Principles|here]]). 

# Topics 
* [[Computer Graphics]] - the theory of computer graphics.

# Links
* [Compute Shaders](http://kylehalladay.com/blog/tutorial/2014/06/27/Compute-Shaders-Are-Nifty.html)
	* [More on Compute Shaders](https://www.youtube.com/watch?v=BrZ4pWwkpto)
	* [Pathtracing With Compute Shaders](http://blog.three-eyed-games.com/2018/05/03/gpu-ray-tracing-in-unity-part-1/)


* [Entity Component System Overview in 7 Minutes](https://www.youtube.com/watch?v=2rW7ALyHaas) 
* [Should You Use DOTS in 2024](https://www.youtube.com/watch?v=Bz24Jp30nkM)
* [Exttreme Performance with Unity DOTS](https://www.youtube.com/watch?v=4ZYn9sR3btg)
