* The goal of lighting models is to render in a way that is as close to realistic or as close to a desired style as possible.
# Parameterizing Light
* Rather than capture all wavelengths, we *use a sample of wavelengths at different intensities*. The standard case is to use RGB. The **intensity** of the light is from $[0,1]$.
* **Angle of Incidence** - refers to the angle by which light strikes a surface and thus how much light is received.
* **Angle of View** - refers to the angle by which light comes from a surface and onto the eye.
* **Attenuation** - refers to adjusting light such that its intensity is smaller when viewed from farther away.
	* This can be done via **linear attenuation** or **quadratic attenuation** so that the intensity is inversely proportional to distance and square distance respectively.
	* Alternatively, we can clamp the attenuation such that if the light is above a certain distance from the source, it has $0$ intensity.
* **Specular Exponent** - controls the degree of specular lighting to be used in lighting.
* **Maximum Intensity** - the maximum intensity of the light (within HDR space). Any light above this intensity gets clamped.
# Light Sources 
* **Local Illumination** pertains to lighting that only comes from light sources.
* **Global Illumination** pertains to lighting that comes from both light sources and the reflection of light off of surfaces.

* **Directional Light Sources** direct light to a particular direction. 
	* This is useful for when we do not want the angle of incidence to change significantly when we move the light source close.
	* These model light sources that are extremely far away from an object to the point that light only strikes in one direction.
* **Ambient Light** - lighting that emanates off of every object on the scene, coming from all directions equally. In effect, *every object receives a little bit of light intensity*.
	* The intensity of ambient light can be changed (for example to simulate day and night).
	* This is meant to *simulate global illumination*.
* **Point Light** - light that has a position and from which light shines with in all directions.
* **Spotlight** - light source that emits from a position in a generally conical or cylindrical shape at a given direction.

# Lighting Techniques
* **Diffuse Lighting** pertains to when the light reflects from the surface at many angles rather than as a mirror.
	* **Lambertian Reflections** pertain to the ideal case where light is reflected evenly on all directions.
* **Specular Lighting** pertains to when the light strongly reflects off the surface in a perpendicular manner.
	* This gives objects shininess.
	* **Specular Highlights** are highlights due to specular lighting caused by direct illumination from a light source.
	* *Specular Highlights do not linearly interpolate well*.
* **Microfacets** - refer to imperfections on the surface which introduce roughness.		
	* This is controllable by *adjusting the distribution of surface normals*.
	* The **Phong Model** is a simple model which states that light reflected in the direction of the viewer varies based on the difference *between the view direction and direction of perfect reflection*.
		* One limitation of this is depicting rough surfaces that still have specular highlights since *it does not allow specular contributions from areas outside a certain region*
		* Another limitation is it *only allows for view angles less than $90\degree$ have a specular contribution.* 
	* The **Blinn-Phong Model** is an extension of the Phong Model.
		* It does this by checking if *the half angle is aligned with the surface normal*. 
	* The **Gaussian Specular Model** is an extension of the Blinn model which *actually simulates the microfacets*. It assumes that at a given point, the intensity *follows a normal distribution parameterized by the half-angle offset from the surface normal*. 
		* This is parameterized by a  **Gaussian Smoothness** parameter that controls the apparent smoothness (from $[0,1]$ )
		* It offers more distinct highlights for shiny surfaces.

* **High Dynamic Range Rendering** simulates how the human iris adjusts based on the luminance of the environment (i.e., at day, the iris lets in less light to not damage the retina).
	* This manifests as *filtering out some of the light*. 
	* Additionally, we note that *light does not have global maximum brightness*, but this necessitates **tone mapping** from HDR to **Low Dynamic Range**. 

* **Gamma Correction** involves controlling the overall brightness of the image to *account for non-linear color spaces in the display device*. 
	* It involves a parameter $\gamma$. The correction simply involves doing the following for the linear color $c$ $$c^{-\gamma}$$
	* Gamma encoding, where $\gamma < 1$ makes the dark regions lighter.
	* Gamma decoding, where $\gamma >1$ makes the shadows darker.
	* Without gamma correction, light sources tend to look extremely bright even when the rest of the scene is dark.
	* It also allows for details within the darkness to show up more easily.
	* *Do not use gamma correction for color spaces that are already non-linear such as sRGB.*
# Artifacts
* **Light Bands** occur in specular diffusion, manifesting as a sharp cutoff between the specular highlight and dim areas. This is due to the light facing the object a certain way.
* **Light clipping** occurs when the intensity of the light exceeds the allowable range of $[0,1]$, causing the object to lose all detail and instead be rendered as absolute white.
# Shading Techniques
* **Gouraud Shading** involves lighting each vertex and then interpolating the light across the triangle surface.
	* This is an ancient and inaccurate technique, however, as it is limited to diffuse lighting and the performance constraints are no longer a concern.
* **Fragment Lighting** involves interpolating both normals and the light direction on the fragment 
	* This removes artifacts due to using vertex only shading, which are more apparent when the triangle is close to the light.
# Materials
* **Materials** are effectively containers which store parameters for how a surface should be illuminated.
* The **diffuse color** pertains to the color to be given off due to diffuse lighting.
* The **specular color** pertains to the color to be given off due to specular lighting.
# Impostors
* *Lighting can be used to make an object appear different from what is expected from its geometry*. This is through **impostors**.
* This allows using objects as placeholders to invoke the fragment shader to make it look like something else (e.g., a box mesh that is rendered as a perfect sphere)
* This can be made accurate with **ray tracing** so that the impostor behaves correctly when viewed from the camera
# Computational Aspects
* We make use of *normal vectors*. Each vertex in a mesh will be assigned a normal vector.
	* Regions in a fragment are then shaded based on the normals of its vertices.
# Links 
* [[Basic Rendering and the Rendering Pipeline]] - for more information on how to render and position objects.

* [Learning Modern 3D Graphics Programming Ch. 3](https://paroj.github.io/gltut/index.html)
