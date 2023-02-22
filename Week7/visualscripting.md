# Visual Scripting

Visual scripting in Unity is really powerful - but it still has a lot of overhead to get into it. Mainly that it relies on you being aware of the various Unity Core libraries and some of the more useful functions/methods. As you start using Visual Scripting you will realize that searching for functions/methods native to Unity libraries is a big part of working through Visual Scripting.

* Note: There are some areas of work that Visual Scripting just takes *A LOT* longer to utilize in which one or two lines of written C# code is ideal from a time perspective. I believe a hybrid approach to these systems is an ideal starting point for anyone new to Unity and new to programming. If you're experienced in programming you might find the visual scripting enjoyable but rather time consuming to build out full systems.

## Setup

Get out your Unity project and go to the Package Manager and confirm or install the Visual Scripting Library - as of 2021 Unity now provides the Visual Scripting Library in all of it's 'default packages'

### Terminology

* Machine
  * Script Machine: Component that contains your 'Graph' and your referenced Script Graph Asset.
  * State Machines: Component that contains
* Graph
  * A graph is your Unity data that can be thought of as your class - just in the data format that works with the Unity Graph Editor
* Subgraph
  * A graph that you can reuse 
* Script Graph Window
  * The Unity Editor interface for modifying and updating your Graphs

## Script Graph Window/Editor

Similar to the UI Builder: the graph editor is an entirely new Unity Editor experience and can almost live on it's own.

* Graph Window: main area where you build and modify your 'graph'
* Graph Inspector: similar to how the normal Unity Editor Inspector works - provides details for teh selected unit/node that you have selected in your graph
* Blackboard: holds all of your variables/parameters associated with the graph.

![Visual Scripting Window](../images/VisualScriptingEditor.PNG)

To follow along with how Unity teaches this section in most cases you want to separate the panels as by default they are stacked which can cause some issues viewing both at the same time.

![Visual Scripting Window](../images/VisualScriptingEditor_01.PNG)

The rest of the visual scripting blocks will be discussed in class as we slowly go through the basics of visual scripting and getting it working with other scene content.

## Clive the Cat Example

* Will be going through the [Clive the cat](https://learn.unity.com/project/visual-scripting-application-clive-the-cat-s-visual-crypting)
* Setup a clean project in 2022, use 3D core as your template, and while Unity is loading that new project make sure to add your [.gitignore]()
* ![Visual Scripting Clive Install](../images/VS_Clive_01.png)
* ![Visual Scripting Clive Import](../images/VS_Clive_02.png)
* If you see another prompt about dependencies - just accept it.
* ![Visual Scripting Clive Import Next](../images/VS_Clive_03.png)

In class I will be going through the [Unity Learn Clive the Cat Material](https://learn.unity.com/tutorial/gameplay-logic-in-visual-scripting?uv=2021.3&projectId=605b6eefedbc2a0020a72147#63a13396edbc2a52cff857a5).

* We will create a sub-graph
* We will modify an event based graph
  * 'Want To Enter Cell'
  * 'Enter Cell'
  * 'Want To Exit Cell'
  * 'Exit Cell'
  * 'Want to Cross Edge'
  * 'Crossing Edge'
