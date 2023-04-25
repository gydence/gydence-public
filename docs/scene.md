# Scene

The scene is the container for all of the [3D content](/entities) of your project.  It corresponds to the singular `<a-scene>` element and has the `id` "scene".  More info can be found in the [`A-FRAME` documentation](https://aframe.io/docs/master/core/scene.html).

The scene property editor is very similar to the entity property editor.  You can add [components](https://aframe.io/docs/master/core/component.html) one by one and modify their sub-properties.  However, the scene has a reduced list of viable components, which also includes any `A-FRAME`-registered [systems](https://aframe.io/docs/master/core/systems.html).

If any scripts call `AFRAME.registerSystem` or `AFRAME.registerComponent` (with `isSceneComponent: true`), those will appear as options here.