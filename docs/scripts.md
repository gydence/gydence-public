# Scripts

Scripts define logic that runs when someone visits your site.  Scripts are written in JavaScript and have full access to the elements of your project using standard web APIs and the [Gydence scripting API](/api).

Clicking "Scripts" in the top menu will bring up the scripts list.  There are two ways to add scripts to your project.


## Add Scripts by URL

You can find many open source three.js, A-FRAME, and general JavaScript examples around the web.  Oftentimes, a useful A-FRAME component is distributed via npm with an option to include it via script tag.

For example, adding physics to your project via [aframe-physics-engine](https://github.com/c-frame/aframe-physics-system) is as simple as including these two URLs:

1. `https://cdn.jsdelivr.net/gh/MozillaReality/ammo.js@8bbc0ea/builds/ammo.wasm.js`
2. `https://cdn.jsdelivr.net/gh/c-frame/aframe-physics-system@v4.2.2/dist/aframe-physics-system.js`

This will give you access to new components like `ammo-shape`, `ammo-body`, and `ammo-constraint` as well as direct manipulation of physics bodies via Ammo.js.  See the [basic physics example](/examples/basic-physics) for more details on this example.


# Add Script Blocks

Whereas scripts included by URL are immutable, script blocks give you the freedom to edit executable logic and see the effects live.  By default, script blocks run in the global scope, so information can be shared between blocks and functions can be called from the 2D UI.

The editor automatically reloads when you make changes to a script block, re-executing all of your scripts from the beginning.  You can disable this by unchecking "Reload on Change?" from the top right of the script property panel, and you can manually reload at any time by pressing the "↻" button.


# Owned Scripts

- Scripts that you purchase from the [marketplace](/marketplace) will appear in the scripts list "Owned" tag.  These scripts will not run unless you explicitly add them to your desired project.

Marketplace scripts can be **public**, in which case you can modify their URL or block contents like normal scripts after adding them, or **private**, in which case you cannot view or edit their URL or contents.  This is set by the person who uploads the script to the marketplace.


# Notes

- Scripts are run in order, but URL scripts can execute at different times depending on their execution mode (e.g. [async](https://www.w3schools.com/tags/att_script_async.asp) or [deferred](https://www.w3schools.com/tags/att_script_defer.asp)).
- By default, changes to the [2D UI](/overlay) do not reload the editor, but they do recreate the DOM.  This means that if a script references an element (e.g. via `document.querySelector`) and caches the result, edits made to the 2D UI might render the cached element invalid.  In this case, you might want to enable "Reload on Change?" from the 2D UI property panel, or manually reload the editor after making changes.
- Most changes made via the [Gydence scripting API](/api) will not trigger a full reload of the editor.  For example, editing an entity property will not reload scripts.  However, `GYDENCE.editScript` will trigger a full reload, restarting all scripts.
- Like with normal web pages, scripts can run before the rest of the DOM is initialized.  You can listen for the [DOMContentLoaded](https://developer.mozilla.org/en-US/docs/Web/API/Window/DOMContentLoaded_event) event to know that everything else has been initialized.