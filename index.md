## Blender to ML64 Equipment Pack Tutorial

From Blender to an OoTO 3.x.x Equipment Pak

This tutorial aims to walk you through the process of importing a custom equipment model from Blender to OoTO's costume manager.

If the images seem too small, feel free to check out this tutorial on [GitHub](https://github.com/Neirn/equipment_pak_tut/blob/gh-pages/index.md), or just open the image in a new tab.

### Needed software:
[Blender](https://www.blender.org/)  
[zzconvert](http://www.z64.me/tools/zzconvert)/[z64convert](http://www.z64.me/tools/z64convert)  
[My Equipment Tester](https://github.com/Neirn/equipment_tester/releases/latest)  
[A ModLoader-compatible Equipment Template](https://github.com/Neirn/z64o_equipment_template)  

## Blender

This will be written under the assumption that you are already familliar with the zzconvert/z64convert pipeline and the associated Blender plugins. If you have no idea what any of that means, check the pins in the #model-dev channel in the [ModLoader64 discord server](https://discord.gg/nHb4fXX).

For this tutorial, we will use the old pipeline (zzconvert), but the process should be fairly similar for the new pipeline.

In Blender, position, name, rotate, etc. your weapon like you would with any regular playas. So, if I was replacing the Master Sword, for example, I would need my equipment meshes named `Hilt.2` and `Blade.2`. I recommend that you use one of the Link Blender templates as a reference, but that isn't *technically* required. So, you *could* just export an existing custom piece of equipment from an existing playas .blend if you really wanted to.

Anyway, for consistency, we have positioned our model on the template. For this tutorial, we will replace the Kokiri Sword, but the process is more or less the same to replace the other equipment.

![Blender Displaying Just Link and Four Sword](https://github.com/Neirn/equipment_pak_tut/raw/main/img/blender_example1.png)

As can be seen in this picture, my custom sword is already in position, appropriately named `Hilt.1` and `Blade.1`, and is rigged to the skeleton.

So, what we're going to want to do is select ONLY the skeleton and the equipment we will replace (if you have multiple pieces of equipment in the .blend, EXPORT EACH SEPARATELY).

![Blender Displaying Selection of Just Skeleton and Sword](https://github.com/Neirn/equipment_pak_tut/raw/main/img/blender_selection.png)

To make things easier to see, I hid everything except for the sword and skeleton. As you can see, they are the only things selected in the scene, with the skeleton as the active selection (i.e. select the skeleton last like you would for a normal playas).

![Blender_Objex_export_UI](https://github.com/Neirn/equipment_pak_tut/raw/main/img/blender_objex_export_ui.png)

## ZOBJ Conversion

Next, you're going to want to export with the objex plugin. We are going to make one very important change to the settings. You see that box in the sidebar that says "Selection Only"? Check it.

![Blender Objex Selection Only Checkbox](https://github.com/Neirn/equipment_pak_tut/raw/main/img/blender_selection_only.PNG)

Then, continue to export like you would any other playas. It shouldn't be a very large file. If it is (i.e. >50 KB or so), make sure you ONLY selected the equipment and skeleton and ensure that you checked "Selection Only."

![Small file example](https://github.com/Neirn/equipment_pak_tut/raw/main/img/explorer_small_file.png)

Now, open up your copy of z\*convert and use the same options that you would use if you were making a regular playas. These are my settings for example.

![zzconvert export options](https://github.com/Neirn/equipment_pak_tut/raw/main/img/zzconvert_export_options.png)

After converting your objex to a zobj, as one last sanity check, look at the output window. The only display lists you should see are the ones for your custom equipment as well as one for the limb they're attached to.

![zzconvert_output](https://github.com/Neirn/equipment_pak_tut/raw/main/img/zzconvert_output.png)

If everything looks good and your zobj seems to be a reasonable size, then we can move on to injecting the model.

## Testing and Pak Conversion

Open up ML64 with the equipment tester and OoTO enabled. Go ahead and open a save file that has the equipment you're replacing.

Once in-game, open up the equipment tester from the Mods section of the main menu bar. In the path box, put a path to the zobj you created with z\*convert earlier and load it.

![Show_four_sword_equipped](https://github.com/Neirn/equipment_pak_tut/raw/main/img/ml64_equipped.png)

Look! It's our weapon! If nothing happens, check the console log for errors.

If the weapon loads but isn't in the right position, move it around in Blender and re-export until it looks right.

Once you're happy with the model, give it a(n) (optional) name (size limit: <32 characters), and select the appropriate category for it. Then, hit the "save equipment zobj" button and check your ModLoader folder for the zobj. It will either have the name you entered or the same name as the zzconvert zobj if you didn't choose a name.

![final_equipment_tester](https://github.com/Neirn/equipment_pak_tut/raw/main/img/equipment_zobj_loader_ui.png)

![final_zobj_windows_explorer](https://github.com/Neirn/equipment_pak_tut/raw/main/img/explorer_final_zobj.png)

Then, you can slap the zobj the plugin generated into the equipment pak template, update said template to suit your needs, and enable it like any other ModLoader mod. It should now work in the costume manager!

![Costume_manager_demo](https://github.com/Neirn/equipment_pak_tut/raw/main/img/ml64_costume_manager_final.png)
