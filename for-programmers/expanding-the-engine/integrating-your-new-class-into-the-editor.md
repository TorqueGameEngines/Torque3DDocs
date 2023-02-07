# Exposing Object Classes to Script

In Torque3D, there are several options available that give the gameplay scripts the ability to read and write variables, and call engine-side functionality. This is important for most classes, as a majority of their logic is implemented within the engine code itself for performance reasons.

Below, this article will go over the means you can use to expose the class to script access.

## Adding Modifiable Fields to an Object Class in Torque3D

Torque3D provides a powerful, but fairly straightforward way to add modifiable fields to object classes, allowing developers to easily modify properties via the tools and gameplay scripts. This functionality is provided through the `addField` or `addProtectedField` functions, which are used inside the `InitPersistFields` function of an object class.

### Using addField

The `addField` function is used to define a new field for an object class, which can then be modified in the engine's GUI editor. The basic syntax for using `addField` is as follows:

```scss
addField( name, type, offset(className, fieldName), description );
```

where:

* `name` is the name of the field as it will appear in the editors, or used in scripts.
* `type` is the data type of the field, such as `TypeS32`, `TypeF32`, `TypeString`, etc.
* `className` is the name of the class the field is being exposed for.
* `fieldName` is the name of the class' attribute variable being exposed.
* `description` is a string that provides a brief description of the field, which will be displayed in editors.

### Example

Let's say we want to add a modifiable field to an object class in Torque3D that exposes the object's height. The following code shows how to do this using the `addField` function:

```css
function MyObjectClass::InitPersistFields()
{
   Parent::InitPersistFields();

   addField( "height", TypeF32, offset(MyObjectClass, mHeight), "The height of the object" );
}
```

In this example, we are adding a new field to the `MyObjectClass` object class, with the data type `TypeF32` (floating-point number), defining the offset for the `MyObjectClass` and `mHeight` variable, and a description of "The height of the object".

You may be wondering what the offset macro function is for. What this does is tells the C++ code where to look for the mHeight field inside the MyObjectClass in memory. When scripts or editors get or set the value of the `height` script variable, it can then successfully look up the `mHeight` variable in the `MyObjectClass`.

###
