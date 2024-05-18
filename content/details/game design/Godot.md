* Use your scenes to organize the game hierarchy.
	* Have a scene for the player character. 
	* Have a scene for the level. Any additional game objects in the level may also correspond to a scene. 
	* Use Node2Ds and Node3Ds to organize the scene.

* Tilemaps have layer functionality  which lets you layer where tiles from a tileset (for example one layer for walls, one layer for soil).
* Metadata is essentially Godot's version of Editor scripts from [[Unity]]

* Project > Project Settings > Input Map to set controls
* For handling mouse events, you will often need to map the Mouse's position into the Node's Local Position. Use `Node.ToLocal()`
* Always prefer to have the root's transform to be the default transform. This will make placing it around as a scene much easier. 

* Canvas Layers are used as the root of the UI because they are always independent of camera movement.

* Use a `globals` folder to store your global variables to be used for Autoloading. This is especially useful to act as a global [[Singleton]] that is accessible by all scenes. This means that a UI and a game logic scene can both access and modify these variables without having to resort to [[Clean Code Principles|unclean]] message passing.
* Modify the stretch settings from the project settings to allow the window to be robust to resizes.


* Prefer to work with sprites first rather than resorting to tilemaps immediately. Tilemaps should be used only when you are certain that the game elements will be static. Regardless, [[Object Oriented Programming|OOP]] applies and we should make things easily adjustable.

# Links 
* [The Ultimate Guide to Godot 4 by Clear Code](https://www.youtube.com/watch?v=nAh_Kx5Zh5Q)

* [Godot Website](https://forum.godotengine.org) - good source for up to date documentation. 
* [Godex](https://github.com/GodotECS/godex) - brings Entity Component System to Godot. 
* [Dialogic](https://docs.dialogic.pro) - allows easy to create RPGs and Visual Novels.