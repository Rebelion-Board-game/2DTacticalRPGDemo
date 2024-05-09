A Godot 4.x demo project for a tactical 2D RPG.

## Features
* Setup combatant and skill definitions in databases using Autoloads
* Combatant movement on a 2D grid
* Support for different movement costs for tiles
* Support for flying units
* Support for blocking certain unit classes from entering specific tiles
* Simple melee enemy AI

## Additional Credits
Graphical assets created by DENZI under the CC-BY-SA 3.0 license:
https://opengameart.org/content/denzis-32x32-orthogonal-tilesets

## Documentation

before we can use ```add_combatant```   
we have to use ```create_combatant``` method, where is created unit from```combatant_databse```.    

### Databases

This tactic engine contain 2 databses:
- ```skill_database```
- ```combatant_database```
Both databases are represets as dictionary defined in ```combat\resources\**Definition.gd```.

### Skill_database

-  name: String
-  min_range: int
-  max_range: int
-  min_damage: int
-  max_damage: int
-  min_prob: int
-  max_prob: int
-  icon: Texture2D

### Combatan_database

-  name = ""
- group("Class")
- enum("Melee", "Ranged", "Magic") var class_t = 0
- enum("Ground", "Flying", "Mounted") var class_m = 0
- group("Stats")
- range(1, 2, 1, "or_greater") var max_hp = 1
- range(1, 3, 1, "or_greater") var movement = 3
- range(1, 2, 1, "or_greater") var initiative = 1
- group("Visual")
- icon: Texture2D
- map_sprite: Texture2D
- hframes: int
- vframes: int
- frame: int
- group("Skills")
-  skills: Array[String]

# Camera Controls and Behavior

The camera in this 2D tactic engine can be controlled using the following methods:

- **WASD Keys**: Pressing the W, A, S, and D keys allows for moving the camera up, left, down, and right respectively.
- **Arrow Keys**: Similarly, the arrow keys can also be used for camera movement, with the up arrow moving the camera up, the left arrow moving it left, the down arrow moving it down, and the right arrow moving it right.
- **Middle Mouse Button**: Holding down the middle mouse button and moving the mouse allows for panning the camera in any direction.

Additionally, at the beginning of every turn of every unit, the camera receives a signal from `Combat.gd` indicating the start of a new unit's turn. Upon receiving this signal, the camera automatically centers itself on the current active unit, ensuring that players have optimal visibility of their unit's surroundings during their turn.