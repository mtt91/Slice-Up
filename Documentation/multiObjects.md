
# How to work with multiple walls (WIP)

# How to work with multiple walls

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

First we set a `offset distance` equal to the extrusion width for the `first loop`. This will create a thicker wall.

[insert example image]

Next, we set a negative value to the `second loop`, so to make our object wider.

[insert example image]

Finally, we duplicate the first offset on the  `third loop` so to also make the outer wall thicker.

### Offset and Waves

>**WARNING:** wave offset is a `loose offset`. It does not strictly respect the offset distance at all points in the path. This can be more or less of a problem depending on your design and/or print technology, so plan accordingly.

When importing `waves` in the offset module you can choose to force it to use `primary curves`.

Let's consider the some examples:

[insert relevant image]

Here we force the offset to a `primary copy` in order to obtain a smooth finish on the inside while having a wave structure on the outside.

[insert relevant image]

In this example, we offset the primitive curve to both sides while maintaining the structure to the inside. 

### Further modifying multi-objects
Once you created a `multiObject` you can export it and continue to work on it as usual.

>**NOTE:**  If you try to import a `multiObject` into the `Offset ` module, the `Combine` module or the `Spiral` module will not accept a multi object upon input. 

>**NOTE:** when modifying a `multiObject` you can only work on one `loop` at the time.

Upon import of a `multiObject`:
- Make sure to toggle `show input` in the `Display tab`. This will allow you to see all the `loops` as a reference.
- Select the desired `loop` in the `I/O tab`
- Exporting will export the entire `multiObject`, but it will replace the `loop` you just worked on.

>**TIP:** you can quickly modify different `loops` by exporting and  re-importing while switching `loops` in the process.

In this example we use this method to quickly apply the same pattern through the external loops, and a different one in the middle.


The same logic applies when using transformations.

In this example we scale our toolpath so that the loops meet each other at top and bottom.

WARNING: Applying rotation to a single loop causes a mismatch between the seams of the rotated loop, and the other loops. For this reason, it is recommended to apply the rotation before applying the transformation creating the offset, so that the seam will remain aligned.

Building a base
Building a base for multiple walls is no different. When you import multi-objects in the wave modules, the outer loop will be automatically selected as your base boundary.

This concludes the technical aspect of this tutorial, in the next
