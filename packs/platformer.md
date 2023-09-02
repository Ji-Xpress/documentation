# Platformer Pack Documentation

## Objects

* `block` - Physical Block (Movable).
* `game_console_character` - Player character - game console.
* `boy` - Boy Charater.
* `girl` - Girl Charater.
* `soldier` - Soldier Charater.
* `door_open` - Open door.
* `door_locked` - Locked door.
* `gem` - A gem.
* `heart` - A heart.
* `key` - A key.
* `moving_platform` - A moving platform.
* `portal` - A portal.
* `saw` - Saw Hazard object.
* `switch` - Switch.
* `thorns` - Thorn hazards.
* `tiles_bricks` - Brick tiles.
* `tile_grass` - Grass tiles.
* `tile_placeholder` - Placeholder tiles.
* `tile_sand` - Sand tiles.

## Backgrounds

* `background_colored_desert`
* `background_colored_forest`
* `background_colored_trees`
* `background_colored_tall_trees`
* `desert_background`

## Entry points

* `ready` - When an object is loading.
* `collides` - Collision happened. It contains data about the colliding object type and object ID - for instance type `block` or `door_locked` or `game_console_character`.
* `update_loop` - Runs for each object on each frame.
* `broadcast` - Used to process a message broadcast from another object.

### Broadcast entrypoint expression entries

* `broadcast_message.message_id` - message_id sent from the source broadcaster.
* `broadcast_message.message` - computed message sent from the source broadcaster.

### Collision entrypoint expression entries

* `body.type` - can be one of `alien`, `coin`, `star`, `big_block`, `small_block`, `tile`
* `body.object_id` - `object_id` of the colliding body.
* `body.is_on_floor` - is only available for the `alien` object. This is the status on wether the alien is on the `tile`

**Note:** If you need to access these values over a large sequence of code blocks, try to immediately store these values into dedicated Object or Global variables. This avoids situations where somewhere down the line the values of these change due to collisions registered elsewhere.

## Behaviors

* By default the `game_console_character` moves left or right by pressing the left or right keys, and jumps when pressing the space key.

## Custom properties

### `block`

* `mass` - Block's mass.
* `is_active` - Is active or not active.
* `color` - Color of the block.

### `game_console_character` / `boy` / `girl` / `soldier`

* `is_current` - is the current active player (the one currently being controlled).
* `jump_force` - force of the character's jump.
* `speed` - Movement speed.
* `push_force` - Force with which the character can push objects such as `block` on the stage.

### `locked_door`

* `is_active` - Is active or not active.
* `color` - Color of the door.

### `door_open`

* `is_active` - Is active or not active.
* `color` - Color of the door.

### `moving_platform`

* `is_active` - Is active or not active.
* `horizontal_start_position` - left or right.
* `vertical_start_position` - top or bottom.
* `vertical_distance` - How much distance it moves vertically.
* `horizontal_distance` - How much distance it moves horizontally.
* `move_horizontally` - Should it move horizontally?
* `move_vertically` - Should it move vertically?
* `movement_duration` - Duration of movement in one direction (in seconds).
* `width` - Width of the moving platform

### `portal`

* `is_active` - Is active or not active.
* `color` - Color of the portal.

### `saw`

* `is_active` - Is active or not active.
* `rotation_speed` - Rotation speed in rotations per second.

### `switch`

* `is_active` - Is active or not active.
* `is_pressed` - Pressed or not pressed.
* `color` - Color of the switch.

### `thorns`

* `is_active` - Is active or not active.

### `gem`

* `is_active` - Is active or not active.
* `color` - Color of the gem.

### `heart`

* `is_active` - Is active or not active.

### `key`

* `is_active` - Is active or not active.
* `color` - Color of the key.

### All the different types of tiles: `tiles_bricks` , `tile_grass` , `tile_placeholder` , `tile_sand`

* `width` - Tile width in number of tiles.
* `height` - Tile height in number of tiles.
* `platform_kind` - Sand or Concrete tile.
* `is_active` - Is active or not active.

### Working with the color property in expressions

You can work with the color property in the following fashion in the expressions (for example to reference the color Red): `properties.color == color_red`

All colors include: `color_red`, `color_green`, `color_blue`, `color_yellow`.

## Custom functions

### `block`

* `destroy`
* `central_impulse` - Apply an impulse force in x and y axis.
* `central_force` - Apply a constant central force in x and y axis.

### `game_console_character` / `boy` / `girl` / `soldier`

* `die`

### `gem`

* `destroy`

### `heart`

* `destroy`

### `key`

* `destroy`

### `locked_door`

* `destroy`

### `door_open`

* `destroy`

### `portal`

* `destroy`

### `saw`

* `destroy`

### `switch`

* `destroy`
* `set_pressed` (This custom function sets the switch to pressed or not pressed and updates its `is_pressed` property)

### `thorns`

* `destroy`