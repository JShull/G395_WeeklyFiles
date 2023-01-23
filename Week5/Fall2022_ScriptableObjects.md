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