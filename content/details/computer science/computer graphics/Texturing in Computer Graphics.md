# Demystifying Textures
* *Textures are not that important*. Not all computer graphics problems require textures to solve.
* *Textures are not always  pictures*. 
* *Textures are just large look up tables accessible from shaders*. Data within textures are called **images**, and these are multidimensional entries.
* *Textures are tools*. Use them as needed when they are needed.
	* They can be used to *vary material parameters across a surface*.
# Sampling and Mapping
* **Texture Sampling** pertains to fetching data from a texture at a particular location or **texture coordinate**.
* Texture Coordinates are expressed as **$u,v$-coordinates** whose coordinates are normalized to be between $[0,1]$.
* **Texture Mapping** pertains to associating triangles on a mesh to texels on a texture.
* **Projective Texturing** is a special form of texture mapping wherein texture coordinates are generated for a texture such that it appears the texture is projected onto a scene.
	* This is done by projecting from mesh coordinates to texture coordinates.
* **Cube Maps** are special texture where texture coordinates correspond to a 3D vertex direction.
# Artifacts and Techniques
* **Aliasing** can appear within textures when used as images. They manifest as **jaggies**. 
	* This can be solved via **texture filtering** to *magnify or minify* the texture based on the required resolution.
	* This is done by sampling and interpolating texels.
* **Loss of Detail and Fluttering** manifests when the texture is too far away, causing it to appear wrong when magnified or minified.
	* **Mipmaps** can solve this by creating a sequence of progressively small images that allow for better level of detail.
		* Mipmaps improve performance at the cost of requiring more memory.
		* *Textures used as lookup tables do not need mipmaps*.
		* *Mipmaps should operate on linear color spaces.*.
	* **Mipmap Filtering** involves interpolating between mipmap levels so that changes between mipmap levels is much smoother.
	* *Note*: Mipmaps on their own sample from all directions equally. However, for more oblong, diagonal shapes, this will leave isotropic artifacts.

* Textures can be **misaligned**.
* **Isotropic Artifacts** manifest when the texture from perspective looks wrong because the shading of each pixel does not account for diagonals being farther away.
	* **Anisotropic Filtering** removes isotropy by filtering in a non-square box.
* There can be potential issues with **gamma correction due to textures** since some textures are in a non-linear color space by default.
	* Mitigate this by *linearizing first before applying gamma correction*

# Links
* [[Illuminating Rendered Objects]] - for more on lighting.

* [Learning Modern 3D Graphics Programming Ch. 4](https://paroj.github.io/gltut/index.html) 
	* Ch. 17 - shows an application for textures for varying light intensity
