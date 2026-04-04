# ParametricMeshLayer object

`app.project.item(index).layer(index)`

!!! note
    This functionality was added in After Effects (Beta) 26.3 and is subject to change while it remains in Beta.

#### Description

The ParametricMeshLayer object represents a Parametric Mesh layer within a composition.

!!! info
	ParametricMeshLayer is a subclass of [AVLayer object](avlayer.md). All methods and attributes of AVLayer are available when working with ParametricMeshLayer.

#### Example

If the first item in the project is a CompItem, and the first layer of that CompItem is a ParametricMeshLayer, the following checks its type.

```javascript
var layer = app.project.item(1).layer(1);
if (layer instanceof ParametricMeshLayer)
{
    // do something
}
```

## Attributes

### ParametricMeshLayer.meshType

`app.project.item(index).layer(index).meshType`

!!! note
    This functionality was added in After Effects (Beta) 26.3 and is subject to change while it remains in Beta.

#### Description

For a parametric mesh layer, its mesh type. Trying to set this attribute for a non-parametric mesh layer produces an error.

#### Type

A `MeshType` enumerated value; read/write. One of:

- `MeshType.SPHERE`
- `MeshType.PLANE`
- `MeshType.CYLINDER`
- `MeshType.CONE`
- `MeshType.TORUS`
- `MeshType.CUBE`

---

### ParametricMeshLayer.meshOptions

`app.project.item(index).layer(index).meshOptions`

!!! note
    This functionality was added in After Effects (Beta) 26.3 and is subject to change while it remains in Beta.

#### Description

Gets/sets details about the structure of the parametric mesh.

#### Type

`MeshOptions` based on the MeshType of the layer, as follows.

#### For MeshType.CUBE
- `meshOptions.width`
- `meshOptions.height`
- `meshOptions.depth`
- `meshOptions.smoothingAngle`

#### For MeshType.SPHERE
- `meshOptions.radius`
- `meshOptions.sides`
- `meshOptions.sliceCaps`
- `meshOptions.sliceStart`
- `meshOptions.sliceEnd`
- `meshOptions.smoothingAngle`

#### For MeshType.PLANE
- `meshOptions.width`
- `meshOptions.length`
- `meshOptions.cornerRadius`
- `meshOptions.cornerSides`

####  For Meshtype.TORUS
- `meshOptions.ringRadius`
- `meshOptions.pipeRadius`
- `meshOptions.ringSides`
- `meshOptions.pipeSides`
- `meshOptions.caps`
- `meshOptions.sliceStart`
- `meshOptions.sliceEnd`
- `meshOptions.smoothingAngle`

####  For MeshType.CONE
- `meshOptions.topRadius`
- `meshOptions.bottomRadius`
- `meshOptions.height`
- `meshOptions.sides`
- `meshOptions.topCap`
- `meshOptions.bottomCap`
- `meshOptions.sliceCaps`
- `meshOptions.sliceStart`
- `meshOptions.sliceEnd`
- `meshOptions.smoothingAngle`

#### For MeshType.CYLINDER
- `meshOptions.radius`
- `meshOptions.height`
- `meshOptions.sides`
- `meshOptions.topCap`
- `meshOptions.bottomCap`
- `meshOptions.sliceCaps`
- `meshOptions.sliceStart`
- `meshOptions.sliceEnd`
- `meshOptions.smoothingAngle`

---

### ParametricMeshLayer.bevelOptions

`app.project.item(index).layer(index).bevelOptions`

!!! note
    This functionality was added in After Effects (Beta) 26.3 and is subject to change while it remains in Beta.

#### Description

Gets/sets details about the beveling of the parametric mesh.

!!! info
	Only Parametric Mesh Layers with `MeshType.CUBE`, `MeshType.CONE`, and `MeshType.CYLINDER` have `bevelOptions`.

#### Type

`BevelOptions` based on the MeshType of the layer, as follows.

#### For MeshType.CUBE
- `bevelOptions.radius`
- `bevelOptions.sides`

#### For MeshType.CONE
- `bevelOptions.topRadius`
- `bevelOptions.topSides`
- `bevelOptions.bottomRadius`
- `bevelOptions.bottomSides`

#### For MeshType.CYLINDER
- `bevelOptions.radius`
- `bevelOptions.sides`

---

