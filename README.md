# UE5-ModularArrangementSystem

## Overview
-Official documentation for the Modular Arrangement System(MAS) Unreal Engine plugin: setup, usage.
-This version come with two tool: Duplicate tool and arrangemen tool.

### Duplicate Tool
-This tool use to duplicate selected actors with multi feature like offset, custom copy name, incremental suffix, insert into a folder...etc.

-To Open this tool window just select the actors needed to clone then RMB clicked on the level or outliner to trigger actor context menu then look down you can see the duplicate menu.
<Image>

The menu settings include:
* Times: this integer number decide how many duplicate was created.
* Offset: the offset location on the selected actors.
* Path: The path the copy should put into in the outliner heirachy, if the folder/path not exist this will automatic create one. eg: 'Bulding\Bricks'or 'Temple\Columns'
* Move Selection: should we move the selection actors into this folder after clone. false is not moving it and default is false.
* Prefix: this prefix will add to the copy name.
* Suffix: this suffix will add to the copy name.
* Custom name: default copies share the same name with the selection actors. if this is true it will override the name of all copies.
* Incremental: if true this will append a increase number to each copy name.
  + Prefix: This is the prefix of the incremental number.
  + Suffix: append to the incremental number.
  + Digits: how many digits the incremental number could have.
  + From: the start number of the incremental number. example: name=Cube, copy 12 times, Digits=2, From=8 then the first copy name will be Cube08 then Cube09, Cube10...Cube19.
  + Rename Selection: Also renamed the selection actors. With incremental they take the first number and the copies carry on after them.

### Arrangement Tool
-This tool use to arrange selected actor with different layout, filter, order even custom layout as desire.
-There are a few built-in layout use for quick access to those basic arrangement. To use this tool, the minimum of selected actor must be at least two actors, then RMB click on the level or outliner to open the actor context menu. so RMB click->Arrange this will show a sub menu which two session the first is Built-in: Box, Circle, Grid, Line , Sphere and another session is Custom which will appear when user create a preset to reuse.
<Imagge>
-When select a built-in arrange layout will open a Arrangement window, this window can also open by Main menu -> Tools -> Arrangement.
<Image>
-The Arrangement window will have three main sections: Preset, Pivot and Stack.

#### Preset
-This section use to save load a preset which include exact entire stack section and it config/settings on each node which can be load and reuse the layout process for another times, just think about the bulit-in but these preset was custom by user.
-From the left to the right, first is the serach field which use to select a existing and automatic load that preset into the stacks below
<Image>
-Second is the green plus button which use to save new preset and the last one is override/update the current selected preset.
#### Pivot
-Next is the pivot, which is the point where the layout, arrangement begin in the world and it come with a few options.
<Image>
-First is Placement which is determine where to start place the arrangement it come with a few option like start from view port center, first/last actors selection location or center of the selection bound.
-The second is the rotation of the pivot with come to align with axis or custom rotator.

#### Modifer stacks
-This is the core of the arrangement system, this stack can contain vary of modifier type like Filter, Order, Layout and contraints.
-The stack will evaluate from top to the bottom through each modifier a time so each modifier can swap position by drag/drop the header of it.
<Image>
-to start arrange manually first select the actors then on the stacks section has two button a blue dot is arrangement button this will start evaluate the stack and process the result on the level but this is not the final result until user confirm/cancel the arrangement.
-The next is the green plus button which show a small menu with for type of modifiers Filter, Order, Layout and constraints then select the item will add to the stacks.

#### Modifier
-These modular components will drive the arrangement of the selection actors and it share the UI header but also customable too.
<Image>
-From the left to the right on the header, the first one is expandable arrow this useful when we have a long stacks and collapse those will shorten the stacks.
-Second is the modifier type, current it could be Filter, Order, Layout or Constraint, these also come with a different color.
-Right on the type is the modifier subclass picker which allow quick changing sub class.
-Next is the option menu and the delete button. there also another way to show these option by RMB-click on the header which will show the modifier action menu.

##### Filter Modifier
-As it name this class use to filter the selection or the result from previous modifiers on the stacks. Example Filter those actor has class Enemies in the selection group include buildings, trees, rocks, enemies, after filter execute it will return a list of enemies actor to the next modifier in the stack to execute.
-Filter modifier always come with a settings Source which show which is input source for the filter to process is the actors selection on the level or the last result from the previous modifiers.


* Built-in arrangement include:
  + Box: this arrange the selection in to a box layout with settings:
    - Spacing: the spacing between each actor in X, Y, Z direction.
    - Auto Axis: Select the axis which will auto count base on the two other axies to fit the number of actors selected. example six actors were selected and columns=3, rows=2 with Auto Axis=Depth the the Depth will auto calculate Depth=1.
    - Columns, Row, Depth: maximun number of items per axis.
    - Fill Patten: the pattern use during the fill. example fill Center out which fill from the center first and go outward.
    - Axis order: priority fill base on which axis.

