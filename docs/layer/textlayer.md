# TextLayer object

`app.project.item(index).layer(index)`

#### Description

The TextLayer object represents a text layer within a composition. Create it using the [LayerCollection object's addText method](layercollection.md#layercollectionaddtext). It can be accessed in an item's layer collection either by index number or by a name string.

!!! info
    TextLayer is a subclass of [AVLayer](avlayer.md), which is a subclass of [Layer](layer.md). All methods and attributes of AVLayer and Layer are available when working with TextLayer.

#### AE Properties

TextLayer defines no additional attributes, but has the following AE properties and property groups, in addition to those inherited from AVLayer:

- `Text`
- `SourceText`
- `PathOptions`
- `Path`
- `ReversePath`
- `PerpendicularToPath`
- `ForceAlignment`
- `FirstMargin`
- `LastMargin`
- `MoreOptions`
- `AnchorPointGrouping`
- `GroupingAlignment`
- `Fill&Stroke`
- `InterCharacterBlending`
- `Animators`

## Attributes

### TextLayer.canAddOrRemoveMaterialOverride

`app.project.item(index).layer(index).canAddOrRemoveMaterialOverride`

!!! warning
    This functionality is in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

`true` if text layers support adding or removing their material overrides. This is a layer-type capability and does not check whether the layer is currently 3D or whether the composition uses the Advanced 3D renderer.

Text layers return `true` even when they are 2D or the composition uses another renderer. Material assignment access and override operations still fail until the layer is 3D in an Advanced 3D composition.

#### Type

Boolean; read-only.

---

### TextLayer.materialAssignment

`app.project.item(index).layer(index).materialAssignment`

!!! warning
    This functionality is in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

The layer's material assignment group. Material assignments are available when the text layer is 3D and the composition uses the Advanced 3D renderer. The front, bevel, side, and back assignments can be selected with `MaterialAssignment.FRONT`, `MaterialAssignment.BEVEL`, `MaterialAssignment.SIDE`, and `MaterialAssignment.BACK`.

Accessing this attribute on a 2D text layer, or in a Classic 3D or Cinema 4D composition, reports `Unable to find materials on this layer.`

Each assignment's [material properties](../property/materialpropertygroup.md#accessing-material-properties) depend on its source and projection mode. A default source exposes no intrinsic material properties or texture transforms; Substance and layer sources expose texture controls, and a layer source also exposes intrinsic overrides.

#### Type

[MaterialAssignmentPropertyGroup object](../property/materialassignmentpropertygroup.md); read-only.

---

### TextLayer.materialAssignmentCount

`app.project.item(index).layer(index).materialAssignmentCount`

!!! warning
    This functionality is in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

The total number of material assignments available on a 3D text layer in an Advanced 3D composition. The value is 4 for the front, bevel, side, and back assignments, including assignments whose override has not been added. This value is the same as `materialAssignment.numProperties`.

#### Type

Integer; read-only.

---

## Methods

### TextLayer.addAllMaterialOverrides()

`app.project.item(index).layer(index).addAllMaterialOverrides()`

!!! warning
    This functionality is in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

Adds every material override that is not already present, preserving existing material sources and property values.

This method reports an error if the layer has no available material state or if all overrides are already present. A 2D text layer, or one in a Classic 3D or Cinema 4D composition, reports `Unable to find materials on this layer.` If all overrides are already present, it reports `All material overrides have been added.`

#### Parameters

None.

#### Returns

Nothing.

---

#### Unused Properties and Attributes

The `TimeRemapandMotionTrackers` properties, inherited from AVLayer, are not applicable to text layers, and their related AVLayer attributes are not used:

- `canSetTimeRemapEnabled`
- `timeRemapEnabled`
- `trackMatteType`
- `isTrackMatte`
- `hasTrackMatte`
