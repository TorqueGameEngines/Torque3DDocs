# What are Assets?

## What are assets?&#x20;

Assets, as far as Torque3D 4.0 is concerned, is a means of tracking a game’s content via metadata. There are many types of assets: shapes, materials, images, levels, sounds and so on. Unlike a simple file path reference, the metadata an asset provides gives a litany of supporting data and utility.

<img src="https://lh4.googleusercontent.com/UA4HpjXAk6LHE2Ds-Bc3xOr6gwgUeo9vEevNgn4TYArUxXR0Hq73ROqaE8HkEowfftvp-KbR6J5kE5KgLQ7vfalmTeYbXm_efvjC4CQS9Bk3IlV1a9MJtII8rLpow_gPIjgBkiD2qqsiSM4u4eh2ViciRjmEc3WoMW0LbEGdZLbA9iYnovRDDQpl" alt="" data-size="original">

Classically, engine assets such as shape files were simply the literal files themselves. A class or object that would want to use said shape file would have a filepath field that would point to it, and the class would process it. In a few special cases, like shape files, the loader logic for the shape would run some logic during load to generate secondary files. For shapes, you’d have your engine-formatted \*.cached.dts data, the shape constructor script file, etc.

Loading resources the classical way An example of when the shape is loaded can be seen here. We pass in the filepath into the resource loader, and in the case of Shape resources, would generate the \*.cached.dts file if it didn’t exist, and load it if/when it did, returning the shape resource.

![](https://lh6.googleusercontent.com/5j9g\_J9mWaJDT2yoL15AjTA9eVWMpsUt\_ZefYidBAv4t5b2\_s8nVe8N9xbpzizHdzAJ7s7auswxJJqXyUZA9isqzu-5Ans8pwzowi-NiNkvCJb-WQ71MlFIE\_IxYdO3BRINuZuNiUjRx9WU5vDEoPVwRgnO36dVs4VxRlBSN6PfhwXTGrix\_e1-d)

One of the problems, however, was it relied on a direct file reference.

If for any reason - a typo, the file was moved or deleted or so on - the file was not found at the file path, it broke.

![](https://lh3.googleusercontent.com/CZ81LJLCunINHwRSdDX-wj6OYZ6QlcEQfbSjgLzJxHoqgylOI\_fs3vHkMQZsxpDzrl6aT3IAOfc7QSyo75VDZKXl0T4ULboTEzdkh4o5iln0QmB04wCCAS-IiiSbB6w7Z2wlj4cMFpMPad7ChLLQvIo\_\_kjz38kCHWbfArboONIvToKHLRp9OhPf)

When this happened, the object would fail to load, and then would not exist in the scene. This made the level editor particularly dangerous, as if the objects failed to load their shape files, they wouldn’t be added to the scene at all, and if the mapper failed to notice missing objects and saved, they were gone for good.

### Loading resources the Asset way

&#x20;The asset system sidesteps this issue by instead utilizing unique id names to reference, similar to referencing an object by name. The asset itself handles the path info, and game objects themselves need only request the unique id name.

![](https://lh3.googleusercontent.com/LBuJK5YaaKTjYqZsrh8lrVp8S8pA\_WE5mTLGRZ1IUcwiV2lzqXqKUQzuJus3CYAgnzGdwH\_yCJK1Vl8WZfUYW5hwuI8T7N0PdgdCr0lH-r4DWLNfL2D90M5BybEvW49Uw0QJhRY5acv8Ze3NZJsiI8Yad0ANdsa3tfkpKaCUAloP3CoWYgZ9xIWK)

This means that if the shape’s file path was spelt incorrectly, or was moved, then as long as it’s correct in the asset metadata, any object with the assetId will get the correct path.

Another useful aspect is how assets handle fallbacks. In the event an asset isn’t found, or something is not loaded correctly preventing the asset from being used, it can safely fall back to a placeholder asset without ‘damaging’ the original data. As previously noted, the old way, this meant that the object did not load at all, causing problems with the map.

![](https://lh4.googleusercontent.com/J9u\_OYRbs\_OpcnTXihVIR9U1emSnPMRX07\_my6TNnEmsk\_fNikRKqPFvXMgphX6lh6hC45CO6kQAKjLR5d5o6L3Nzzvd8S8xWbzuStNO\_U0TztU2AborvJYcZwBlmqCNh4wyNmmnmeSHuToeQbRICtXdlW7\_k8KzUARbYHxrlIAvFZzRUDFOuLIT)

Instead, the asset system can realize it failed to find or load the requested asset, and provide a placeholder fallback. This allows the level to load as normal, and present obvious indicator content to the level editor or testers that something did not load as was expected, without harming the level file as it’s otherwise being worked on. This prevents the problem from holding up other team members’ tasks.

Other issues often faced in the legacy, path-based resources were order of operations and dependencies loading. To ensure materials were loaded before they were needed(as there was no way to associate materials to what used them), the game template would just scan all material.cs files and bruteforce load everything ahead of time. This could lead to longer startup times, and could be an exploitable vulnerability, as well as often loading a ton of additional material into memory that wasn’t needed.

![](https://lh5.googleusercontent.com/JCx5N6It94dZPJ6HGQVz0pzmUK8wD64LRQFNN9NzDoua9QX0-SuHqnBUJHs38nB0EOpPBE4qN8MMZ1m95XUdsH0rt0bIuJia9F-BXZieS63pHQ-kEILu1Vagsd3z0bf8v1ZKt\_rVa\_0NCsLo2AR7R1lW8T9YInZ84q5Ip49c33R5d-Fr04uYP03r)

It could also suffer from similar path unreliability issues if paths the materials relied on for image maps or the like were invalid due to misspellings, or being moved.

Assets, however, allow integrated dependency tracking. When an asset, such as a shape, is loaded, it has its own list of dependencies.

![](https://lh4.googleusercontent.com/MXCy26ox9SD22qsTsvzvxdh3NvxXoQ5XrKPSHN-LhML77Tp\_El5M6wNUbmJUZT72UUuFTV9qUPdlvB-zwRnhG6ftNnZFBStOlYsn5vM6LAXjPHGWKMKRSRiLFYYJRVHsqqK7qCC4hd82kau0NL0\_mkjC91E13pgTAtaTfOQWcWMg9J17ZykowPqw)

Because asset loading is reference-based. Only assets that are actually called get loaded. When they go to load, it checks for any dependencies in the asset metadata, and loads them first. Those assets load in a similar way, continuing until the dependency chain is complete.

In the above example, the shapeAsset is loaded, but it relies on 2 material assets. It loads those, but those themselves have dependencies to image assets, so those are loaded. Once the entire dependency chain is loaded and valid, the shapeAsset is ready and passed back to the game object that wanted to use it. If anything goes wrong, each can provide a fallback placeholder to ensure things load correctly, while still indicating what and how it failed to provide more info for debugging.

Because assets’ loading is reference-based, when all the references are removed, such as when a level is unloaded, the asset can too be unloaded. This makes post-level cleanup easy, and goes a long way to ensure only memory and resources in use actually get consumed.

Similar to how the Shape loader code has logic to detect if a \*.cached.dts version of the file(which is the shape, but in an engine-friendly binary format) exists - and, if it does not, runs an import process to generate it so it can be used - there is an asset importer that some asset types can run an auto-import on if a file is provided that does not have an asset associated to it.

If a ‘**loose file**’ - a non-asset file - is found that does not have an associated asset to it, the loader code in a game class can run the auto-import process, which will in-place import the file and generate all the asset metadata, including dependencies. Once this is done, the new asset is passed back for the game object to utilize.

Similar to cached.dts generate, however, this is not intended to be utilized in a final, released production game. It creates incredibly long load times, and any generation or import errors could cause unexpected effects, including levels littered with placeholder fallback content. The ideal route is to utilize this during development to ensure all content is correctly imported and has assets, and release the already-generated assets and cached files.
