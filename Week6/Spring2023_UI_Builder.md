# Unity UI

We are going to play around with the two main ways you can build some UI content in Unity. What you will figure out pretty quickly is that the older UnityEngine.UI system is really easy to use out the gate, but terrible to adjust and to make changes to over time.

Assets I'm using in todays class

* [JetBrains Font Download](https://download.jetbrains.com/fonts/JetBrainsMono-2.304.zip?_gl=1*dmkehz*_ga*MTc5MTc5OTcyOC4xNjc2NDg1MzIz*_ga_9J976DJZ68*MTY3NjQ4NTMyMi4xLjAuMTY3NjQ4NTMyNi4wLjAuMA..&_ga=2.122666379.1614187004.1676485323-1791799728.1676485323)
* [All Google Fonts](https://fonts.google.com/)
  * [Roboto Font Download](https://fonts.google.com/download?family=Roboto)
* [Google Icons Resource](https://fonts.google.com/icons)

## New UI System Unity UI Builder

The new UI Toolkit and the UI Builder is a very nice addition to Unity. Unfortunately this toolkit is really designed around having some previous experience with cascading style sheets (CSS). Thankfully Unity provides a builder that sort of makes this easy - but it will be important for you all who really want to fully understand this to spend additional time understanding general website HTML/CSS relationships as I won't be spending a lot of time covering that in class but will hint at it throughout.

### Basic Setup

* By default it's already installed in Unity with any version over 2021.
* Create a Blank Scene
  * Name it '00_Menu'
* Create a 'UI Document' in the hierarchy by right clicking, 'UI Toolkit-->UI Document' and find the UI Builder option.
  * ![UIBuilder](/images/UIBuilder_01.png)
* This then creates a gameobject and adds the UI Document component on it
  * ![UI Builder 2](/images/UIBuilder_02.png)
  * Notice the 'Source Asset' is missing, so let's create it.
* Right click in your assets folder where you want to save this asset - I created a new folder called UI under my ODU395 folder and in that folder in Unity I right clicked, Create--> UI Toolkit--> UI Document. Name this document something like 'Unity_395_MenuUXMLTemplate'
  * ![UI Builder Creating UXML Document](/images/UIBuilder_03.png)
  * With this UXML document created, let's drag it on our Scene GameObject we created the step before under the UI Document Component, and in the Source Asset Field.
    * ![UI Builder UXML Attached to Component](/images/UIBuilder_04.png)
* Double click the UXML document you just created to open it up in the UI Builder Unity Window.
  * ![UI Builder interface](/images/UIBuilder_interface.png)
* At first this is going to look sort of very different to your normal Unity tools
* This entire system is built as a hybrid visual editor that relies on some well known HTML/CSS standards and then Unity basically packages it all up as a 'special' [XML](https://www.w3.org/standards/xml/core#:~:text=What%20is%20XML%3F,more%20suitable%20for%20Web%20use.) document that they call 'UXML'.
  * For those familiar with CSS and HTML you will slowly start to see how powerful this new way of building UI elements can be.
* Let's first get our main UI to align to our game view as by default it's clearly not correct.
  * ![UI Builder Default Interface Vertical Page](/images/UIBuilder_interface_01.png)
  * Make the adjustment and notice that it greys out the dimensions and it's going to align this UI to your current game view pixel size/setup.
  * ![UI Builder Game View Align](/images/UIBuilder_interface_02.png)
* At this moment you have the absolute basics in to start building your interface.
* There are a few high level details you can adjust here: like if you want a solid color for your main backdrop, an image, or you want to grab a feed from a camera.
  * ![UI Builder Canvas Background](/images/UIBuilder_interface_03.png)

### Buttons, UI Builder Position, Align, & Size

* In the Library window (bottom left) of the UI Builder window find the 'Button' component and drag it into your viewport/canvas.
  * ![UI Builder Button Drag and Drop](/images/UIBuilder_Button_00.png)
* Lets explore all of the properties of this button in the right side of the UI Builder window
* First lets make sure to give our Button a reference name - the very top parameter on the right Inspector - this is how we will reference *this* button later: I named mine 'StartButton'
  * Let's update our text as well for what it says on our Button: 'Start Game'
  * ![UI Builder Button Settings](/images/UIBuilder_Button_01.png)
* Let's look at the Display properties 'Absolute' & 'Relative'
  * ![UI Builder Display Settings](/images/UIBuilder_Button_02.png)
  * Going to play around here with some settings to get what I want
* Let's now look into the Position, Align, and Size Settings
  * ![UI Builder Align Settings](/images/UIBuilder_Button_03.png)
* These settings are the core settings to the way you want to layout and position your button. Now depending upon what you're going for and/or how you want this button to dynamically adjust to screen size and/or not to screen size these settings will be the core areas for your initial basic buttons.
* In class I will demonstrate how to create our own custom style requiring us to create new or modify an existing style sheet
  * We will go through a button style variation ':hover' to provide feedback for our clicking as well as ':active'

### Panels, Containers, and CSS Styles

* I'm going to go through some rapid fire changes in class to demonstrate how to adjust these items as you think about containerizing pieces of UI elements.
* Style sheets and information on those containers flows down for items contained and similar for how those items might be contained in other containers.
* [Cascade Style Sheet](https://www.w3schools.com/css/css_intro.asp)
