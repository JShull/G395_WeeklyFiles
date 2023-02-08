# GitHub Projects, Scriptable Objects, Prefabs, and Saving Data

The past two weeks of class and the current week of class are dealing with a lot of administration and project setup work for your initial high stake deliverable. To recap last week we will be quickly going back through GitHub projects/issues and where the files are for your first large high stake deliverable. The rest of the video and material is what we are missing due to the inclement weather and my work travels. Majority of the video will be about how Unity works with different data types - when to use them, why to use them, and then ultimately what you want to utilize them for covering Scriptable Objects and Unity Prefabs.

## Scriptable Objects

Unity has a way to generate data/information and store it that it can be used during the editor and at runtime to do a lot of work for you. In most cases Scriptable objects are best used for helping maybe manage player/level settings, or staging an environment, and/or loading in some asset in which you want to populate that asset with some pre-configured data. In most cases you're using a scriptable object from the editor to save some sort of 'state' or data of something that you then plan on loading during runtime. You wouldn't want to use Scriptable Objects to save to while at runtime - this is something you cannot do and there are better alternatives to do this. Generally this is a way to quickly optimize information/data within Unity to populate some other asset/component.

### OnEnable and OnDisable

Generally you want to load/unload scriptable object data via another component/script and you generally want to do this using Unity's [OnEnable](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnEnable.html) and [OnDisable](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnDisable.html) method calls. This provides a quick and clean way to make sure your Unity object has the information it needs and/or should be populating from.

### Creating Asset Menus

You can use Unity's Create Asset Menu to automatically have your scriptable object appear in the asset menu - when you right click and say 'Create' you can use the attributes within your scriptable object to allow then Unity to provide an in Editor menu option for creation.

## Prefabs and Prefab Variants

Prefabs and Prefab variants are incredibly powerful tools in which everyone in this class should understand and utilize for their projects.

## Live Unity

* GitHub Projects
* 2D Game Kit Setup
  * New Project
  * [Add/Import 2D Game Kit](https://assetstore.unity.com/packages/templates/tutorials/2d-game-kit-107098)
  * ![Find 2D Game Kit in your Package Manager](/images/2DGameKitPackage.png)
  * **2D Game Kit Error 1**
    * What's going on here?
      > *"Assets\2DGamekit\Utilities\Editor\RuleTileEditor.cs(231,24): error CS0433: The type 'RuleTile' exists in both 'Assembly-CSharp, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' and 'Unity.2D.Tilemap.Extras, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'"*
    * ![Importing Game Kit](/images/2DGameKit_Error.png)
    * Most of you would have started with the 2D Core Template which includes an updated newer version of a Tilemap system that when the original 2D game kit was created... didn't exist. This error is telling us that with three words: *'exists in both'* which immediately means we have two of these scripts in our project and Unity cannot figure out which one to reference/use.
    * Two Options:
      * Remove the entire package *'Unity.2D.Tilemap.Extras'*
      * Remove the one script *'RuleTileEditor'* located in *'Assets\2DGamekit\Utilities\Editor'* that we imported with the kit.
  * **2D Game Kit Error 2**
    * What's going on here?
      > *"CinemachineExtension requires a Cinemachine Virtual Camera component"*
      >
      > *"UnityException: Virtual Camera was not found, default follow cannot be assigned"*
    * ![Cinemachine Error](/images/2DGameKitCInemachineBug.png)
    * On this surface this looks like two problems... but is it?
      * No: One error cascades into the second one, always start with the first error: initially as most of you aren't that experienced in Unity, when you see a lot of errors there's always a high probability that they might be associated.
      * To fix this error we have to open up **Zone2** and make some modifications to a component
      * ![Cinemachine Component Double](/images/2DGameKitCinemachine_DoubleComponent.png)
        * Unity forgot to update their prefab and/or they didn't clean up their other component!
        * You also need to update this in the other scenes with the same camera loading setup: **'Zone3'** & **'Zone4'**
* 2D RPG Game Kit Setup
  * Worked like a charm - just add the [RPG asset](https://assetstore.unity.com/packages/templates/tutorials/creator-kit-rpg-149309) to your store and open it in package manager!
  * ![2D RPG Import](/images/2DRPGInstal.png)
* Time permitting: John's Custom Packages
  * GIT Custom Packages require full [Git install](https://git-scm.com/downloads)