# Tips 
* Prefer to use Meshes as primitives Use the mesh that is closest to your target shape.
* High poly is hard to render, hard to tweak. *It is easier to add resolution / polys than it is to remove*
	* That said, do not go low resolution for round objects.
* *Things that look perfect also look too fake*. Most of 3D rendering is about making imperfections in a realistic way.
* **Z-fighting** - a rendering issue where a face is on top of another face and the renderer is unsure of which to render (appears as flickering) 
* **Backface Projection** - Happens when one face of the mesh is projected to the wrong side of the other mesh. 

# Engine Notes 
* The default view is in **Viewport Shading** which gives a lightweight view of the scene without lighting. Switch to **Render mode** to bake lights
* Immediately after adding objects, there is an option to tweak it that is available (bottom left). This option disappears after any action is performed. Press `F9` to make it reappear.
* Consider **Modifiers** which apply to the mesh as a whole (top to bottom)
	* **Viewport Subdivision** - add subdivisions to increase the mesh's resolution and make it look smoother from either Viewport or Render mode (or both ).
	* **Solidify** - add a thickness to the mesh.
	* **Shinkwrap**- allows an object to shrink to the surface of another object, effectively making the vertices snap to the other surface's vertices.
* Consider **Sculpting** for adding complex shapes and details.
	* 

* `E` - when an edge is selected, it Extrudes
* `F` - change the size of brush in Sculpt Mode
* `G` - Grab (move object). Note that this will make the object move with your cursor regardless of where it is
	* `MIddle axis drag` - move along the nearest axis (X, Y or Z).
	* `X, Y, Z` - move along X / Y or Z axis.
* `H` - Hide parts of mesh (based on selection)
* `N` - properties 
* `O` - Proportional Edit mode - allows changing a mesh vertex and any adjacent vertices. Select the vertex and then press `G`. `Scroll Up / Down` to increase or decrease the sphere of influence
* `R` - Rotate object.
	* `Middle axis drag` - rotate along  X, Y or Z 
	* `X, Y, Z` - move along X / Y or Z axis.
* `S` - Scale object
	* `Middle axis drag` - scale along  X, Y or Z 
	* `X, Y, Z` - scale along X / Y or Z axis
* `Tab` - switch from Object to Edit mode (to edit meshes)
* `F2` - with selected object. Rename 
* `F12` - render image based on the POV of the camera and save the image.

* `Shift + A` - Add object 
* `Shift + D` - Duplicate object 
* `Shift + F` - Change brush intensity of sculpt brush.
* `Shift + Tab` - Turn on snapping
	* If snapping doesn't work try adding more resolution
* `Shift + Middle Mouse Drag` - Pan 

* `Alt + Click` on a mesh in Edit mode - selects the edge (goes in a straight line)
* `Alt + H` - unhide hidden elements of the mesh
* `0` - Camera view
# Links 
* [[Computer Graphics]]
* [Blender Tutorial for Complete Beginners by Blender Guru](https://www.youtube.com/watch?v=B0J27sf9N1Y&list=PLjEaoINr3zgEPv5y--4MKpciLaoQYZB1Z)