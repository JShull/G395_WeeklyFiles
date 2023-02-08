# GitHub Projects, Scriptable Objects, & Prefabs

The past two weeks of class and the current week of class are dealing with a lot of administration and project setup work for your initial high stake deliverable. To recap last week we will be quickly going back through GitHub projects/issues and where the files are for your first large high stake deliverable. The rest of the video and material is what we are missing due to the inclement weather and my work travels. Majority of the video will be about how Unity works with different data types - when to use them, why to use them, and then ultimately what you want to utilize them for covering Scriptable Objects and Unity Prefabs.

## Scriptable Objects Concepts

Unity has a way to generate data/information and store it that it can be used during the editor and at runtime to do a lot of work for you. In most cases [Scriptable objects](https://learn.unity.com/tutorial/introduction-to-scriptable-objects) are best used for helping maybe manage player/level settings, or staging an environment, and/or loading in some asset in which you want to populate that asset with some pre-configured data. Think that you have a prefab and you want to initialize a lot of them and then when they are spawned you want them to pull from a data file to do something even else: scriptable objects and prefabs combined can be very powerful. In most cases you're using a scriptable object from the editor to save some sort of 'state' or data of something that you then plan on loading during runtime. You wouldn't want to use Scriptable Objects to save to while at runtime - this is something you cannot do and there are better alternatives to do this. Generally this is a way to quickly optimize information/data within Unity to populate some other asset/component.

### OnEnable and OnDisable

Generally you want to load/unload scriptable object data via another component/script and you generally want to do this using Unity's [OnEnable](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnEnable.html) and [OnDisable](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnDisable.html) method calls. This provides a quick and clean way to make sure your Unity object has the information it needs and/or should be populating from.

### Creating Asset Menus

You can use Unity's Create Asset Menu to automatically have your scriptable object appear in the asset menu - when you right click and say 'Create' you can use the attributes within your scriptable object to allow then Unity to provide an in Editor menu option for creation.

## Live Unity

### Custom Unity Packages, URP, & Scriptable Objects

* Unity Custom Package Setup
  * GIT Custom Packages require full [Git install](https://git-scm.com/downloads)
    * Lab machines already have this installed - other personal machines even if you installed GitHub you also need core Git.
  * Open your existing Unity Project that we've been playing around with - last week we were using it with Inputs.
    * First off let's make sure everyone has a *.gitignore file! (if you don't) copy it from the Week3 Unity Project Folder in your repository.
      * ![Gitignore Copy](/images/CopyGitIgnore.PNG)
      * Go find your project folder and look at the root of your Unity project... look for '*.gitignore' if you don't see it paste that copied gitignore file in here.
      * ![GitIgnore Location in Unity](/images/GitIgnoreFileLocation.PNG)
    * Now back to Unity/Open up Unity and go to the Package Manager-->Plus Icon--> Git URL
    * Paste the link below into the Git URL field
    * >https://github.com/jshull/FP_Control.git
      * ![Git URL Unity Editor](/images/PackageManager_Control.PNG)
    * Install the samples
      * ![Git Samples Control](/images//PackageManager_ControlSamples.PNG)
    * Install Unity Universal Render Pipeline (URP) package and the samples after it finishes installing
      * ![URP](/images/URPPipeline.PNG)
      * ![URP Samples](/images/URPSamples.PNG)
    * URP Settings: Project Settings-->Graphics-->Modify the Render Pipeline Asset (you are using samples you imported here)
      * Unity will prompt you to make sure you want to do this- yes you want to do this.
      * ![URP Settings](/images/URPSettings.PNG)
      * Select one that Unity provided in the samples: e.g. "SamplesPipelineAsset" or "BlobShadowPipeline'
        * ![URP Blob](/images/URPBlob.PNG)

#### Scriptable Objects

Let's open my example control scene and talk about scriptable objects.

* ![John Control Sample](/images/ControlScene.PNG)
* Hit play and use the AWSD/Mouse/Space bar to interact
* Checkout the Hierarchy and look for the 'Controller' GameObject
  * ![Controller Scriptable Object](/images/Control_SO.PNG)
  * Let's look at the variable named 'Player Control Data' which we see is called 'Sample_ControlParameters (SO_Control Parameters)' double click that to navigate to it's location
    * ![Controller SO Data](/images/Control_SO_2.PNG)
  * Let's make a new one and assign it to our controller
  * ![Control Create 1](/images/Control_SO_3_Create.PNG)
  * ![Control Create 2](/images/Control_SO_4_Create.PNG)
  * ![Control Create 3](/images/Control_SO_5_Create.PNG)
  * ![Control Create 4](/images/Control_SO_6.PNG)

This is showcasing a workflow in which you have custom unity packages that utilize data oriented design practices by storing variable data within a scriptable object. We then use that package to generate/create our own data parameter file and apply it to our controller interface. In class I will spend a few minutes showcasing how you can make your own scriptable objects, get them to show up in the unity editor, and then use them to change the color of something.

### Unity 2D Game Kit Projects

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
