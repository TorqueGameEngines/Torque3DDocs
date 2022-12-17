# What are Assets?

## What are assets?&#x20;

Assets, as far as Torque3D 4.0 is concerned, is a means of tracking a game’s content via metadata. There are many types of assets: shapes, materials, images, levels, sounds and so on. Unlike a simple file path reference, the metadata an asset provides gives a litany of supporting data and utility.

<figure><img src="https://lh4.googleusercontent.com/UA4HpjXAk6LHE2Ds-Bc3xOr6gwgUeo9vEevNgn4TYArUxXR0Hq73ROqaE8HkEowfftvp-KbR6J5kE5KgLQ7vfalmTeYbXm_efvjC4CQS9Bk3IlV1a9MJtII8rLpow_gPIjgBkiD2qqsiSM4u4eh2ViciRjmEc3WoMW0LbEGdZLbA9iYnovRDDQpl" alt=""><figcaption></figcaption></figure>

Classically, engine assets such as shape files were simply the literal files themselves. A class or object that would want to use said shape file would have a filepath field that would point to it, and the class would process it. In a few special cases, like shape files, the loader logic for the shape would run some logic during load to generate secondary files. For shapes, you’d have your engine-formatted \*.cached.dts data, the shape constructor script file, etc.

Loading resources the classical way An example of when the shape is loaded can be seen here. We pass in the filepath into the resource loader, and in the case of Shape resources, would generate the \*.cached.dts file if it didn’t exist, and load it if/when it did, returning the shape resource.

<figure><img src="https://lh6.googleusercontent.com/5j9g_J9mWaJDT2yoL15AjTA9eVWMpsUt_ZefYidBAv4t5b2_s8nVe8N9xbpzizHdzAJ7s7auswxJJqXyUZA9isqzu-5Ans8pwzowi-NiNkvCJb-WQ71MlFIE_IxYdO3BRINuZuNiUjRx9WU5vDEoPVwRgnO36dVs4VxRlBSN6PfhwXTGrix_e1-d" alt=""><figcaption></figcaption></figure>

One of the problems, however, was it relied on a direct file reference.

If for any reason - a typo, the file was moved or deleted or so on - the file was not found at the file path, it broke.

![](https://lh3.googleusercontent.com/CZ81LJLCunINHwRSdDX-wj6OYZ6QlcEQfbSjgLzJxHoqgylOI\_fs3vHkMQZsxpDzrl6aT3IAOfc7QSyo75VDZKXl0T4ULboTEzdkh4o5iln0QmB04wCCAS-IiiSbB6w7Z2wlj4cMFpMPad7ChLLQvIo\_\_kjz38kCHWbfArboONIvToKHLRp9OhPf)

When this happened, the object would fail to load, and then would not exist in the scene. This made the level editor particularly dangerous, as if the objects failed to load their shape files, they wouldn’t be added to the scene at all, and if the mapper failed to notice missing objects and saved, they were gone for good.

### Loading resources the Asset way

&#x20;The asset system sidesteps this issue by instead utilizing unique id names to reference, similar to referencing an object by name. The asset itself handles the path info, and game objects themselves need only request the unique id name.

<figure><img src="https://lh3.googleusercontent.com/LBuJK5YaaKTjYqZsrh8lrVp8S8pA_WE5mTLGRZ1IUcwiV2lzqXqKUQzuJus3CYAgnzGdwH_yCJK1Vl8WZfUYW5hwuI8T7N0PdgdCr0lH-r4DWLNfL2D90M5BybEvW49Uw0QJhRY5acv8Ze3NZJsiI8Yad0ANdsa3tfkpKaCUAloP3CoWYgZ9xIWK" alt=""><figcaption></figcaption></figure>

This means that if the shape’s file path was spelt incorrectly, or was moved, then as long as it’s correct in the asset metadata, any object with the assetId will get the correct path.

Another useful aspect is how assets handle fallbacks. In the event an asset isn’t found, or something is not loaded correctly preventing the asset from being used, it can safely fall back to a placeholder asset without ‘damaging’ the original data. As previously noted, the old way, this meant that the object did not load at all, causing problems with the map.

<figure><img src="https://lh4.googleusercontent.com/J9u_OYRbs_OpcnTXihVIR9U1emSnPMRX07_my6TNnEmsk_fNikRKqPFvXMgphX6lh6hC45CO6kQAKjLR5d5o6L3Nzzvd8S8xWbzuStNO_U0TztU2AborvJYcZwBlmqCNh4wyNmmnmeSHuToeQbRICtXdlW7_k8KzUARbYHxrlIAvFZzRUDFOuLIT" alt=""><figcaption></figcaption></figure>

Instead, the asset system can realize it failed to find or load the requested asset, and provide a placeholder fallback. This allows the level to load as normal, and present obvious indicator content to the level editor or testers that something did not load as was expected, without harming the level file as it’s otherwise being worked on. This prevents the problem from holding up other team members’ tasks.

Other issues often faced in the legacy, path-based resources were order of operations and dependencies loading. To ensure materials were loaded before they were needed(as there was no way to associate materials to what used them), the game template would just scan all material.tscript files and bruteforce load everything ahead of time. This could lead to longer startup times, and could be an exploitable vulnerability, as well as often loading a ton of additional material into memory that wasn’t needed.

<figure><img src="https://lh5.googleusercontent.com/JCx5N6It94dZPJ6HGQVz0pzmUK8wD64LRQFNN9NzDoua9QX0-SuHqnBUJHs38nB0EOpPBE4qN8MMZ1m95XUdsH0rt0bIuJia9F-BXZieS63pHQ-kEILu1Vagsd3z0bf8v1ZKt_rVa_0NCsLo2AR7R1lW8T9YInZ84q5Ip49c33R5d-Fr04uYP03r" alt=""><figcaption></figcaption></figure>

It could also suffer from similar path unreliability issues if paths the materials relied on for image maps or the like were invalid due to misspellings, or being moved.

Assets, however, allow integrated dependency tracking. When an asset, such as a shape, is loaded, it has its own list of dependencies.

<figure><img src="https://lh4.googleusercontent.com/MXCy26ox9SD22qsTsvzvxdh3NvxXoQ5XrKPSHN-LhML77Tp_El5M6wNUbmJUZT72UUuFTV9qUPdlvB-zwRnhG6ftNnZFBStOlYsn5vM6LAXjPHGWKMKRSRiLFYYJRVHsqqK7qCC4hd82kau0NL0_mkjC91E13pgTAtaTfOQWcWMg9J17ZykowPqw" alt=""><figcaption></figcaption></figure>

Because asset loading is reference-based. Only assets that are actually called get loaded. When they go to load, it checks for any dependencies in the asset metadata, and loads them first. Those assets load in a similar way, continuing until the dependency chain is complete.

In the above example, the shapeAsset is loaded, but it relies on 2 material assets. It loads those, but those themselves have dependencies to image assets, so those are loaded. Once the entire dependency chain is loaded and valid, the shapeAsset is ready and passed back to the game object that wanted to use it. If anything goes wrong, each can provide a fallback placeholder to ensure things load correctly, while still indicating what and how it failed to provide more info for debugging.

Because assets’ loading is reference-based, when all the references are removed, such as when a level is unloaded, the asset can too be unloaded. This makes post-level cleanup easy, and goes a long way to ensure only memory and resources in use actually get consumed.
