# Further Unreal Engine Help

## Creating the Level

Give your level a name and chose 1 of 2 options. For this I will pick "Create with Starter Map" to get started on a level that already has some useful content.

![](./images/1.png)

Double click your level to open it. This new folder is also where you should store any content specific to this render inside. Think of these folders like each of them are a .blend file if you come from blender experience.
The generated folders also include the current Fortnite version in the title, this is because content can get removed and added back between updates and it is good to keep track of when you created a level.

![](./images/2.png)

## Setting up the Level Sequence Part 1

Level Sequences are super important, they are how you will pose characters, work with Niagara Systems, and eventually render out your final image!
Create one for your new level using the first Level Sequence related button

## Setting up our Character

Now that the Level Sequence is created and opened, lets set up our character. Search for the skin you want by Display Name or by Item Definition, and with a mannequin actor selected in the viewport simply click the search result to apply it.

_Note that searches will cause UEFN to freeze for a moment, this is normal. The engine is just loading Data Assets in the background to display_

![](./images/3.png)

The skin I selected has effects that I want to enable, to do that you can tick Spawn FX in the Details tab.

![](./images/4.png)

Your skin may also have edit styles that you want to change, and you can do that as well by scrolling further down!

![](./images/5.png)

## Posing the Character

Press the second Level Sequence related button with your character selected to add them to the sequence and give them 2 Control Rigs automatically! One for the body and one for the face. You can now pose (or even animate) the character just like you would in Blender.

Note that the Level Sequence is where your poses will be stored, not the level itself. If you open your level without the Sequence also being open you will see your characters in the default A-pose!

![](./images/6.png)

I went ahead and also set up the camera to be how I wanted. Wont get into that because of course I cant teach everything about Unreal in one go...

![](./images/7.png)

## Settings_World
This is a Blueprint I set up to help with creating quick character renders. It mimicks some Blender World stuff in its settings. It also has some lighting setups pre made! Also feel free to not use this of course, get creative.

For this, Im going to keep the lighting and just set the background to transparent

![](./images/8.png)

## Setting up the Level Sequence Part 2

Drag your camera for the render into the Level Sequence window from the Outliner

![](./images/9.png)

Follow the flow of these dropdowns to get to this setting, and change time to display as Frames. This will be useful for our next step!

![](./images/10.png)

Go 1 frame in (or a few more than that if youd like) on your Level Sequence and right click the red pointer to set your end time. For still renders this will represent how many times its rendered. There are few scenarios where more than 1 might be needed.

![](./images/11.png)

## Rendering

Press this button on the Level Sequence window to open the Movie Render Queue

![](./images/12.png)

You can now configure any settings you need to here, though for most cases all you should touch is the Output section

![](./images/13.png)

Unreal should (hopefully without issue) do its job and begin to render your image. This has 2 phases
- Warm up (Letting physics, effects, etc set in)
- Rendering your actual frames

![](./images/14.png)

## Done!

You now have your finished render!

![](./images/15.png)

This was only just a basic overview of what you can do with UEFN, but there is so, so much more. I can only teach so much before I have to just encourage looking things up and learning that way. Unreal is complicated and takes time to learn.

_Example of a Level Sequence with much more going on, a full custom scene in this render too!_
![](./images/16.png)

Before moving into a general guide with UEFN and some tips, feel free to check out my art [here on my website](https://vnova.dev/gallery).

## General UEFN Rules: How to NOT crash!
Patched UEFN can be unstable at times.. the following is a list of actions that __WILL CRASH__ the editor instantly. Please save your work often and avoid these!
- Opening _some_ cooked assets (notably Niagara, something an artist probably would attempt to peek at)
- Having AnimAssets directed at the player load. This means in the Content Browser, editor dropdowns, and most importantly __in the Sequencer, characters will have an "Animation" dropdown.. DO NOT HOVER OVER IT!__ Please move your cursor __around__ it when using the menu.
- Loading the original __Roxas__ outfit will crash, more specifically once his Body Character Part due to using a bad asset. Please make sure Character_FaunaPike_Patched is being used in place of Character_FaunaPike
- Copying __Volume__ type Actors inside of __cooked Levels__ will crash. If you would like to copy Actors outside of a level please search "Volume", delete them, then copy all the actors. I dont think any other Actor types cause this.
- Do not accidentally try to __save/apply changes__ to a cooked asset such as a __cooked Material__ or a __cooked Material Instance__. Not that this would do anything useful.. but dont accidentally do it.
- Dont __undo edits__ done to a __cooked Material__ or __cooked Material Instance__. I dont know if this crashes 100% of the time, but it has happened before. Be cautious if touching these asset types.


## Tips!
You can pose individual skeletal meshes of a skin by adding them to the sequencer, giving it a FKControlRig, and setting it to Layered! Very useful for taking control of physics parts of skins.

![](./images/t1.png)

A Sim Cache can be created to record and freeze Niagara FX to get them perfect for your render. I cant explain it all here but I suggest looking into it!

![](./images/t2.png)

You can find TODM/DSA settings in the World Settings tab. Please use these instead of the Time of Day dropdown added at the top of the viewport by using a DSA, those settings wont save to the level but these will.

![](./images/t3.png)

Fortnite boosts the brightness on the lighting for better game performance. Press Perspective and turn off Game Settings and this will result in a more Natural lighting such as darker nights and so on. Really good overall. Wouldn't recommend on OG/CH1,CH2 Or CH3 as their lighting plays into the brightness!
