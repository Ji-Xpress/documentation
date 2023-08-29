# Platformer Pack Documentation

## Objects

* `block` - Physical Block (Movable)
* `character_game_console` - Player character - game console
* `door_open` - Open door
* `door_locked` - Locked door
* `gem` - A gem
* `heart` - A heart
* `key` - A key
* `moving_platform` - A moving platform
* `portal` - A portal
* `saw` - Saw Hazard object
* `switch` - Switch
* `thorns` - Thorn hazards
* `tiles_bricks` - Brick tiles
* `tile_grass` - Grass tiles
* `tile_placeholder` - Placeholder tiles
* `tile_sand` - Sand tiles

## Backgrounds

* `background_colored_desert`
* `background_colored_forest`
* `background_colored_trees`
* `background_colored_tall_trees`
* `desert_background`

## Entry points

* `ready` - When an object is loading.
* `collides` - Collision happened. It contains data about the colliding object type and object ID - for instance type `block` or `door_locked` or `character_game_console`.
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

* By default the `character_game_console` moves left or right by pressing the left or right keys, and jumps when pressing the space key.

## Custom properties

**Note:** Some properties may be unavailable and under development.

### `block`

* `mass` - Block's mass.
* `is_active` - Is active or not active.
* `color` - Color of the block.

### `character_game_console`

* `is_current` - is the current active player (the one currently being controlled).
* `jump_force` - force of the character's jump.
* `speed` - Movement speed.

### `locked_door`

* `is_active` - Is active or not active.

### `door_open`

* `is_active` - Is active or not active.

### `moving_platform`

* `is_active` - Is active or not active.
* `horizontal_start_position` - left or right.
* `vertical_start_position` - top or bottom.
* `vertical_distance` - How much distance it moves vertically.
* `horizontal_distance` - How much distance it moves horizontally.
* `move_horizontally` - Should it move horizontally?
* `move_vertically` - Should it move vertically?
* `movement_duration` - Duration of movement in one direction (in seconds).

### `portal`

* `is_active` - Is active or not active.

### `saw`

* `is_active` - Is active or not active.
* `rotation_speed` - Rotation speed in rotations per second.

### `thorns`

* `is_active` - Is active or not active.

### `gem`

* `is_active` - Is active or not active.

### `heart`

* `is_active` - Is active or not active.

### `key`

* `is_active` - Is active or not active.

### All the different types of tiles: `tiles_bricks` , `tile_grass` , `tile_placeholder` , `tile_sand`

* `width` - Tile width in number of tiles.
* `height` - Tile height in number of tiles.
* `platform_kind` - Sand or Concrete tile.
* `is_active` - Is active or not active.

## Custom functions

### `block`

* `destroy`
* `central_impulse` - Apply an impulse force in x and y axis
* `central_force` - Apply a constant central force in x and y axis

### `character_game_console`

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

### `thorns`

* `destroy`