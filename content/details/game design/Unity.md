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

# Topics 
* [[Computer Graphics]] - the theory of computer graphics.

# Links
* [Compute Shaders](http://kylehalladay.com/blog/tutorial/2014/06/27/Compute-Shaders-Are-Nifty.html)
	* [More on Compute Shaders](https://www.youtube.com/watch?v=BrZ4pWwkpto)
	* [Pathtracing With Compute Shaders](http://blog.three-eyed-games.com/2018/05/03/gpu-ray-tracing-in-unity-part-1/)
* [Entity Component System Overview in 7 Minutes](https://www.youtube.com/watch?v=2rW7ALyHaas) 
