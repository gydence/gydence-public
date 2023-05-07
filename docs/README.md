# Gydence

[Gydence](https://gydence.com) is a collaborative, online editor for building 3D and AR experiences.

Gydence is built on [three.js](https://threejs.org/), [A-FRAME](https://aframe.io/), and [supabase](https://supabase.com/).

Gydence is currently in early alpha.


# Getting Started

When you first open the editor, you are prompted to create a new project. Projects have a few properties:

| Property    | Description |
| ----------- | ----------- |
| Name        | The name of your project.  This appears in the Project selection dropdown and as the title of the page when you visit it. |
| Editors     | Comma separated list of emails for accounts to which you'd like to give access to your project.  Editors can access your project and edit collaboratively.  Only the creator of a project can delete it. |
| Template    | [Templates](/templates) are starting points for your projects, including 2D UI, 3D content, scripts, apps, and assets.  [Templates](/templates) can be purchased from the [marketplace](/marketplace). |
| Environment | Environments are purely aesthetic surroundings for the editor.  They do not affect your published project.  Environments can be purchased from the [marketplace](/marketplace). |

After creating your project, you can edit any of its properties except for its template.  **Your project is not publicly viewable until you have chosen to publish it.**  At any point, you can choose to unlist your project.  If you are the creator of a project, you can also choose to delete it completely.


# Editor

The editor allows you to make changes your projects and use the marketplace.  Here is a diagram of the different parts of the editor:

![An annotated image of the editor.](/assets/editor.png)

| Number    | Description |
| --------- | ----------- |
| 1 | **Main menu.**  From here, you can create new [3D entities](/entities), add and edit [scripts](/scripts), [apps](/apps), and [assets](/assets), and visit or upload to the [marketplace](/marketplace). |
| 2 | **Scene graph.**  Choose or edit your current project or create a new one and bring up the property panel for the [scene](/scene), [2D UI](/overlay), or [3D entities](/entities). |
| 3 | **Property panel.**  The properties of the currently selected item.  For the [scene](/scene) and [entities](/entities), these are A-FRAME component properties.  For [2D UI](/overlay), [scripts](/scripts), [apps](/apps), and [assets](/assets), these can be code editors or more specific functions. |
| 4 | **Item list.**  When [scripts](/scripts), [apps](/apps), or [assets](/assets) is selected in the main menu, this panel lists all of the items of the selected type in use by your site or that you own.  You can add additional items of that type or delete them from your site. |
| 5 | **Preview / Publish.** Preview your site to see what it looks like to a visitor.  Publish your site to make it public.  Changes made in the editor, including to assets, do not appear publicly until you publish your project again. |
| 6 | **Info and Log out.**  Log out of the editor.  If multiple people are editing at the same time, hover over the count to see their emails. |
| 7 | **Preview**.  The core of the editor, previewing all of the 2D + 3D content in your project. |
| 8 | **Selection**.  The selected 3D [entity](/entities) will be outlined. |


## Controls

Default controls for the editor:

| Key    | Behavior    |
| ------ | ----------- |
| W | Move forward. |
| A | Move left. |
| S | Move backwards. |
| D | Move right. |
| Z | Move up. |
| X | Move down. |
| Q | Turn left. |
| E | Turn right. |
| C | Turn up. |
| V | Turn down. |
| Shift | Hold to slow down movements. |
| Ctrl | Hold to interact with 2D content while in the editor.  By default, pointer events on the [2D UI](/overlay) are disabled - unless explicitly enabled in your [2D UI](/overlay) - while editing to allow you to interact with the 3D content. |
| 1 | First person mode. |
| 2 | Third person mode. |
| Click | Click on an [entity](/entities) to select it. |
| Click + Drag | Reposition the selected [entity](/entities) on the XZ plane. |
| Click + Shift + Drag | Reposition the selected [entity](/entities) on the Y axis. |
| Ctrl + Z | Undo. |
| Ctrl + Shift + Z | Redo. |
| Ctrl + C | Copy the selected object's properties (e.g. the [scene](/scene), [2D UI](/overlay), or an [entity](/entities), [script](/script), or [app](/app)). |
| Ctrl + V | Duplicate the previously copied object.  If the previously selected object was a [scene](/scene), its properties will be applied to the current [scene](/scene).  If the previously selected object was the [2D UI](/overlay), it will overwrite the current [2D UI](/overlay). |
| Ctrl + Shift + V | Same as the above, but if the previously selected object was an [entity](/entities), and the currently selected object is an [entity](/entities), the newly created [entity](/entities) will be a child of the currently selected [entity](/entities). |
| Click + P | Make the newly selected [entity](/entities) a child of the newly selected [entity](/entities). |
| Delete | Delete the currently selected object. |


# Next Steps

Now that you've got a project set up, add some content!  Check out more information on the different elements you can use:

- [Templates](/templates)
- [Scene properties](/scene)
- [2D UI](/overlay)
- [3D Entities](/entities)
- [Scripts](/scripts)
- [Apps](/apps)
- [Assets](/assets)
- The [scripting API](/api)

And learn about the [marketplace](/marketplace) or check out some [examples](/examples).