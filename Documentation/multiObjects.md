
# How to work with multiple walls (WIP)

One perk of Slice-Up is that it can generate a continuous tool-path for multiple walls.

> **NOTE:** from now on I will refer to multiple walls object as `multiObject`, while we will call each wall  a `loop`

In this tutorial I will show a bit of the general work-flow of working with multiple walls. Specifically, I am going to detail:

- How to create `multiObjects`
- How to modify `multiObjects`

In order to simplify visualization, in the examples I will use a layer height of 10mm.
Here are the example files we will use:

[add image of primitvie + wave + rotated]


### Creating multiObjects
Multi objects are created using the `Offset` module.

> **NOTE:** you can add up to three offset loops to your original wall, which means that you can create objects with up to 4 walls.

>**NOTE:** All loops will be automatically sorted outside in, so you don’t need to worry about the order when using multiple loop.

General offset rules: 
- Negative values offset to the outside
- Positive values offset to the inside
- For `loops` you can either set an independent distance, or repeat the first `loop` offset. 

Let's see an example:

[insert 1st example image]

First we set a `offset distance` equal to the extrusion width for the first `loop`. This will create a thicker wall.

[insert example image]

Next, we set a negative value to the second `loop`, so to make our object wider.

[insert example image]

Finally, we duplicate the first offset on the third `loop` so to also make the outer wall thicker.



Offset and Wave
WARNING: although you can import waved object, be aware that the wave offset is a ‘loose’ offset, meaning that it does not guarantee to strictly respect the offset distance at all points in the path. This can be more or less of a problem depending on your object and/or technology, so plan accordingly.

Let’s see what happens when  you import a waved object in the offset module:

As before, the first option is two simply offset the wave. This can be used in order to double the wall, or to replicate the same shape in a different location.
You can toggle the primary copy on to force the offset to use the original curve that underlay the wave structure. 

This opens up a world of possibilities of what you can do with your toolpath.

In this example, we use the primitive copy on the inner offset, so as to have a wave pattern on the outside, but a smooth finish inside (as it may be desirable for a coffee mug).
In the following example, we offset the primitive curve to both sides while maintaining the structure to the inside. For example it could be the case of a insulated wall or some kind of wheel that require different gradient of support

This should have toggled a little lightbulb in your head, and with a bit of creativity a planning you can come out with a hundred different interesting scenario for multiple walls application.

Further modifying multi-objects
Once you created a multi-object you can export it and continue to work on it as needed.

WARNING: the offset module, the combine module, and the spiral module will not accept a multi object upon input. If you do, you will get an error upon import.

When importing a multiple wall object, you can only work on one ‘loop’ at the time. You can select the desired loop in the I/O tab. Make sure to toggle ‘show input’ in the Display tab to see all the loops as a reference (white)
When exporting, you will export the whole object, replacing only the loop that you worked on

TIP: you can quickly modify different loops by exporting / re-importing, switching loop each time.
In this example we use this method to quickly apply the same pattern through the external loops, and a different one in the middle.


The same logic applies when using transformations.

In this example we scale our toolpath so that the loops meet each other at top and bottom.

WARNING: Applying rotation to a single loop causes a mismatch between the seams of the rotated loop, and the other loops. For this reason, it is recommended to apply the rotation before applying the transformation creating the offset, so that the seam will remain aligned.

Building a base
Building a base for multiple walls is no different. When you import multi-objects in the wave modules, the outer loop will be automatically selected as your base boundary.

This concludes the technical aspect of this tutorial, in the next
