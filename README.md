# Unity Heightmap Baker
A small Blendfile that enables you to bake .raw terrain heightmaps for unity.

Youtube Link: https://youtu.be/53KAZO0cimw

Disclaimer: This is neither a fully developed Blender Addon, nor a very clean solution. But it seems to work and it is fast. So i hope it will assist you in your terrain creation process.

## Usage

To use the baker open the blendfile. After that you may put anything inside the Baking Volume. Everything that is outside of it will not be included in the heightmap. By default it contains a plane with a multires modifier, that is ready for sculpting and a monkey mesh for demonstration purposes. After creating your terrain simply press the "Run Script" Button on the bottom right. Blender will most likely freeze for a couple of seconds and a file called "Heightmap.raw" will appear in the folder that contains your blendfile.

In unity import the .raw image, and set the following values:
- Depth: 16bit
- Width/Height: like set in Blender (1025 by default) Must be power of two plus one!
- Byte Order: Windows
- Flip vertically: false
- Terrain Size: By deafult the "Y" axis should be half as big as "X" and "Z"

## Modification

Here are some modifications you may make to adjust the blendfile to your needs:

To adjust the resolution of the heightmap, just change the resolution in your scene renderer settings in Blender. Be aware that unity requires the resolution to be a power of two plus one.

To change the filepath or name of the output open the python script and change the corresponding String in line 8.

To change the height of your baking volume move the camera up by that amount, go to the world settings -> Mist Pass and add your heightchange to the "Depth" value. You may also change the BakingVolume mesh, but it is more of a reminder than a necessity. Also take the heightchange into consideration when importing to unity.

If you dont want to bake it, but use an image, you can also comment out the rendering line in the script (line 14) and plug your own image into the viewer node. The script will interpret the red channel of the image as your height.

You can also use your GPU to render the image, but i experienced some weird bugs when doing that, so it is set to CPU by deafult. But just try it out.
