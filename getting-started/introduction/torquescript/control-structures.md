# Control Structures

TorqueScript provides basic branching structures that will be familiar to programmers that have used other languages. If you are completely new to programming, you use branching structures to control your game’s flow and logic. This section builds on everything you have learned about TorqueScript so far.

### if, else

This type of structure is used to test a condition, and then perform certain actions if the condition passes or fails. You do not always have to use the full structure, but the following syntax shows the extent of the conditional:

{% code lineNumbers="true" %}
```clike
if(<boolean expression>)
{
   //pass logic
}
else
{
   //alternative logic
}
```
{% endcode %}

Remember how boolean values work? Essentially, a boolean can either be true (1) or false (0). The condition (boolean) is always typed into the parenthesis after the “if” syntax. Your logic will be typed within the brackets `{}`. The following example uses specific variable names and conditions to show how this can be used:

{% code lineNumbers="true" %}
```clike
// Global variable that controls lighting
$lightsShouldBeOn = true;

// Check to see if lights should be on or off
if($lightsShouldBeOn)
{
   // True. Call turn on lights function
   turnOnLights();

   echo("Lights have been turned on");
}
else
{
   // False. Turn off the lights
   turnOffLights();

   echo("Lights have been turned off");
}
```
{% endcode %}

Brackets for single line statements are optional. If you are thinking about adding additional logic to the code, then you should use the brackets anyway. If you know you will only use one logic statement, you can use the following syntax:

{% code lineNumbers="true" %}
```clike
// Global variable that controls lighting
$lightsShouldBeOn = true;

// Check to see if lights should be on or off
if($lightsShouldBeOn)
  turnOnLights();   // True. Call turn on lights function
else
  turnOffLights(); // False. Turn off the lights
```
{% endcode %}

<mark style="color:orange;">NOTE: Brackets and their usage are a 'style' if you are working as a part of a team, it might be that they have a convention or guide in the style they use, it is always best to have a single style in your codebase, phrase of the day here; Be Consistent if you bracket single line stuff do it all the time.</mark>

### switch, switch$

If your code is using several cascading if-then-else statements based on a single value, you might want to use a switch statement instead. Switch statements are easier to manage and read. There are two types of switch statements, based on data type: numeric (`switch`) and string (`switch$`):

{% code lineNumbers="true" %}
```clike
switch(<numeric expression>)
{
   case value0:
       statements;
   case value1:
       statements;
   case value3:
       statements;
   default:
       statements;
}
```
{% endcode %}

As the above code demonstrates, start by declaring the switch statement by passing in a value to the `switch(...)` line. Inside of the brackets `{}`, you will list out all the possible cases that will execute based on what value is being tested. It is wise to always use the default case, anticipating rogue values being passed in:

{% code lineNumbers="true" %}
```clike
switch($ammoCount)
{
   case 0:
      echo("Out of ammo, time to reload");
      reloadWeapon();
   case 1:
      echo("Almost out of ammo, warn user");
      lowAmmoWarning();
   case 100:
      echo("Full ammo count");
      playFullAmmoSound();
   default:
      doNothing();

```
{% endcode %}

`switch` only properly evaluates numerical values. If you need a switch statement to handle a string value, you will want to use `switch$`. The `switch$` syntax is similar to what you just learned:

{% code lineNumbers="true" %}
```clike
switch$ (<string expression>)
{
   case "string value 0":
                statements;
   case "string value 1":
                statements;
   case "string value N":
                statements;
   default:
                statements;
}
```
{% endcode %}

Appending the $ sign to switch will immediately cause the parameter passed in to be parsed as a string. The following code applies this logic:

{% code lineNumbers="true" %}
```clike
// Print out specialties
switch($userName)
{
   case "Heather":
      echo("Sniper");
   case "Nikki":
      echo("Demolition");
   case Mich:
      echo("Meat shield");
   default:
      echo("Unknown user");
}
```
{% endcode %}

### for

As the name implies, this structure type is used to repeat logic in a loop based on an expression. The expression is usually a set of variables that increase by count, or a constant variable changed once a loop has hit a specific point:

{% code lineNumbers="true" %}
```clike
for(expression0; expression1; expression2)
{
    statement(s);
}
```
{% endcode %}

One way to label the expressions in this syntax are (startExpression; testExpression; countExpression). Each expression is separated by a semicolon:

{% code lineNumbers="true" %}
```clike
for(%count = 0; %count < 3; %count++)
{
    echo(%count);
}


```
{% endcode %}

```
OUTPUT:
0
1
2
```

The first expression creates the local variable `%count` and initialises it to 0. The second expression determines when to stop looping, which is when the `%count` is no longer less than 3. Finally, the third expression increases the count the loop relies on.

### foreach

Simplify the iteration over sets of objects and string vectors.&#x20;

To loop over each object in a SimSet, use the foreach statement:

{% code lineNumbers="true" %}
```clike
foreach( %obj in %set )
   /* do something with %obj */;
```
{% endcode %}

To loop over each element in a string vector, use the foreach$ statement:

{% code lineNumbers="true" %}
```clike
foreach$( %str in "a b c" )
   /* do something with %str */;
```
{% endcode %}

### while

A while loop is a much simpler looping structure compared to a for loop.

{% code lineNumbers="true" %}
```clike
while(expression)
{
    statements;
}
```
{% endcode %}

As soon as the expression is met, the while loop will terminate:

{% code lineNumbers="true" %}
```clike
%countLimit = 0;

while(%countLimit <= 5)
{
   echo("Still in loop");
   %count++;
}

echo("Loop was terminated");
```
{% endcode %}
