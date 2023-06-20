# Scripting API

The JavaScript scripting API is available to developers in [scripts](/scripts) and [apps](/apps).  The API can be accessed via the global `GYDENCE` object.

Some functions are only accessible during editing, while others will also work on published projects.

Note: all variables are read-only.

# Public API

These variables and functions are always available.

#### isEditing

Value: `true` if this script is running inside of the editor, `false` otherwise.

#### currentSite

Value: The UUID of the current project.

#### publicSiteURL

Value: The public URL of the current project.

#### privateSiteURL

Value: The private URL of the current project.

#### assetURL

Value: The base URL for this project's assets.  This will point to the draft asset URL during editing and previewing, and the published asset URL on the public project.


# Editing API

These variables and functions are only available from within the editor (when `GYDENCE.isEditing` is `true`).

#### listAssets

Lists the draft assets for this project according to the provided `options`.  See the [supabase docs](https://supabase.com/docs/reference/javascript/storage-from-list) for more info.

| Parameter | Description |
| --------- | ----------- |
| options |  Optional.  The supabase `SearchOptions` to use. |

Returns: a `Promise` to a list of assets for this project, fetched according to `options`.

Note: by default, this may fail to return all assets if there are more than 100.  See `listAllAssets`.

#### listAllAssets

Lists all of the draft assets for this project.  See the [supabase docs](https://supabase.com/docs/reference/javascript/storage-from-list) for more info.

Returns: a `Promise` to a list of all assets for this project.

#### uploadAsset

Upload `asset` to your project's draft storage with the filename `name`, according to the provided `options`.  See the [supabase docs](https://supabase.com/docs/reference/javascript/storage-from-upload) for more info.

| Parameter | Description |
| --------- | ----------- |
| name | The desired filename, with no path. |
| asset |  The supabase `FileBody` to upload.  e.g. a `Blob`, `File`, `FormData`, or `ArrayBuffer`. |
| options |  Optional.  The supabase `FileOptions` to use. |

Returns: a `Promise` to the result of the upload.

#### renameAsset

Rename the asset with `oldName` to `newName` if it exists in your project's draft storage.  See the [supabase docs](https://supabase.com/docs/reference/javascript/storage-from-move) for more info.

| Parameter | Description |
| --------- | ----------- |
| oldName | The file to rename, with no path. |
| newName | The desired new file name, with no path. |

Returns: a `Promise` to the result of the rename.

#### deleteAssets

Delete all of the assets with names in `filenames` if they exist in your project's draft storage.  See the [supabase docs](https://supabase.com/docs/reference/javascript/storage-from-remove) for more info.

| Parameter | Description |
| --------- | ----------- |
| filenames | An array of file names, with no path, to delete. |

Returns: a `Promise` to the result of the removals.

#### scenePropertyMap

Value: an object where the keys are all of the components and systems on the [scene](/scene) and the values are their property values.  **Read-only**.

### getSceneProperty

Get the value of a [scene](/scene) component or system.

| Parameter | Description |
| --------- | ----------- |
| prop | The component or system to look up. |

Returns: the current value of the component or system with name `prop` if it exists on the [scene](/scene).

### editSceneProperty

Edit or remove a [scene](/scene) component or system.

| Parameter | Description |
| --------- | ----------- |
| prop | The component or system to modify. |
| value | The desired value for the component or system.  If `undefined`, the component/system will be removed. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the edit.

#### entityPropertyMap

Value: an object where the keys are all of the [entity](/entities) IDs and the values are objects where the keys are component names and the values are the property values.  **Read-only**.

### getEntityProperty

Get the value of a component for a specitic [entity](/entities).

| Parameter | Description |
| --------- | ----------- |
| entityID | The entity ID to look up. |
| prop | The component to look up. |

Returns: the current value of the component with name `prop` if it exists on the [entity](/entities) that matches `entityID`.

### addEntity

Add a new entity with the desired properties.

| Parameter | Description |
| --------- | ----------- |
| props | An object where the keys are all of the desired components and the values are their desired properties. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the add.

### addEntities

Adds multiple new entities with the desired properties.

| Parameter | Description |
| --------- | ----------- |
| propsArray | An array of objects where the keys are all of the desired components and the values are their desired properties for each separate entity. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the adds.

### editEntityProperty

Edit or remove a component on an [entity](/entities).

| Parameter | Description |
| --------- | ----------- |
| entityID | The ID of the entity to edit. |
| prop | The component to modify. |
| value | The desired value for the component.  If `undefined`, the component/system will be removed. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the edit.

### deleteEntity

Delete the desired entity.

| Parameter | Description |
| --------- | ----------- |
| entityID | The ID of the entity to delete. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the deletion.

#### overlayElements

Value: a string representation of all of the [2D UI](/overlay) HTML.  **Read-only**.

### getOverlayElements

Returns: the [2D UI](/overlay) HTML string.

### editOverlayElements

Edit the [2D UI](/overlay) HTML string.

| Parameter | Description |
| --------- | ----------- |
| value | The desired value for the [2D UI](/overlay) HTML, represented as a string. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the edit.

#### css

Value: a string representation of all of the [2D UI](/overlay) CSS.  **Read-only**.

### getCSS

Returns: the [2D UI](/overlay) CSS string.

### editCSS

Edit the [2D UI](/overlay) CSS string.

| Parameter | Description |
| --------- | ----------- |
| value | The desired value for the [2D UI](/overlay) CSS, represented as a string. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the edit.

#### scripts

Value: an array of all of the [scripts](/script).  Each entry includes properties like `id` and `name` among others.  **Read-only**.

### getScripts

Returns: the array of all [scripts](/script) with their properties.

### editScript

Edit a single property of a [script](/script).

| Parameter | Description |
| --------- | ----------- |
| scriptID | The ID of the script to edit. |
| prop | The property to modify. |
| value | The desired value for the property. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the edit.

#### apps

Value: an array of all of the [apps](/app).  Each entry includes properties like `id` and `name` among others.  **Read-only**.

### getApps

Returns: the array of all [apps](/app) with their properties.

### editApp

Edit a single property of a [app](/app).

| Parameter | Description |
| --------- | ----------- |
| appID | The ID of the app to edit. |
| prop | The property to modify. |
| value | The desired value for the property. |
| forceUpdate | **Optional, default = true**.  Whether or not to force a [local update](/?id=forceupdate). |

Returns: a `Promise` to the result of the edit.


# forceUpdate

Several API methods have an optional `forceUpdate` parameter.  When edits are made, they are transmitted to collaborators in real time and their views will reload as necessary.  However, sometimes you do not want to reload your own view immediately, as you may be in the middle of making several edits from a script.  In these cases, you can set `forceUpdate` to `false`, which will cause your own view to not update immediately.