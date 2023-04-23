# CallOnModules

In Torque3D, callback functions are used to respond to certain events or actions in the game. One type of callback function that can be utilized is the callOnModules function. This function allows modules to respond to arbitrary calls in a signal-notify-like pattern, without being tied to a specific object. In this article, we will explore how to use callOnModules in TorqueScript.

### Understanding callOnModules

The callOnModules function is used to invoke a function in all loaded modules. This means that any module that has the specified function will be called when callOnModules is invoked. This is useful for creating signal-notify-like behavior in Torque3D.

callOnModules has several useful parameters to control the signaling behavior, as well as allowing arguments to be passed along for recievers.

```javascript
function callOnModules(%functionName, %moduleGroup, %var0, %var1, %var2, %var3, %var4, %var5, %var6)
```

As you can see, it takes not only the functionName to be invoked, but a moduleGroup. Normally this would just be the "Game" group, but allows you to filter the invokes for just tools, or core, or mods.

It additionally supports several arguments that can be passed along to facilitate the function behavior.

### Calling callOnModules to Trigger the Callback

Once you have the callback function in your module's namespace, you can use the callOnModules function to trigger the callback in all loaded modules. For example, to call the "onMySignal" function in all loaded modules, you can use the following TorqueScript code:

```scss
callOnModules("onMySignal");
```

This will invoke the "onMySignal" function in all modules that have it.

### Handling the Callback in a Module

When the callback function is invoked in a module, you can handle it like any other function. For example, if you have a module named "MyModule" and want to handle the "onMySignal" function, you can add the following code to your module:

```javascript
function MyModule::onMySignal(%this)
{
   // Handle the signal here
}
```

This code defines the "onMySignal" function in the "MyModule" module and handles the signal in the module.

### Example Usage

This behavior is broadly useful, because it allows many different modules to handle a common invoke in another module.

For an example, suppose we have in our game items that can be picked up. Rather than having to hard-integrate our gameplay code to specifically call functions for the inventory module to handle the on-pickup event, we can have the on-pickup event utilize callOnModules, and other modules will be able to listen for that call.

For the concrete example:

```javascript
function ShapeBase::setInventory(%this, %itemData, %value)
{
   if(!isObject(%this.inventoryArray))
   {
      %this.inventoryArray = new ArrayObject();
   }
   
   // Set the inventory amount for this datablock and invoke inventory
   // callbacks.  All changes to inventory go through this single method.

   // Impose inventory limits
   if (%value < 0)
      %value = 0;
   else
   {
      %max = %this.maxInventory(%itemData);
      if (%value > %max && %max != 0)
         %value = %max;
   }

   // Set the value and invoke object callbacks
   %currentAmount = %this.getInventory(%itemData);
   if (%currentAmount != %value)
   {
      %name = %itemData.getName();
      %invIdx = %this.inventoryArray.getIndexFromKey(%name);
      
      if(%invIdx == -1)
         %this.inventoryArray.add(%name, %value);
      else
         %this.inventoryArray.setValue(%value, %invIdx);
         
      %itemData.onInventory(%this, %value);
      %this.getDataBlock().onInventory(%itemData, %value);
   }
   callonModules("onSetInventory","Game", %this, %itemData, %value); //%this is the object-instance holding the item
   return %value;
}
```

In this example, our inventory system module handles having an object's inventory being set. Once the inventory change has occured, we use callOnModules to inform about the onSetInventory call, along with the relevant data.

In another module, in this case an Objectives module, we have the function that will be invoked:

```javascript
function ObjectiveModule::onSetInventory(%this, %playerInst, %itemData, %currentAmount)
{
    %count = %this.Objectives.count();
    for (%i=0; %i<%count; %i++)
    {
        %ObjectiveTag = %this.Objectives.getKey(%i);
        if (%ObjectiveTag.collectionItem $= %itemData.getName())
        {
            %idx = %this.items.getIndexFromKey(%itemData.getName());
            if (%idx != -1)
                %this.items.setValue(%currentAmount, %idx);
            else
                %this.items.add(%itemData.getName(),%currentAmount);
                
	         for (%clientIndex = 0; %clientIndex < ClientGroup.getCount(); %clientIndex++)
	         {
		         %cl = ClientGroup.getObject(%clientIndex);
               updateObjectiveForClient(%cl);
            }
            
            if (%currentAmount >= %ObjectiveTag.collectionCount)
                completeObjective(%ObjectiveTag);
        }
    }
}
```

This allows the ObjectiveModule to listen for the onSetInventory event without needing to modify the inventory module's code to call to the objectives module directly.

This allows much more effective drop-in-and-go behavior for modules and allows different gameplay code to easily interop without a lot of manual work to integrate.
