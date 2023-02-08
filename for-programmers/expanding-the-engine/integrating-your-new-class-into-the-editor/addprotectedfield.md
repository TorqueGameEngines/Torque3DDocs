# addProtectedField

### Using addProtectedField

The `addProtectedField` function is used to define a new field for an object class, which can be accessed and modified in scripts and in the engine's GUI editor. The main difference between `addField` and `addProtectedField` is the latter controls access of the class object's variable. The basic syntax for using `addProtectedField` is as follows:

```scss
addProtectedField( name, type, offset(className, fieldName), setFunction, getFunction, writeFunction, description );
```

where:

* `name` is the name of the field as it will appear in the editor, or used in scripts.
* `type` is the data type of the field, such as `TypeS32`, `TypeF32`, `TypeString`, etc.
* `fieldName` is the name of the class' attribute variable being exposed.
* `className` is the name of the class the field is being exposed for.
* `setFunction` is the name of a custom set function that is called whenever the value of the field changes.
* `getFunction` is the name of a custom get function that is called whenever the value of the field is accessed.
* `writeFunction(optional)` is the name of a custom write function that is called whenever the value of the field is written out to a file as part of serialization.
* `description` is a string that provides a brief description of the field, which will be displayed in the editors.

#### Example

Let's say we want to add a protected field to an object class in Torque3D that represents the object's name. The following code shows how to do this using the `addProtectedField` function:

```javascript
void MyObjectClass::initPersistFields()
{
   Parent::initPersistFields();

   addProtectedField( "name", TypeString, offset(MyObjectClass, mHeight), &setName, &getName, "The name of the object" );
}

bool MyObjectClass::setName(void *obj, const char *array, const char *data)
{
   MyObjectClass* myObj = static_cast<MyObjectClass*>(obj);
   if (myObj )
      myObj->setName(data); //Call to our normal class set function
   return false;
}

const char* MyObjectClass::getName(void* obj, const char* data)
{
   MyObjectClass* myObj = static_cast<MyObjectClass*>(obj);
   
   //This lets us check if we have a valid name, and if not, return 
   //a sane value
   if(myObj->getName())
      return myObj->getName(); //The value is good, so use the normal class get function
   
   return StringTable::EmptyString;
}
```

In this example, we are adding a new protected field to the `MyObjectClass` object class, with the data type `TypeString`, defining the offset for the `MyObjectClass` and `mHeight` variable, custom set and get functions `setName` and `getName`, and a description of "The name of the object".&#x20;

For simplicity, and because it is not commonly used, we ignored the `writeFunction` in this example.

It's important to note that, similar to how `initPersistFields()` itself is a static function because it is invoked for the class configuration, not a specific object itself, the set, get, and write functions called back are also defined as static in the class header.

This is why you see that there is a `static_cast` applied to go from the `void*` to the actual object being modified.

With this implementation, the protected field can be accessed and modified both in the engine's editor and in scripts, and the custom set and get functions ensure that the value of the field is properly set and retrieved.
