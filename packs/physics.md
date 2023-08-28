# Physics Pack Documentation

## Objects

* `alien` - Alien character
* `coin`
* `destination` - Stage destination door
* `explosive` - Can apply sudden impulse when in contact with `alien`
* `big_block` - called Large Block in the object list
* `small_block`
* `star`
* `tile` - Floor tile
* `star_counter` - A visual counter for stars. More details on how to use it in the coming sections

## Backgrounds

* `background_colored_desert`
* `background_colored_forest`
* `background_colored_trees`
* `background_colored_tall_trees`
* `desert_background`

## Entry points

* `ready` - When an object is loading.
* `collides` - When a `star`, `coin`, `alien`, `large_block` or `small_block` collides with another object. It contains data about the colliding object type and object ID.
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

## Custom properties

* `tile` object will have the `num_blocks` custom property - which denotes the width of the tile block. So that you don't have to repeat it tile after tile horizontally.
* `explosive` object has the `explosion_force` custom property - which denotes how much its explosive force is when encountering the `alien` object.
* `alien`, `big_block` and `small_block` objects have the `mass` custom property - denoting the mass of the object.
* `destination` object has the `destination_scene` property which denotes the scene name it should automatically transition to should the alien encounter it.

## Custom functions

### Alien

* `central_impluse` - impulse that is applied on the object from its center point.
* `central_force` - constant force that is applied on the object from its center point.

### Coin and Star

* `destroy` - Destroys the object

## Star Counter Object

The star counter is a visual element that shows how many stars have been collected. To make use of it, you need to broadcast the following message:

* `message_id` : `increment_num_stars`
* `message` : Should contain the number of stars for which to increment with.

### Star counter functions

* `set_num_stars` - Sets the number of stars on the counter

### Star counter object variables

* `num_stars` - Number of stars it contains. Do not update this value manually, just use it for reading of the value
