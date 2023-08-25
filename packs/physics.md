# Physics Pack Documentation

## Objects

* `alien` - Alien character
* `coin`
* `destination` - Stage destination door
* `explosive` - Can apply sudden impulse when in contact with `alien`
* `big_block` - called Large Block in the object list
* `small_block`
* `star`
* `desert_background` - serves only as a background for the game
* `tile` - Floor tile

## Entry points

* `ready` - When an object is loading.
* `collides` - When a `star`, `coin`, `alien`, `large_block` or `small_block` collides with another object.
* `update_loop` - Runs for each object on each frame.
* `broadcast` - Used to process a message broadcast from another object.

### Broadcast entrypoint expression entries

* `broadcast_message.message_id` - message_id sent from the source broadcaster.
* `broadcast_message.message` - computed message sent from the source broadcaster.

### Collision entrypoint expression entries

* `body.type` - can be one of `alien`, `coin`, `star`, `big_block`, `small_block`, `tile`
* `body.is_on_floor` - is only available for the `alien` object. This is the status on wether the alien is on the `tile`

**Note:** If you need to execute this over a sequence of code blocks, try to immediately store these values into dedicated Object or Global variables. This avoids situations where somewhere down the line the values of these change due to collisions registered elsewhere.

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