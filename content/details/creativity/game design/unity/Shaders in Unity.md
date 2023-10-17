# Compute Shaders
* Compute Shaders work with either RenderTextures or StructuredBuffers.
* Data is transferred from the CPU to the GPU via setting buffers, uniforms or textures. 
* The general flow for using Compute Shaders in Unity seems to be as follows:
	* **Initialize** any relevant data that is to be processed by the GPU.  
		* Construct any textures as RenderTextures. We may **blip** from a Texture2D object to a RenderTexture object as needed.
		* Construct any structured buffers for other data that needs to be sent to the shader.
	* **Pass all relevant data to the compute shader**. (i.e., via Setter methods on the shader object itself)
	* **Dispatch** the compute shader to signal to the GPU that it should run.
	* **Use** any outputted textures from the GPU in the program.
* *Prefer the use of structures*. It makes it easier to map to Structured Buffers.
* *Prefer the use of buffers when there is a need for precision*. 
* *Prefer outputting textures for grid-based data*. 
	* Keep in mind indexing operations require casting to `int2`.
# Links
* [[Computer Graphics]]

* [Compute Shaders](http://kylehalladay.com/blog/tutorial/2014/06/27/Compute-Shaders-Are-Nifty.html)
	* [More on Compute Shaders](https://www.youtube.com/watch?v=BrZ4pWwkpto)
	* [Pathtracing With Compute Shaders](http://blog.three-eyed-games.com/2018/05/03/gpu-ray-tracing-in-unity-part-1/)


