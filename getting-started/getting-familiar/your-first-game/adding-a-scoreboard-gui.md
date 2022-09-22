# Adding a Scoreboard GUI

### Objects and child objects

When creating objects we are able to define an initialiser. This initialiser has an interesting feature. If you were to create an object like a `SimGroup`, which contains more objects you could do this:



```csharp
%obj = new SimGroup(){};
%obj.addObject(new SimObject(){});
%obj.addObject(new SimObject(){});
//etc..
```

But the constructor allows us to instantiate the child objects inside the constructor:

```csharp
%obj = new SimGroup(theGroup){
   new SimObject(){};
   new SimObject(){};
};
```

We often utilize this feature when writing new .gui files:

```csharp
%guiContent = new GuiControl(ScoreBoardGui){
   new GuiBitmapBorderControl(){
      new GuiBitmapControl(){
      };
   };
};
```

This code will create a new control with a bitmap border inside, and a bitmap inside the border.&#x20;

## The Scoreboard GUI

I prefer writing GUIs in script because the editor feels a bit clumsy to me. Let's start by creating the baseline GUI file in `data/CoinCollection/client/gui/scoreBoard.gui`:

```csharp
new GuiControl(ScoreBoardGUI) {
    position = "0 0";
    extent = "1024 768";
    profile = "GuiModelessDialogProfile";
    tooltipProfile = "GuiToolTipProfile";
    isContainer = "1";
    canSaveDynamicFields = "1";
    enabled = "1";
    noCursor = "1";
};
```

This is a simple control that basically fills the whole screen (starts at top left corner, scales down to the top right corner and it is anchored to the right and bottom sides).

Now we'll add the content inside of it piece by piece.

### A centered container <a href="#a-centered-container" id="a-centered-container"></a>

Now we will need to center the content inside the `ScoreBoardGUI` so it is centered on the screen. Add this to the `GuiControl` `ScoreBoardGUI`, (Remember how we did it? Read “Objects and childobjects again.").

```csharp
new GuiPanel() {
    docking = "None";
    position = "370 271";
    extent = "283 226";
    horizSizing = "center";
    vertSizing = "height";
    profile = "ScoreBoardProfile";
    tooltipProfile = "GuiToolTipProfile";
};
```

This creates a new panel in the center of the screen. Extent means the size of the panel. This panel is `283px` wide and `226px` tall.

We make sure it is centered by letting position be `(screenwidth/2)-(extent/2)`. In this case it is `(1024/2)-(283/2)`, (Likewise for height).

We set `vertSizing` to `height`, which means that it will follow the height of the screen and thus scale vertically.

We set `horizSizing` to `center`, so that it wont scale horizontally. This is because a horizontal scaling would corrupt the design of the scoreboard.

### Headers for the scores <a href="#headers-for-the-scores" id="headers-for-the-scores"></a>

We will be using a `GuiTextListCtrl` to list the players. We can consider it like a table. Since every new `Text` in the list is a row, and we can specify columns by tabs.

Therefore we need some headers for the values “Coins, Kills, Deaths” (yes we will add in some ‘kill each other’ feature in a later tutorial).

**So put this inside the GuiPanel you just created:**

```csharp
new GuiTextCtrl() {
    text = "Coins";
    maxLength = "255";
    position = "104 2";
    extent = "33 18";
    profile = "ScoreBoardTextBoldProfile";
    tooltipProfile = "GuiToolTipProfile";
};
new GuiTextCtrl() {
    text = "Kills";
    maxLength = "255";
    position = "158 2";
    extent = "30 18";
    profile = "ScoreBoardTextBoldProfile";
    tooltipProfile = "GuiToolTipProfile";
};
new GuiTextCtrl() {
    text = "Deaths";
    maxLength = "255";
    position = "206 2";
    extent = "37 18";
    profile = "ScoreBoardTextBoldProfile";
    tooltipProfile = "GuiToolTipProfile";
};
```

As you can see the position value is not very high on these elements, that’s because their parent is the `GuiPanel` so their position is relative to the panel!



### The scrollbars <a href="#the-scrollbars" id="the-scrollbars"></a>

If alot of players is joining, we will need some scrollbars. For this we need a `GuiScrollCtrl` placed inside of the `GuiPanel`.

```csharp
new GuiScrollCtrl() {
    willFirstRespond = "1";
    hScrollBar = "alwaysOff";
    vScrollBar = "dynamic";
    lockHorizScroll = "1";
    lockVertScroll = "0";
    constantThumbHeight = "0";
    childMargin = "0 0";
    mouseWheelScrollSpeed = "-1";
    position = "0 24";
    extent = "228 202";
    horizSizing = "width";
    vertSizing = "height";
    profile = "ScoreBoardScrollProfile";
    tooltipProfile = "GuiToolTipProfile";
    isContainer = "1";
};
```

As you might be able to see, we don’t want a horizontal scrollbar so it is always off (`hScrollBar = "alwaysOff"`) and the vertical scrollbar only shows if it is necessary (`vScrollBar = "dynamic"`) beside from that, all these settings should be fairly straight forward.

Now last but not least we need the aforementioned `GuiTextListCtrl` placed inside the `GuiScrollCtrl`:

```csharp
new GuiTextListCtrl(ScoreBoardGUIList) {
    columns = "0 98 153 200";
    fitParentWidth = "1";
    clipColumnText = "0";
    position = "0 0";
    extent = "228 8";
    horizSizing = "width";
    vertSizing = "height";
    profile = "ScoreBoardTextNormalProfile";
    tooltipProfile = "GuiToolTipProfile";
    isContainer = "1";
};
```

The important things to note here is the `columns` attribute, the `fitParentWidth` attribute and the `clipColumnText` attribute.

* `columns` specifies where the columns will be (on the x-axis relative to the `GuiTextListCtrl`). As you might have noticed this matches the positions of the `GuiText` controls!
* `fitParentWidth` this makes the `TextListCtrl` fill the scroll horizontally.
* `clipColumnText` this makes sure that the columns don’t break or overwrite each other. If the string in this column is longer than the column it will be cut out.

### The final structure <a href="#the-final-structure" id="the-final-structure"></a>

When you are done your structure for the GUI should look something like this:

* `GuiControl` _“ScoreboardGUI”_
  * `GuiPanel`
    * `GuiTextCtrl` _“Coins”_
    * `GuiTextCtrl` _“Kills”_
    * `GuiTextCtrl` _“Deaths”_
    * `GuiScrollCtrl`
      * `GuiTextListCtrl` _“ScoreBoardGUIList”_

### Styling the GUI <a href="#styling-the-gui" id="styling-the-gui"></a>

Here is one thing that you may have noticed and that I haven’t explained!

The profiles! The profile is to GUI objects what CSS is to HTML. They define the style of the GUI’s

I wont spend a lot of time with the profiles even tho they are quite important. Therefore we will use alot of the stock profiles and only create a single custom one.

In `data/CoinCollection/client/gui/customProfiles.cs` add the following snippet:

```csharp
singleton GuiControlProfile(ScoreBoardProfile : GuiDefaultProfile) {
    opaque = "1";
    fillColor = "0 0 0 200";
    fillColorHL = "0 0 0 200";
    borderColor = "0 0 0 255";
    borderThickness = "5";
    border = "1";
};

singleton GuiControlProfile(ScoreBoardTextBoldProfile : GuiDefaultProfile) {
    fontType = "Arial Bold";
    fontColor = "255 255 255 255";
};

singleton GuiControlProfile(ScoreBoardTextNormalProfile : GuiDefaultProfile) {
    fontType = "Arial";
    fontColor = "255 255 255 255";
};

singleton GuiControlProfile(ScoreBoardScrollProfile : GuiDefaultProfile) {
    fontType = "Arial Bold";
    fontColor = "255 255 255 255";
};
```

This should be pretty easy to understand. All controls using the "ScoreBoardProfile" has a black background which is transparent and the border is 5 px wide, black and not transparent.

There is alot more settings that can be played with, for setting text color bevel etc.. This is not within the scope of this tutorial unfortunately!

## Showing the scoreboard <a href="#the-functionality" id="the-functionality"></a>

Now we need to add some functionality to the scoreboard!

**First we should be able to see it shouldn’t we?**

At the bottom of `data/CoinCollection/client/gui/scoreBoard.tscript` add the following code:

```csharp
//-----------------------------------------------------------------------------
// ScoreBoardGUI utility methods
//-----------------------------------------------------------------------------
function ScoreBoardGUI::toggle(%this)
{
    if (%this.isAwake())
        Canvas.popDialog(%this);
    else
        Canvas.pushDialog(%this);
}

function ScoreBoardGUI::clear(%this)
{
    // Override to clear the list.
    ScoreBoardGUIList.clear();
}
```

This toggles the `ScoreBoardGUI` so a call to `ScoreBoardGUI.toggle()` will make it pop up on the screen. If we then call `toggle()` again it will hide itself.

Now, this is just a function we need a way to call it. And calling it through the console is quite.. Clumsy.. So lets add a keybinding!

### Adding an ActionMap

An ActionMap is a way to bind actions to inputs. We can push ActionMaps so that we can change keybindings temporarily and then pop them so we revert to whatever the bindings were previously.

In `data/CoinCollection/client/actionMap.tscript` add the following:

```csharp
if (isObject( CoinCollectionMoveMap ))
    CoinCollectionMoveMap.delete();

new ActionMap(CoinCollectionMoveMap);
CoinCollectionMoveMap.humanReadableName = "Coin Collection Move Map";

CoinCollectionMoveMap.bind(keyboard, f, showScoreBoard);
```

And then add another file in `data/CoinCollection/client/inputCommands.tscript` with the `showScoreBoard` function:

```csharp
function showScoreBoard(%val) {
    // %val == 1 on key down and 0 on key up
    if (%val) {
        ScoreBoardGUI.toggle();
    }
}
```

Now, we need to push this ActionMap on top of what keybinds we already have. We can do that in `data/CoinCollection/CoinCollection.tscript`, whenever a client connects or disconnects to a server:

```csharp
function CoinCollection::onCreateClientConnection(%this) {
    CoinCollectionMoveMap.push();
}

function CoinCollection::onDestroyClientConnection(%this) {
    CoinCollectionMoveMap.pop();
}
```

Now the final thing is we need to execute all of these scripts we added if you haven't already, in `data/CoinCollection/CoinCollection.tscript`:

```csharp
function CoinCollection::initClient(%this) {
    %this.queueExec("./client/gui/customProfiles.tscript");
    %this.queueExec("./client/gui/scoreBoard.gui");
    %this.queueExec("./client/gui/scoreBoard.tscript");

    %this.queueExec("./client/inputCommands.tscript");
    %this.queueExec("./client/actionMap.tscript");
    %this.queueExec("./client/commands.tscript");
}
```
