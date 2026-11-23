# MaterialPropertyGroup object

`app.project.item(index).layer(index).materialAssignment.property(index)`

!!! note
    This functionality was added in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

The MaterialPropertyGroup object represents one material assignment on a material-capable layer. It provides access to the material properties and to the assignment's source and override state.

!!! info
    MaterialPropertyGroup is a subclass of [PropertyGroup object](propertygroup.md). All PropertyGroup methods and attributes are available on a MaterialPropertyGroup.

!!! warning
    `materialSource` is read-only. Use `setMaterialOverride()` to assign or reset the source.

## Accessing material properties

Access a material property directly on the material assignment, such as `material.roughness`, or look it up by name, such as `material.property("Roughness")`. Both forms return a [Property object](property.md). Read its current value with `.value` and change it with `.setValue()`.

The available properties depend on the receiving layer type, the assignment's material source, and the selected projection mode. An unavailable property returns `undefined` through shorthand access, or `null` through `property("Name")`.

You can also use a 1-based index, such as `material.property(1)`. Indexed traversal can return hidden properties, so a returned Property object does not guarantee that it can be edited. Setting a value on a hidden property, or on a property whose parent group is hidden, reports an error.

See [MaterialAssignmentPropertyGroup availability](materialassignmentpropertygroup.md#availability) for the layer, renderer, and override requirements. The material-property entries below describe availability on an added override.

- **Default source:** `materialSource === null`.
- **Substance source:** A Substance material FootageItem.
- **Layer source:** An eligible AVLayer used as the material source, not the receiving layer.

### Example

```javascript
var material = textLayer.materialAssignment.property(MaterialAssignment.FRONT);

material.setMaterialOverride(sourceLayer);
material = textLayer.materialAssignment.property(MaterialAssignment.FRONT);

if (material.roughness) {
    material.roughness.setValue(50);
}

var textureOffset = material.property("Texture Offset");
if (textureOffset) {
    textureOffset.setValue([0.25, 0.5]);
}
```

After changing the material source, retrieve the `MaterialPropertyGroup` again before accessing its properties because the available property set can change.

---

## Material properties

### MaterialPropertyGroup.ambient

`app.project.item(index).layer(index).materialAssignment.property(index).ambient`

#### Description

The material's response to ambient lighting.

#### Availability

- ParametricMeshLayer: available with a default or layer source.
- ThreeDModelLayer, TextLayer, and ShapeLayer: available with a layer source only.

Unavailable with a Substance source.

#### Type

[Property object](property.md) with a numeric percentage value.

---

### MaterialPropertyGroup.baseColor

`app.project.item(index).layer(index).materialAssignment.property(index).baseColor`

#### Description

The base color of the default parametric mesh material.

#### Availability

Available only on a ParametricMeshLayer with a default source. Unavailable on imported models, text layers, and shape layers.

Unavailable with a Substance or layer source. A layer source supplies its color through its rendered pixels.

#### Type

[Property object](property.md) with a four-component color value, `[red, green, blue, alpha]`.

---

### MaterialPropertyGroup.blendSoftness

`app.project.item(index).layer(index).materialAssignment.property(index).blendSoftness`

#### Description

The softness of the transitions between the projected textures in Triplanar projection.

#### Availability

Available on any supported receiving layer with a Substance or layer source, when Triplanar projection is selected for the assignment.

Unavailable with a default source or in other projection modes.

#### Type

[Property object](property.md) with a numeric percentage value in the range `[0..100]`.

---

### MaterialPropertyGroup.emissionColor

`app.project.item(index).layer(index).materialAssignment.property(index).emissionColor`

#### Description

The color of the light emitted by the material.

#### Availability

- ParametricMeshLayer: available with a default or layer source.
- ThreeDModelLayer, TextLayer, and ShapeLayer: available with a layer source only.

Unavailable with a Substance source.

#### Type

[Property object](property.md) with a four-component color value, `[red, green, blue, alpha]`.

---

### MaterialPropertyGroup.emissionIntensity

`app.project.item(index).layer(index).materialAssignment.property(index).emissionIntensity`

#### Description

The intensity of the material's emission.

#### Availability

- ParametricMeshLayer: available with a default or layer source.
- ThreeDModelLayer, TextLayer, and ShapeLayer: available with a layer source only.

Unavailable with a Substance source.

#### Type

[Property object](property.md) with a numeric percentage value.

---

### MaterialPropertyGroup.metallic

`app.project.item(index).layer(index).materialAssignment.property(index).metallic`

#### Description

The metallic appearance of the material.

#### Availability

- ParametricMeshLayer: available with a default or layer source.
- ThreeDModelLayer, TextLayer, and ShapeLayer: available with a layer source only.

Unavailable with a Substance source.

#### Type

[Property object](property.md) with a numeric percentage value.

---

### MaterialPropertyGroup.opacity

`app.project.item(index).layer(index).materialAssignment.property(index).opacity`

#### Description

The opacity of the material supplied by a source layer.

#### Availability

Available on any supported receiving layer with a layer source. Unavailable with default and Substance sources.

#### Type

[Property object](property.md) with a numeric percentage value.

---

### MaterialPropertyGroup.projectionMode

`app.project.item(index).layer(index).materialAssignment.property(index).projectionMode`

#### Description

The texture projection mode for the material assignment.

#### Availability

Available on any supported receiving layer with a Substance or layer source.

Unavailable with a default source on every receiving layer type.

#### Type

[Property object](property.md) with a numeric popup value. The choices depend on the receiving layer:

| Receiving layer | Values |
| --- | --- |
| ParametricMeshLayer | `1` = Proportional; `2` = Stretch; `3` = Triplanar. |
| ThreeDModelLayer, TextLayer, ShapeLayer | `1` = Default UV; `2` = Triplanar. |

---

### MaterialPropertyGroup.randomizeOffset

`app.project.item(index).layer(index).materialAssignment.property(index).randomizeOffset`

#### Description

Enables per-letter or per-shape variation in the texture offset.

#### Availability

Available on 3D text and shape layers with a Substance or layer source.

Unavailable with a default source, and on parametric meshes and imported models.

#### Type

[Property object](property.md) with a numeric checkbox value: `0` for off, `1` for on.

---

### MaterialPropertyGroup.randomizeOffsetSeed

`app.project.item(index).layer(index).materialAssignment.property(index).randomizeOffsetSeed`

#### Description

The seed used to generate the randomized texture offsets.

#### Availability

Available on 3D text and shape layers with a Substance or layer source. The property remains accessible when `randomizeOffset` is off.

Unavailable with a default source, and on parametric meshes and imported models.

#### Type

[Property object](property.md) with a numeric value in the range `[0..99999]`.

---

### MaterialPropertyGroup.roughness

`app.project.item(index).layer(index).materialAssignment.property(index).roughness`

#### Description

The roughness of the material's surface.

#### Availability

- ParametricMeshLayer: available with a default or layer source.
- ThreeDModelLayer, TextLayer, and ShapeLayer: available with a layer source only.

Unavailable with a Substance source.

#### Type

[Property object](property.md) with a numeric percentage value.

---

### MaterialPropertyGroup.textureOffset

`app.project.item(index).layer(index).materialAssignment.property(index).textureOffset`

#### Description

The horizontal and vertical offset of the material's texture.

#### Availability

- ThreeDModelLayer: available with any source, including the default source.
- ParametricMeshLayer, TextLayer, and ShapeLayer: available with a Substance or layer source; unavailable with a default source.

#### Type

[Property object](property.md) with a two-number array value.

---

### MaterialPropertyGroup.textureRotation

`app.project.item(index).layer(index).materialAssignment.property(index).textureRotation`

#### Description

The rotation of the material's texture.

#### Availability

- ThreeDModelLayer: available with any source, including the default source.
- ParametricMeshLayer, TextLayer, and ShapeLayer: available with a Substance or layer source; unavailable with a default source.

#### Type

[Property object](property.md) with a numeric rotation value in degrees.

---

### MaterialPropertyGroup.textureScale

`app.project.item(index).layer(index).materialAssignment.property(index).textureScale`

#### Description

The horizontal and vertical scale of the material's texture.

#### Availability

- ThreeDModelLayer: available with any source, including the default source.
- ParametricMeshLayer, TextLayer, and ShapeLayer: available with a Substance or layer source; unavailable with a default source.

#### Type

[Property object](property.md) with a two-number array value.

---

### MaterialPropertyGroup.uniformTiling

`app.project.item(index).layer(index).materialAssignment.property(index).uniformTiling`

#### Description

Controls whether texture tiling uses a shared bounding box or the local bounds of each shape.

#### Availability

Available on 3D text and shape layers with a Substance or layer source, except when Triplanar projection is selected.

Unavailable with a default source, and on parametric meshes and imported models.

#### Type

[Property object](property.md) with a numeric checkbox value: `0` for off, `1` for on.

---

## Attributes

### MaterialPropertyGroup.isOverride

`app.project.item(index).layer(index).materialAssignment.property(index).isOverride`

!!! warning
    This functionality is in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

`true` if the material override has been added for this assignment; otherwise `false`.

Some layers, such as parametric meshes and single-material 3D models, always have their material override present. On text, shape, and multi-material 3D model layers, an override can be added or removed when the layer reports `canAddOrRemoveMaterialOverride` as `true`.

#### Type

Boolean; read-only.

---

### MaterialPropertyGroup.materialSource

`app.project.item(index).layer(index).materialAssignment.property(index).materialSource`

!!! warning
    This functionality is in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

The source currently assigned to the material. The value is:

- A [FootageItem object](../item/footageitem.md) whose footage is a Substance material.
- An eligible visual [AVLayer object](../layer/avlayer.md) from the same composition. The layer can be 2D.
- `null` when the assignment uses its default material.

The following layers are ineligible as material sources:

- The layer receiving the material assignment.
- A layer in another composition.
- A null layer.
- An adjustment layer.
- An imported 3D model layer.
- A ParametricMeshLayer.
- An audio-only layer.
- A layer whose layer or source name is empty.
- A layer that depends on the target layer and would create a circular material dependency.

CameraLayer and LightLayer objects are also ineligible because they are not AVLayer objects. A source layer must be a visual AVLayer and can be 2D.

An unadded material override is readable and returns `null`.

#### Type

FootageItem object, AVLayer object, or `null`; read-only.

---

## Methods

### MaterialPropertyGroup.removeMaterialOverride()

`app.project.item(index).layer(index).materialAssignment.property(index).removeMaterialOverride()`

!!! warning
    This functionality is in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

Removes the material override and resets its source, property values, keyframes, and expressions to the layer's default material state.

This method reports an error when the layer's material override is always present or when this assignment has no override to remove. Use the layer's `canAddOrRemoveMaterialOverride` and the assignment's `isOverride` attributes before calling it.

#### Parameters

None.

#### Returns

Nothing.

---

### MaterialPropertyGroup.setMaterialOverride()

`app.project.item(index).layer(index).materialAssignment.property(index).setMaterialOverride([materialSource])`

!!! warning
    This functionality is in After Effects (Beta) 27.1 and is subject to change while it remains in Beta.

#### Description

Adds the material override if necessary, then assigns the supplied material source. Passing no argument or `null` adds or updates the override with the default material. The override remains added after resetting its source to the default.

An item source must be a Substance material item. Assigning the same source again is allowed.

A layer source must be a suitable visual AVLayer with a nonempty name in the same composition. It may be a 2D layer. See [materialSource](#materialpropertygroupmaterialsource) for the complete list of ineligible layer types and references.

An invalid source is rejected before the material override is added or changed.

#### Parameters

| Parameter        | Type                            | Description                                                                                 |
| ---------------- | ------------------------------- | ------------------------------------------------------------------------------------------- |
| `materialSource` | Substance FootageItem object or AVLayer object | Optional material source. If omitted or `null`, the default material is selected. |

#### Returns

Nothing.

---
