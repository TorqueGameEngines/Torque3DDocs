# Exposing Object Classes to Script

In Torque3D, there are several options available that give the gameplay scripts the ability to read and write variables, and call engine-side functionality. This is important for most classes, as a majority of their logic is implemented within the engine code itself for performance reasons.

Below, this article will go over the means you can use to expose the class to script access.

## Adding Modifiable Fields to an Object Class in Torque3D

Torque3D provides a powerful, but fairly straightforward way to add modifiable fields to object classes, allowing developers to easily modify properties via the tools and gameplay scripts. This functionality is provided through the `addField` or `addProtectedField` functions, which are used inside the `initPersistFields` function of an object class.

### Using addField

The `addField` function is used to define a new field for an object class, which can then be modified in the engine's editors. The basic syntax for using `addField` is as follows:

```scss
addField( name, type, offset(className, fieldName), description );
```

where:

* `name` is the name of the field as it will appear in the editors, or used in scripts.
* `type` is the data type of the field, such as `TypeS32`, `TypeF32`, `TypeString`, etc.
* `className` is the name of the class the field is being exposed for.
* `fieldName` is the name of the class' attribute variable being exposed.
* `description` is a string that provides a brief description of the field, which will be displayed in the editors.

#### Example

Let's say we want to add a modifiable field to an object class in Torque3D that exposes the object's height. The following code shows how to do this using the `addField` function:

```css
void MyObjectClass::initPersistFields()
{
   Parent::initPersistFields();

   addField( "height", TypeF32, offset(MyObjectClass, mHeight), "The height of the object" );
}
```

In this example, we are adding a new field to the `MyObjectClass` object class, with the data type `TypeF32` (floating-point number), defining the offset for the `MyObjectClass` and `mHeight` variable, and a description of "The height of the object".

You may be wondering what the offset macro function is for. What this does is tells the C++ code where to look for the mHeight field inside the MyObjectClass in memory. When scripts or editors get or set the value of the `height` script variable, it can then successfully look up the `mHeight` variable in the `MyObjectClass`.

Below is a list of more detailed information on variants of addField that do expanded or more specialized behavior beyond just exposing a class' variable to script.

{% content-ref url="addprotectedfield.md" %}
[addprotectedfield.md](addprotectedfield.md)
{% endcontent-ref %}

## Adding Engine Methods to an Object Class in Torque3D

In Torque3D, the `DefineEngineMethod` macro function provides a powerful tool for adding engine methods to object classes, allowing developers to expose custom functionality to scripts. This functionality can be used to create new actions, calculations, and other operations that can be performed on objects in the engine, where the C++ code is more efficient than script.

### Using DefineEngineMethod

The `DefineEngineMethod` macro function is used to define a new engine method for an object class, which can be called from scripts. The basic syntax for using `DefineEngineMethod` is as follows:

```scss
DefineEngineMethod( className, methodName, returnType, (argList), (defaultValueList), methodDescription )
{
   // implementation of the method
}
```

where:

* `className` is the name of the class to add the method to.
* `methodName` is the name of the method as it will appear in scripts.
* `returnType` is the data type of the return value, such as `void`, `bool`, `int`, `float`, etc.
* `argumentList` is a list of argument names, in the format `(argType argName, argType argName, ...)`.
* `defaultValueList` is an optional list of default values, matched in order to the `argumentList.`
* `methodDescription` is a string that provides a brief description of the method, which will be displayed in the engine's documentation.

#### Example

Let's say we want to add a new engine method to an object class in Torque3D that sets the object's position. The following code shows how to do this using the `DefineEngineMethod` macro function:

```perl
void MyObjectClass::setPosition(const float& x, const float& y, const float& z)
{
   mPosition = Point3F(x, y, z);
}

DefineEngineMethod( MyObjectClass, setPosition, void, (float x, float y, float z), (0,0,0), "Sets the position of the object." )
{
   object->setPosition(x, y, z);
}
```

In this example, we are adding a new engine method `setPosition` to the `MyObjectClass` object class, with a return type of `void`, arguments of `x`, `y`, and `z` each with data type `float`, and a description of "Sets the position of the object."

{% hint style="info" %}
It's important to note that while we have default values for each argument here, any and all default values are optional. If no default values are defined, then the enclosing parentheses are removed, like so:

```
DefineEngineMethod( MyObjectClass, dump, void, (),, "Dumps info about the object to the console" )
{
    object->dump();
}
```

The parentheses for the arg list are required, but the empty default values list is not.
{% endhint %}

{% hint style="info" %}
If using an Object Class for an argument type, the default must be defined as:

```
nullAsType<MyObjectClass*>()
```
{% endhint %}

Below is an example of it being called in a script:

```
%obj = new MyObjectClass();
%obj.setPosition(5, 10, 3);
```

With this implementation, the engine method can be called from scripts to set the position of an object in the engine, making it easier to control the position of objects in your game.
