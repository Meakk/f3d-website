## namespace `F3DUtils` {#namespaceF3DUtils}

### Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public VTKEXT_EXPORT double `[`ParseToDouble`](#F3DUtils_8h_1a1f3f6d785aab63015203d8a2deb62df5)`(const std::string & str,double def,const std::string & nameError)`            | 
`public VTKEXT_EXPORT int `[`ParseToInt`](#F3DUtils_8h_1aa80ae10ed644843e29f6929be254c33b)`(const std::string & str,int def,const std::string & nameError)`            | 

### Members

#### `public VTKEXT_EXPORT double `[`ParseToDouble`](#F3DUtils_8h_1a1f3f6d785aab63015203d8a2deb62df5)`(const std::string & str,double def,const std::string & nameError)` {#F3DUtils_8h_1a1f3f6d785aab63015203d8a2deb62df5}

#### `public VTKEXT_EXPORT int `[`ParseToInt`](#F3DUtils_8h_1aa80ae10ed644843e29f6929be254c33b)`(const std::string & str,int def,const std::string & nameError)` {#F3DUtils_8h_1aa80ae10ed644843e29f6929be254c33b}

## class `vtkF3DBitonicSort` {#classvtkF3DBitonicSort}

```
class vtkF3DBitonicSort
  : public vtkObject
```

Compute shader used to sort key/value pairs.

This class is used to sort buffers based on the Bitonic Sort algorithm. Inspired by [https://poniesandlight.co.uk/reflect/bitonic_merge_sort/](https://poniesandlight.co.uk/reflect/bitonic_merge_sort/) The original code can be found there: [https://github.com/tgfrerer/island](https://github.com/tgfrerer/island) It's mostly rewritten but some parts are copied (MIT license, Tim Gfrerer)

### Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`vtkTypeMacro`](#classvtkF3DBitonicSort_1ac7d33117c6ed24db9e11a926fa6f0da7)`(`[`vtkF3DBitonicSort`](#classvtkF3DBitonicSort)`,vtkObject)` | 
`public bool `[`Initialize`](#classvtkF3DBitonicSort_1a16c2b14d63d94a27412b3edb0f4a89e8)`(int workgroupSize,int keyType,int valueType)` | Initialize the compute shaders. workgroupSize is the number of threads running in a single GPU workgroup keyType and valueType are the VTK types of the key and value to sort respectively Only VTK_DOUBLE, VTK_FLOAT, VTK_INT and VTK_UNSIGNED_INT are supported Returns true if succeeded
`public bool `[`Run`](#classvtkF3DBitonicSort_1aab9ad18a9dc9dad0848d64a2e9b982d9)`(vtkOpenGLRenderWindow * context,int nbPairs,vtkOpenGLBufferObject * keys,vtkOpenGLBufferObject * values)` | Run the compute shader and sort the buffers. An OpenGL context must exists and given as input in the first argument nbPairs is the number of element in the buffer keys and values OpenGL buffers keys and values must be valid and containing data types specified when this class has been initialized Returns true if succeeded

### Members

#### `public  `[`vtkTypeMacro`](#classvtkF3DBitonicSort_1ac7d33117c6ed24db9e11a926fa6f0da7)`(`[`vtkF3DBitonicSort`](#classvtkF3DBitonicSort)`,vtkObject)` {#classvtkF3DBitonicSort_1ac7d33117c6ed24db9e11a926fa6f0da7}

#### `public bool `[`Initialize`](#classvtkF3DBitonicSort_1a16c2b14d63d94a27412b3edb0f4a89e8)`(int workgroupSize,int keyType,int valueType)` {#classvtkF3DBitonicSort_1a16c2b14d63d94a27412b3edb0f4a89e8}

Initialize the compute shaders. workgroupSize is the number of threads running in a single GPU workgroup keyType and valueType are the VTK types of the key and value to sort respectively Only VTK_DOUBLE, VTK_FLOAT, VTK_INT and VTK_UNSIGNED_INT are supported Returns true if succeeded

#### `public bool `[`Run`](#classvtkF3DBitonicSort_1aab9ad18a9dc9dad0848d64a2e9b982d9)`(vtkOpenGLRenderWindow * context,int nbPairs,vtkOpenGLBufferObject * keys,vtkOpenGLBufferObject * values)` {#classvtkF3DBitonicSort_1aab9ad18a9dc9dad0848d64a2e9b982d9}

Run the compute shader and sort the buffers. An OpenGL context must exists and given as input in the first argument nbPairs is the number of element in the buffer keys and values OpenGL buffers keys and values must be valid and containing data types specified when this class has been initialized Returns true if succeeded

## class `vtkF3DFaceVaryingPointDispatcher` {#classvtkF3DFaceVaryingPointDispatcher}

```
class vtkF3DFaceVaryingPointDispatcher
  : public vtkPolyDataAlgorithm
```

dispatch face-varying attributes by duplicating points.

This filter processes arrays on point data in case some of them are flagged as face-varying in which case points must be duplicated before rendering

Face-varying attributes are a special case between point and cell data where the number of tuples in the attributes is equal to the cell connectivity array size. For example, if we have two adjacent quads, we will have 6 points and 8 cell indices (4 per quad) Face-varying attributes, even if located on point data will have 8 tuples, and not 6 It can be seen as attributes, but this filter will normalize it by outputting 8 points.

### Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`vtkTypeMacro`](#classvtkF3DFaceVaryingPointDispatcher_1a91d5a06042aa2ffe4e5659a762c94a06)`(`[`vtkF3DFaceVaryingPointDispatcher`](#classvtkF3DFaceVaryingPointDispatcher)`,vtkPolyDataAlgorithm)` | 
`protected  `[`vtkF3DFaceVaryingPointDispatcher`](#classvtkF3DFaceVaryingPointDispatcher_1ac6c58598dd120e26d9f89e8cae1f47f8)`()` | 
`protected  `[`~vtkF3DFaceVaryingPointDispatcher`](#classvtkF3DFaceVaryingPointDispatcher_1a2cec14ec93fc87d03e21823ab42e90a5)`()` | 
`protected int `[`RequestData`](#classvtkF3DFaceVaryingPointDispatcher_1ace7ef1e416f2d4f6808df00d68ead236)`(vtkInformation *,vtkInformationVector **,vtkInformationVector *)` | 

### Members

#### `public  `[`vtkTypeMacro`](#classvtkF3DFaceVaryingPointDispatcher_1a91d5a06042aa2ffe4e5659a762c94a06)`(`[`vtkF3DFaceVaryingPointDispatcher`](#classvtkF3DFaceVaryingPointDispatcher)`,vtkPolyDataAlgorithm)` {#classvtkF3DFaceVaryingPointDispatcher_1a91d5a06042aa2ffe4e5659a762c94a06}

#### `protected  `[`vtkF3DFaceVaryingPointDispatcher`](#classvtkF3DFaceVaryingPointDispatcher_1ac6c58598dd120e26d9f89e8cae1f47f8)`()` {#classvtkF3DFaceVaryingPointDispatcher_1ac6c58598dd120e26d9f89e8cae1f47f8}

#### `protected  `[`~vtkF3DFaceVaryingPointDispatcher`](#classvtkF3DFaceVaryingPointDispatcher_1a2cec14ec93fc87d03e21823ab42e90a5)`()` {#classvtkF3DFaceVaryingPointDispatcher_1a2cec14ec93fc87d03e21823ab42e90a5}

#### `protected int `[`RequestData`](#classvtkF3DFaceVaryingPointDispatcher_1ace7ef1e416f2d4f6808df00d68ead236)`(vtkInformation *,vtkInformationVector **,vtkInformationVector *)` {#classvtkF3DFaceVaryingPointDispatcher_1ace7ef1e416f2d4f6808df00d68ead236}

## class `vtkF3DGLTFImporter` {#classvtkF3DGLTFImporter}

```
class vtkF3DGLTFImporter
  : public vtkGLTFImporter
```

VTK GLTF importer customization.

Subclasses the native importer to modify the armature shader.

### Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`vtkTypeMacro`](#classvtkF3DGLTFImporter_1aee9cf8a568f96d9a75b8b671939f5bf6)`(`[`vtkF3DGLTFImporter`](#classvtkF3DGLTFImporter)`,vtkGLTFImporter)` | 
`protected  `[`vtkF3DGLTFImporter`](#classvtkF3DGLTFImporter_1a54e3b368c94cd53d998e366b972c8b64)`()` | 
`protected  `[`~vtkF3DGLTFImporter`](#classvtkF3DGLTFImporter_1a9430898ee2d26ca17ff98384fff8a5c2)`() = default` | 
`protected void `[`ApplyArmatureProperties`](#classvtkF3DGLTFImporter_1ac1919590316b268949ca15d94a47a007)`(vtkActor * actor)` | This method is reimplemented to add information to the actor in order to properly draw armatures on top.

### Members

#### `public  `[`vtkTypeMacro`](#classvtkF3DGLTFImporter_1aee9cf8a568f96d9a75b8b671939f5bf6)`(`[`vtkF3DGLTFImporter`](#classvtkF3DGLTFImporter)`,vtkGLTFImporter)` {#classvtkF3DGLTFImporter_1aee9cf8a568f96d9a75b8b671939f5bf6}

#### `protected  `[`vtkF3DGLTFImporter`](#classvtkF3DGLTFImporter_1a54e3b368c94cd53d998e366b972c8b64)`()` {#classvtkF3DGLTFImporter_1a54e3b368c94cd53d998e366b972c8b64}

#### `protected  `[`~vtkF3DGLTFImporter`](#classvtkF3DGLTFImporter_1a9430898ee2d26ca17ff98384fff8a5c2)`() = default` {#classvtkF3DGLTFImporter_1a9430898ee2d26ca17ff98384fff8a5c2}

#### `protected void `[`ApplyArmatureProperties`](#classvtkF3DGLTFImporter_1ac1919590316b268949ca15d94a47a007)`(vtkActor * actor)` {#classvtkF3DGLTFImporter_1ac1919590316b268949ca15d94a47a007}

This method is reimplemented to add information to the actor in order to properly draw armatures on top.

## class `vtkF3DImporter` {#classvtkF3DImporter}

```
class vtkF3DImporter
  : public vtkImporter
```

Generic importer for F3D.

This generic importer is provided to simplify implementation of other importers and handle multiple versions of VTK.

### Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool `[`UpdateAtTimeValue`](#classvtkF3DImporter_1afa7f0fc1608a37a57e9a2f21fcba400d)`(double timeValue)` | This method should be reimplemented in importer implementations to handle update the importer at a specific time value then call this method and return what it returns.
`public void `[`SetFailureStatus`](#classvtkF3DImporter_1acd5c322fbe7f72589db10fc2fcfc8ea4)`()` | Call this method to set the status to failure if supported by the VTK version in use

### Members

#### `public bool `[`UpdateAtTimeValue`](#classvtkF3DImporter_1afa7f0fc1608a37a57e9a2f21fcba400d)`(double timeValue)` {#classvtkF3DImporter_1afa7f0fc1608a37a57e9a2f21fcba400d}

This method should be reimplemented in importer implementations to handle update the importer at a specific time value then call this method and return what it returns.

#### `public void `[`SetFailureStatus`](#classvtkF3DImporter_1acd5c322fbe7f72589db10fc2fcfc8ea4)`()` {#classvtkF3DImporter_1acd5c322fbe7f72589db10fc2fcfc8ea4}

Call this method to set the status to failure if supported by the VTK version in use

Generated by [Moxygen](https://sourcey.com/moxygen)