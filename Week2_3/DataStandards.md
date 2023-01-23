# Data Standards and Serialization

This class is really dedicated towards identifying and understanding data standards and interoperability.

I'm going to approach this from going through real-time systems and then getting into just the basics of data formats and importantly how this all falls under *interoperability.*

## Real-time Systems

Going to breakout three classifications of real-time systems and use the work of some great authors/researchers. The below information is based on the work by Hermann Kopetz book, *'Real-Time Systems', 2011* and on the work by Andrew G. PSaltis in *'Streaming Data',2017*, you may also find other terms being used, ['Hard', 'Firm', and 'Soft'](https://en.wikipedia.org/wiki/Real-time_computing#Real-time_and_high-performance).

1. **Hard:** microseconds-milliseconds
  Think very strict time requirements and generally in embedded systems these are part of vital systems in which if time requirements fail we have a total failure of the system: spaceships, pacemaker, anti-lock brakes.
2. **Soft:** milliseconds-seconds
  Generally these systems can be thought of as social media companies, reservation systems, game chat services, etc.
3. **Near:** seconds-minutes
  Smart home devices, some iOT services, video streaming, etc.

I don't want to get in a back and forth on the differences between soft and near as they are very close together and as systems generally get better and as the internet gets faster these will more than likely combine under one concept.

So why do we care about real-time systems? Well in Unity there are multiple ways to get data, do you need it as fast as possible aka a user input from a controller and what sort of tolerances can our software anticipate in those cases and what ones can we *actually* control? This is why Unity and other game engines run multiple core loops within their engines to guarantee tolerances are hit and also to provide foundational 'time' for you to work with. Point to make here: [Fixed Update vs Update.](https://learn.unity.com/tutorial/update-and-fixedupdate)

## Unity Update vs Fixed Update

Update loop is **NOT** called on a regular timeline - this is really important to understand. Update is running 'as fast as possible' meaning that every frame/loop that Unity processes is directly tied to what's going on within your hardware, software, etc. The time difference between update loops changes each loop and we have no guarantee that Update will maintain a constant interval.

## Data Standards

Let's go to the Environmental Protection Agency (EPA) - some of you cited our largest challenges are dealing with the environment so let's see what the [EPA says on 'Data Standards'](https://www.epa.gov/data-standards/learn-about-data-standards)!

>Data standards are documented agreements on representation, format, definition, structuring, tagging, transmission, manipulation, use, and management of data. EPA data standards are a means to promote the efficient sharing of environmental information among US EPA, states, tribes, local governments, the private sector, and other information trading partners.

In a nutshell: how to effectively communicate information about something with others in a way in which we can reimplement that and/or understand it. There are a lot of standards out there... technically every single file type on your computer is a sort of 'standard': .png, .jpg, .csv, .json, .docx, .html, .md... so why would we do this and why should you care if it's just your game and no one else is going to use it? If you build your game around this simple idea: *'how does **data** in my game move*, your game will have less bugs, will be more likely to scale later if needed, and is easier to communicate with others who might be helping.

## Interoperability

At the core of having data standards we want to generally do something with the standard - view an image - open a website - see the text you wrote, etc. So now with these standards we can build systems that work together and/or are interoperable. Truly after data standards we just need to agree on how we are going to communicate and then you're off the to races building interoperable systems. I just want you to be aware of this word as it's used heavily within the DoD and you're seeing it more and more across other domains now - so let's just say that two of you in the class today agreed on a data standard and then both shared each others ways of getting that data - say you stored online in a database and you shared each others access keys, by knowing the data standard and by having the communication protocols locked in you all could build two different games that allowed you to load each others data... or even better let the data drive your game in near-real time! :rocket:

## Serialization and Marshalling

Serialization and why you should be aware. Serialization is taking a data structure/object and encoding it into something a computer can store and/or transfer in a way that if we understand how it was serialized/encoded, we can deserialize/decode it on the other end and get an exact copy of the original data. Aka we take some data and turn it into a bunch of bytes that have some sort of order in which on the end if we process those bytes in the same order we get whatever that data structure is (assuming we have the information on how to deserialize it!) This is the core general term to how we files are saved and/or transferred. Now you might do a lot of other things on-top of serialization, maybe you encrypt it, maybe you started with one format, converted it to another, etc. It's super easy to use and is one simple way to hide some of your data - but not full proof!

## Singleton Curse

I want to briefly get into a Singleton pattern here - we will spend more time on that coming up - I want to open up how easy it is to use but point out that it's a curse as you scale and can cause a lot of problems. Good to be aware of them - they can be helpful in a pinch but in the long run there are better alternatives.

## Live Unity

* Pull up GitHub Desktop
  * Make sure you're logged in
  * File --> 'New Repository'
    * Make sure you put it in a folder that you know where it is and that it's not in another repository!
    * Name the folder: Game395_firstName_wk2
    * For Readme = yes
    * For gitignore file = Unity
* Pull up Unity Hub
  * New Project
  * At the top of the window make sure it's Editor Version 2022.3.xx (don't worry if it's not the exact one I'm using)
  * Find the 'First Person Core' template and select that.
  * Give it a name Unity_wk2 and make sure the location is in the folder you created on GitHub!
  * Hit Create project
* Let's move the generated *gitignore file
  * As Unity is building the project, go to your folders and navigate to the main/root folder you created for this project.
  * Turn on hidden files
    * Windows: In the fodler tab, go to the view tab, find the 'Hidden items' and make sure to check it
    * Mac: While in the folder, just hit '**command**, **Shift**, and **.**' (period)
  * Find the .gitignore and move it to the root folder of your Unity project in the same folder as where it says 'Assets'
* Back to Unity
  * First thing were going to do!
    * Edit/Preferences...
    * Change our play color!!!
  * Go to File/Build Settings (CTRL,SHIFT,B)
    * Navigate to Player, then under 'Other Settings' scroll down to the bottom where it says 'Active Input Handling*' and change it to both systems. This will automatically restart Unity.
* When Unity restarts: lets go to the Unity Package Manager
  * John Custom Package
    * Go to Window, find Package Manager and hit it
    * In the top left corner, where the plus icon is, use the dropdown arrow to select 'Add Package from git url'
    * Type this into the field: "https://github.com/jshull/GAME395_UP_DataSerializer.git"
    * Import the samples after it loads
  * While still in the package manager
    * Navigate over to the Input System package: look for the 'Input Recorder' in the samples, import that.
* Now in your Unity Project tab where you see 'Assets' look for 'Samples/ODU Data Serializer/0.2.0/Data Serialization Example'
* Now this is a little tedious, so watch and read as I go along. For those not familiar with Unity at all - I'm going to show you why I like having the 2 x 3 layout because I like to mess with stuff in the editor
* Proceed to walk through how and what this does
* Navigate to the file we just saved
  * Check your hidden windows folders!
  * Lets open up a JSON file
  * Lets open up a byte array file
* Now back to Unity - find the samples first person controller scene
* Lets add a recorder (we've already imported the samples)
* How does this work? What did I just do!?