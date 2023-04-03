# 2D Rigging

Using the updated 2D Sprite tools we can do a lot of rigging in Unity. This won't get into the sprite importing/photoshop approach but there's plenty of content out there on how you can setup your sprite in a sprite sheet to allow to use the PSD pivot points upon bringing that file into Unity.

## Unity Package Requirements

Ideally you should already have the other 2D packages in because you should have started with a 2D Core URP setup.

2D Packages Required
![Image of 2D Packages](../images/2DAnimation_00.PNG)

* com.unity.2d.animation: 9.0.2
  * 2D Animation now includes the IK tools/packages that are no longer in preview
* com.unity.2d.psdimporter: 8.0.2
  * 2D PSD Importer required to use the Unity samples
* com.unity.2d.spriteshape: 9.0.2
  * 2D SpriteShape good to have for other things.

## Unity Rigging Steps

This is assuming you already have a 2D PSD setup sprite. If not - please use the one Unity provides in their 2D samples for the 2D Animation 9.0.2 for the (3) Character 'Fei'. Unity already has this fully setup for you but for our intentions we are going to make a copy of the PSD removing all of the pre-built Unity content.

At this point we can start the process.

### 2D Rigging Flow

* Sprite Adjustments
  * Select your PSD file and hit the 'Open Sprite Editor'
  ![Image of SPrite Editor](../images/2DAnimation_01.png)
  * Default Sprite Editor
  ![Image Default Sprite Editor](../images/2DAnimation_02.png)
* Skinning Editing & Creating Bones
![Image of 2D Skinning Option](../images/2DAnimation_03.png)
* Start Adding some Bones
  * Always start with our center/navel/hip area and work our way out and up to the head
  * Right click will stop the editing process and you can now go back and start to create hips/shoulders from the other root bones.
  ![Image of 2D bones](../images/2DAnimation_04_bones.png)
  * After creating the basic limb bones
  ![Image of 2D bones with limbs](../images/2DAnimation_05_bones.png)
* Geometry Generation
  * We need to assign the sprite geometry to our bones, we first use the auto geometry tool
  ![Image of Geometry Auto](../images/2DAnimation_06_geometry.png)
  * After clicking Generate for all Visible we should see this fun color chart now by bone weight (we will need to tweak this)
  ![Image of Geometry Auto](../images/2DAnimation_07_geometry.png)
  * Bone Influence
    * Auto generation doesn't always fully work and you should always tweak and adjust, we are going to go through each of the major sprites here for our current Unity Fei character, there are more sprites than we are going to rig as we are just focusing in on the core system.
  * Click on Bone Influence and then double click the head sprite - we are going to adjust the bones now
  ![Image of Bone Influence](../images/2DAnimation_08_boneInfluence.png)
  * As long as the head is being impacted by just the top bones we should be good
  ![Image of Bone Influence bones](../images/2DAnimation_09_boneInfluence.png)
  * Lets look at the body
  ![Image of Bone Influence body bones](../images/2DAnimation_10_boneInfluence.png)
  * We need to remove all of these other bones that are impacting the body
  ![Image of Bone Influence body bones](../images/2DAnimation_11_boneInfluence.png)
  * Check the rest of the major sprites to make sure we are good here
  * I had to adjust the piece of hair to make sure the neck bone was influencing it.
  * We can now hit Preview Pose and check our system.
  ![Image of Bone Influence body bones](../images/2DAnimation_12_boneInfluence.png)
