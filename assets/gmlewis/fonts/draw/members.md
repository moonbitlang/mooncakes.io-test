# Documentation
|Trait|description|
|---|---|
|[@gmlewis/fonts/draw.Clonable](#@gmlewis/fonts/draw.Clonable)||

|Type|description|
|---|---|
|[AffineMatrix](#AffineMatrix)||
|[Anchor](#Anchor)||
|[BoundingBox](#BoundingBox)||
|[Color](#Color)||
|[CompoundPath](#CompoundPath)||
|[DrawError](#DrawError)||
|[Fill](#Fill)||
|[Graphic](#Graphic)||
|[Group](#Group)||
|[Path](#Path)||
|[Stroke](#Stroke)||
|[StrokeAlignment](#StrokeAlignment)||
|[StrokeCap](#StrokeCap)||
|[StrokeJoin](#StrokeJoin)||
|[TextAlign](#TextAlign)||
|[Transform](#Transform)||
|[Vec2](#Vec2)||

|Value|description|
|---|---|
|[affine\_transform](#affine_transform)||
|[affine\_transform\_without\_translation](#affine_transform_without_translation)||
|[all\_anchors](#all_anchors)||
|[almost\_equals](#almost_equals)||
|[area](#area)||
|[as\_fill](#as_fill)||
|[assign\_style](#assign_style)||
|[bbox](#bbox)||
|[boolean\_intersect](#boolean_intersect)||
|[bounding\_box](#bounding_box)||
|[canonicalize](#canonicalize)||
|[center](#center)||
|[clone](#clone)||
|[closest\_point](#closest_point)||
|[contains\_bounding\_box](#contains_bounding_box)||
|[contains\_point](#contains_point)||
|[copy](#copy)||
|[determinant](#determinant)||
|[expand\_scalar](#expand_scalar)||
|[expand\_to\_include\_bounding\_box](#expand_to_include_bounding_box)||
|[expand\_to\_include\_point](#expand_to_include_point)||
|[fill](#fill)||
|[group](#group)||
|[has\_tangent\_handles](#has_tangent_handles)||
|[has\_zero\_handles](#has_zero_handles)||
|[height](#height)||
|[invert](#invert)||
|[is\_contained\_by\_bounding\_box](#is_contained_by_bounding_box)||
|[is\_identity](#is_identity)||
|[is\_inf](#is_inf)||
|[is\_intersected\_by\_bounding\_box](#is_intersected_by_bounding_box)||
|[is\_invertible](#is_invertible)||
|[is\_mirror](#is_mirror)||
|[is\_nan](#is_nan)||
|[is\_orthogonal](#is_orthogonal)||
|[is\_overlapped\_by\_bounding\_box](#is_overlapped_by_bounding_box)||
|[is\_uniform\_scale](#is_uniform_scale)||
|[loose\_bounding\_box](#loose_bounding_box)||
|[luminance](#luminance)||
|[mix](#mix)||
|[mul](#mul)||
|[mul\_without\_translation](#mul_without_translation)||
|[normalize](#normalize)||
|[op\_mul](#op_mul)||
|[origin](#origin)||
|[overlaps\_bounding\_box](#overlaps_bounding_box)||
|[pre\_mul](#pre_mul)||
|[pre\_mul\_without\_translation](#pre_mul_without_translation)||
|[reverse](#reverse)||
|[rgba](#rgba)||
|[rotate](#rotate)||
|[scale](#scale)||
|[scale\_scalar](#scale_scalar)||
|[set](#set)||
|[size](#size)||
|[skew](#skew)||
|[stroke](#stroke)||
|[text](#text)||
|[to\_css\_hex\_string](#to_css_hex_string)||
|[to\_css\_rgba\_string](#to_css_rgba_string)||
|[to\_css\_string](#to_css_string)||
|[to\_hsva](#to_hsva)||
|[to\_rgb8\_number](#to_rgb8_number)||
|[to\_transform](#to_transform)||
|[transform](#transform)||
|[translate](#translate)||
|[unit\_circle](#unit_circle)||
|[unit\_square](#unit_square)||
|[vec2](#vec2)||
|[width](#width)||

## @gmlewis/fonts/draw.Clonable

```moonbit
:::source,gmlewis/fonts/draw/path.mbt,52:::pub(open) trait @gmlewis/fonts/draw.Clonable {
  clone(Self) -> Self
}
```


## AffineMatrix

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,7:::pub(all) struct AffineMatrix {
  a : Double
  b : Double
  c : Double
  d : Double
  tx : Double
  ty : Double
}
```

 AffineMatrix represents a 2D affine transform that preserves parallel lines.
See: https://en.wikipedia.org/wiki/Affine\_transformation

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,14:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/affine-matrix.mbt,14:::fn op_equal(<a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,14:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/affine-matrix.mbt,14:::fn output(<a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,97:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::clone(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  clone returns a copy of this 2D affine matrix.
- #### copy
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,104:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::copy(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, other : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  copy copies another 2D affine matrix into itself and returns itself.
- #### determinant
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,274:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::determinant(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Double
  ```
  > 
  >  determinant returns the determinant of the 2D affine matrix.
- #### from\_center\_scale
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,82:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::from_center_scale(center : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, scale : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  AffineMatrix::from\_center\_scale returns a new 2D affine matrix that scales
  > from the provided center point.
- #### from\_rotation
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,60:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::from_rotation(angle : Double) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  AffineMatrix::from\_rotation returns a new 2D affine matrix from a rotation `angle`
  > in degrees.
- #### from\_scale
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,69:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::from_scale(v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  AffineMatrix::from\_scale returns a new 2D affine matrix from scale `v`.
- #### from\_scale\_scalar
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,75:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::from_scale_scalar(s : Double) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  AffineMatrix::from\_scale\_scalar returns a new 2D affine matrix from uniform scale `s`.
- #### from\_transform
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,31:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::from_transform(transform : <a href="gmlewis/fonts/draw#Transform">Transform</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  AffineMatrix::from\_transform returns a new 2D affine matrix from a Transform.
- #### from\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,43:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::from_translation(v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  AffineMatrix::from\_translation returns a new 2D affine matrix from translation `v`.
- #### from\_translation\_points
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,50:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::from_translation_points(p1 : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, p2 : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  AffineMatrix::from\_translation\_points returns a new 2D affine matrix that
  > translates from p1 to p2.
- #### invert
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,116:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::invert(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  invert inverts this 2D affine matrix.
- #### is\_identity
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,315:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::is_identity(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
  ```
  > 
  >  is\_identity returns true if this 2D affine matrix is the identity matrix.
- #### is\_inf
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,337:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::is_inf(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
  ```
  > 
  >  is\_inf returns true if any elements of this 2D affine matrix are infinite.
- #### is\_invertible
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,292:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::is_invertible(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
  ```
  > 
  >  is\_invertible returns true if this 2D affine matrix is invertible.
- #### is\_mirror
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,309:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::is_mirror(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
  ```
  > 
  >  is\_mirror returns true if this 2D affine matrix mirrors either axis.
- #### is\_nan
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,326:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::is_nan(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
  ```
  > 
  >  is\_nan returns true if any elements of this 2D affine matrix are NaN (not a number).
- #### is\_orthogonal
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,282:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::is_orthogonal(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, tolerance~ : Double = ..) -> Bool
  ```
  > 
  >  is\_orthogonal returns true if the two basis vectors of the 2D affine matrix
  > are orthogonal within the provided tolerance.
- #### is\_uniform\_scale
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,299:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::is_uniform_scale(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, tolerance~ : Double = ..) -> Bool
  ```
  > 
  >  is\_uniform\_scale returns true if both basis vectors of this 2D affine matrix
  > are of the same length.
- #### mul
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,131:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::mul(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, m : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  mul multiplies this 2D affine matrix with another.
- #### mul\_without\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,153:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::mul_without_translation(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, m : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  mul\_without\_translation multiplies this 2D affine matrix with another,
  > discarding the transation.
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,18:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::new(a~ : Double = .., b~ : Double = .., c~ : Double = .., d~ : Double = .., tx~ : Double = .., ty~ : Double = ..) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  AffineMatrix::new returns a new 2D affine matrix.
- #### normalize
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,255:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::normalize(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  normalize scales the basis vectors of this 2D affine matrix
  > so that they have unit length.
- #### op\_mul
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,145:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::op_mul(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, b : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  op\_mul multiplies two 2D affine matrices together, returning a new one.
- #### origin
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,245:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::origin(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  origin translates the matrix such that the center of future
  > scale, rotate, and skew transformations will be `v`.
- #### pre\_mul
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,169:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::pre_mul(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, m : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  pre\_mul multiplies another matrix `m` by this 2D affine matrix, then
  > stores and returns the result.
- #### pre\_mul\_without\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,184:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::pre_mul_without_translation(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, m : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  pre\_mul\_without\_translation multiplies another matrix `m` by this 2D affine matrix,
  > discarding the translate, then stores and returns the result.
- #### rotate
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,208:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::rotate(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, angle : Double) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  rotate rotates this 2D affine matrix by `angle` degrees.
- #### scale
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,224:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::scale(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  scale scales this 2D affine matrix by `v`.
- #### scale\_scalar
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,234:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::scale_scalar(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, s : Double) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  scale\_scalar scales this 2D affine matrix uniformly by `s`.
- #### skew
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,214:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::skew(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, angle : Double) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  skew skews the Y basis vector of this 2D affine matrix by `angle` degrees.
- #### to\_transform
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,362:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::to_transform(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Transform">Transform</a>
  ```
  > 
  >  to\_transform converts this 2D affine matrix to a Transform.
- #### translate
  ```moonbit
  :::source,gmlewis/fonts/draw/affine-matrix.mbt,199:::fn <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>::translate(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
  ```
  > 
  >  translate translates this 2D affine matrix by position `v`.

## Anchor

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,4:::pub(all) struct Anchor {
  position : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  handle_in : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  handle_out : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
}
```

 Anchor represents a single point in a path. Two anchors form a segment.
The position of an Anchor is absolute and the handles are both relative.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,8:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/anchor.mbt,8:::fn op_equal(<a href="gmlewis/fonts/draw#Anchor">Anchor</a>, <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,8:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/anchor.mbt,8:::fn output(<a href="gmlewis/fonts/draw#Anchor">Anchor</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,8:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/anchor.mbt,8:::fn to_json(<a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,8:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/anchor.mbt,8:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### affine\_transform
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,33:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::affine_transform(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  >  affine\_transform transforms this Anchor by the provided `affine_matrix`.
- #### affine\_transform\_without\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,43:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::affine_transform_without_translation(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  >  affine\_transform\_without\_translation transforms this Anchor's rotation, scale,
  > and skew, without affecting its translation.
- #### all\_anchors
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,158:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::all_anchors(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Anchor">Anchor</a>]
  ```
  > 
  >  all\_anchors returns all anchors.
- #### bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,78:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  bounding\_box returns a BoundingBox for this Anchor.
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,23:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::clone(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  >  clone makes a new copy of this Anchor.
- #### closest\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,107:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::closest_point(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, area_of_interest? : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>?
  ```
  > 
  >  closest\_point returns the closest point to `point` or None if no point is found.
  > area\_of\_interest is used to focus the computation within a smaller region.
- #### has\_tangent\_handles
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,141:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::has_tangent_handles(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, tolerance~ : Double = ..) -> Bool
  ```
  > 
  >  has\_tangent\_handles returns true if this Anchor has handles that
  > are tangent to each other.
- #### has\_zero\_handles
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,152:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::has_zero_handles(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> Bool
  ```
  > 
  >  has\_zero\_handles returns true if this Anchor has handles that are both zero.
- #### is\_contained\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,84:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::is_contained_by_bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_contained\_by\_bounding\_box returns true if this Anchor lies within `box`.
- #### is\_intersected\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,91:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::is_intersected_by_bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_intersected\_by\_bounding\_box returns true if the Anchor lies on the
  > boundary of `box`.
- #### is\_overlapped\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,100:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::is_overlapped_by_bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_overlapped\_by\_bounding\_box returns true if the Anchor is within `box`.
- #### loose\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,72:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::loose_bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  loose\_bounding\_box is a simple computation that returns a BoundingBox which
  > may not be the smallest possible.
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,13:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::new(position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., handle_in~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., handle_out~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  >  Anchor::new returns a new anchor. You must either create new Vec2 points
  > or clone them before passing them in.
- #### reverse
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,125:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::reverse(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  >  reverse reverses this Anchor.
- #### transform
  ```moonbit
  :::source,gmlewis/fonts/draw/anchor.mbt,55:::fn <a href="gmlewis/fonts/draw#Anchor">Anchor</a>::transform(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., rotation~ : Double = .., scale~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., skew~ : Double = .., origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  >  transform provides a convenient API for a common task.

## BoundingBox

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,3:::pub(all) struct BoundingBox {
  min : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  max : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
}
```

 BoundingBox represents a minimum bounding box as an axis-aligned rectangle.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,6:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/bounding-box.mbt,6:::fn op_equal(<a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,6:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/bounding-box.mbt,6:::fn output(<a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### area
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,84:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::area(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Double
  ```
  > 
  >  area represents the signed area of the bounding box (width\*height).
  > If min \> max, the area will be negative.
- #### boolean\_intersect
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,166:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::boolean_intersect(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, boxes : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>]) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  boolean\_intersect returns a new BoundingBox representing the intersection
  > of this bounding box with one or more boxes if one exists.
- #### canonicalize
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,102:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::canonicalize(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  >  canonicalize ensures that min \< max.
- #### center
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,59:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::center(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  center returns the center point of the bounding box (the average of min and max).
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,53:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::clone(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  >  clone makes a copy of the bounding box.
- #### contains\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,144:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::contains_bounding_box(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  contains\_bounding\_box returns true if `box` is contained within this bounding box.
- #### contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,137:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::contains_point(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  contains\_point returns true if `point` is contained within this bounding box.
- #### expand\_scalar
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,129:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::expand_scalar(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, distance : Double) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  >  expand\_scalar expands this bounding box by a scalar distance on all sides.
- #### expand\_to\_include\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,120:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::expand_to_include_bounding_box(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  >  expand\_to\_include\_bounding\_box expands this bounding box to also cover `box`.
- #### expand\_to\_include\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,112:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::expand_to_include_point(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  >  expand\_to\_include\_point expands this bounding box to include `point`.
- #### from\_points
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,41:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::from_points(points : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Vec2">Vec2</a>]) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  >  BoundingBox::from\_points constructs the minimum bounding box containing `points`.
- #### height
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,77:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::height(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Double
  ```
  > 
  >  height returns the height of the bounding box.
- #### is\_inf
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,90:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::is_inf(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_inf returns true if either min or max is\_inf.
- #### is\_nan
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,96:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::is_nan(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_nan returns true if either min or max is\_nan.
- #### max\_reversed
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,33:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::max_reversed() -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  >  BoundingBox::max\_reversed returns a new BoundingBox with min=+infinity
  > and max=-infinity.
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,10:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::new(min~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., max~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
  ```
  > 
  >  BoundingBox::new returns a new empty BoundingBox.
- #### overlaps\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,154:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::overlaps_bounding_box(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  overlaps\_bounding\_box returns true if any part of `box` overlaps this bounding box.
- #### size
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,65:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::size(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  size returns a vector representing the (width,height) of the bounding box.
- #### width
  ```moonbit
  :::source,gmlewis/fonts/draw/bounding-box.mbt,71:::fn <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>::width(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Double
  ```
  > 
  >  width returns the width of the bounding box.

## Color

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,3:::pub(all) struct Color {
  r : Double
  g : Double
  b : Double
  a : Double
}
```

 Color represents a color in RGBA color space.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,8:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/color.mbt,8:::fn op_equal(<a href="gmlewis/fonts/draw#Color">Color</a>, <a href="gmlewis/fonts/draw#Color">Color</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,8:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/color.mbt,8:::fn output(<a href="gmlewis/fonts/draw#Color">Color</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,8:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/color.mbt,8:::fn to_json(<a href="gmlewis/fonts/draw#Color">Color</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,8:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/color.mbt,8:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#Color">Color</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### as\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,170:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::as_fill(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> <a href="gmlewis/fonts/draw#Fill">Fill</a>?
  ```
  > 
  >  as\_fill is a convenience function for setting a fill color.
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,176:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::clone(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  >  clone returns a new copy of this Color.
- #### from\_css\_string
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,95:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::from_css_string(css_string : String) -> <a href="gmlewis/fonts/draw#Color">Color</a>!<a href="moonbitlang/core/error#Error">Error</a>
  ```
  > 
  >  Color::from\_css\_string returns a color from a CSS string.
- #### from\_hsva
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,29:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::from_hsva(hue : Double, saturation : Double, value : Double, alpha : Double) -> <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  >  Color::from\_hsva creates a color by converting HSVA space to RGBA.
- #### from\_rgb8\_number
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,161:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::from_rgb8_number(value : UInt) -> <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  >  Color::from\_rgb8\_number returns a color from a bit-packed RGB8 format.
- #### luminance
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,208:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::luminance(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> Double
  ```
  > 
  >  luminance returns the relative luminance of this color for standard human vision.
- #### mix
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,198:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::mix(self : <a href="gmlewis/fonts/draw#Color">Color</a>, c : <a href="gmlewis/fonts/draw#Color">Color</a>, t : Double) -> <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  >  mix linearly interpolates between this Color and `c` with mixing factor `t`.
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,12:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::new(r~ : Double = .., g~ : Double = .., b~ : Double = .., a~ : Double = ..) -> <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  >  Color::new returns a new color.
- #### set
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,182:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::set(self : <a href="gmlewis/fonts/draw#Color">Color</a>, r : Double, g : Double, b : Double, a : Double) -> <a href="gmlewis/fonts/draw#Color">Color</a>
  ```
  > 
  >  set sets the RGBA components of this Color.
- #### to\_css\_hex\_string
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,255:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::to_css_hex_string(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> String
  ```
  > 
  >  to\_css\_hex\_string returns a CSS-style hex string for this color.
- #### to\_css\_rgba\_string
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,273:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::to_css_rgba_string(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> String
  ```
  > 
  >  to\_css\_rgba\_string returns a CSS-style "rgba()" string for this color.
- #### to\_css\_string
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,214:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::to_css_string(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> String
  ```
  > 
  >  to\_css\_string returns a CSS-style string for this color.
- #### to\_hsva
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,293:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::to_hsva(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[Double]
  ```
  > 
  >  to\_hsva converts this color to the HSVA color space, returning
  > \[hue, saturation, value, alpha\] in the range (0..1).
- #### to\_rgb8\_number
  ```moonbit
  :::source,gmlewis/fonts/draw/color.mbt,283:::fn <a href="gmlewis/fonts/draw#Color">Color</a>::to_rgb8_number(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> UInt
  ```
  > 
  >  to\_rgb8\_number returns a bit-packed number in RGB8 format.

## CompoundPath

```moonbit
:::source,gmlewis/fonts/draw/compound-path.mbt,3:::pub(all) struct CompoundPath {
  paths : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Path">Path</a>]
  fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?
  stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?
}
```

 CompoundPath represents one or more paths that typically make up a font glyph.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,7:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/compound-path.mbt,7:::fn output(<a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,7:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/compound-path.mbt,7:::fn to_json(<a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,7:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/compound-path.mbt,7:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### affine\_transform
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,52:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::affine_transform(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  affine\_transform transforms this CompoundPath by `affine_matrix`.
- #### affine\_transform\_without\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,65:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::affine_transform_without_translation(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  affine\_transform\_without\_translation transforms this CompoundPath by `affine_matrix`
  > without affecting translation.
- #### all\_anchors
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,351:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::all_anchors(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Anchor">Anchor</a>]
  ```
  > 
  >  all\_anchors returns a flattened array of all anchors in this CompoundPath.
- #### as\_graphic
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,21:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::as_graphic(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  as\_graphic returns a CompoundPath as a Graphic.
- #### assign\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,93:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::assign_fill(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  assign\_fill assigns a fill to this CompoundPath.
- #### assign\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,103:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::assign_stroke(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  assign\_stroke assigns a stroke to this CompoundPath.
- #### assign\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,113:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::assign_style(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  assign\_style assigns a stroke and fill style to this CompoundPath.
- #### bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,126:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::bounding_box(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  bounding\_box returns the smallest axis-aligned bounding box that contains
  > this CompoundPath or None.
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,43:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::clone(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  clone makes a new copy of this CompoundPath.
- #### closest\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,144:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::closest_point(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, area_of_interest : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>?
  ```
  > 
  >  closest\_point returns the closest point to `point` that lies on this CompoundPath or None.
- #### contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,182:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::contains_point(_self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, _point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  contains\_point returns true if this CompoundPath contains `point`.
- #### copy\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,191:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::copy_style(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, graphic : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  copy\_style copies the fill and stroke from `graphic`.
- #### first\_styled
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,202:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::first_styled(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>?
  ```
  > 
  >  first\_styled returns this CompoundPath if it is styled or None.
- #### has\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,212:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::has_style(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> Bool
  ```
  > 
  >  has\_style returns true if this CompoundPath has fill or stroke.
- #### is\_contained\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,219:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::is_contained_by_bounding_box(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_contained\_by\_bounding\_box returns true if no part of this CompoundPath
  > lies beyond its min or max.
- #### is\_intersected\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,234:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::is_intersected_by_bounding_box(_self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, _box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_intersected\_by\_bounding\_box returns true if part of this CompoundPath crosses
  > the boundary between inside and outside of `box`.
- #### is\_overlapped\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,269:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::is_overlapped_by_bounding_box(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_overlapped\_by\_bounding\_box returns if true if a point can be chosen
  > that is inside both the CompoundPath and `box`.
- #### loose\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,280:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::loose_bounding_box(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  loose\_bounding\_box returns an approximate bounding box for this CompoundPath.
  > It may not be the smallest possible bounding box, but is cheaper to compute.
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,11:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::new(paths~ : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Path">Path</a>] = .., fill? : <a href="gmlewis/fonts/draw#Fill">Fill</a>, stroke? : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  CompoundPath::new creates a new CompoundPath.
- #### op\_get
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,27:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::op_get(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, index : Int) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  op\_get is a convenience function.
- #### op\_set
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,33:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::op_set(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, index : Int, path : <a href="gmlewis/fonts/draw#Path">Path</a>) -> Unit
  ```
  > 
  >  op\_set is a convenience function.
- #### primitives
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,298:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::primitives(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>]
  ```
  > 
  >  primitives returns a flattened array of Graphics primitives.
- #### remove\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,304:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::remove_fill(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  remove\_fill removes fill styling from this CompoundPath.
- #### remove\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,311:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::remove_stroke(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  remove\_stroke removes stroke styling from this CompoundPath.
- #### reverse
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,318:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::reverse(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  reverse reverses this CompoundPath.
- #### rotate
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,371:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::rotate(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, angle : Double) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  rotate rotates a CompoundPath clockwise by `angle` in degrees.
- #### scale
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,364:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::scale(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  scale scales a CompoundPath by `v`.
- #### scale\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,328:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::scale_stroke(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, scale_factor : Double) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  scale\_stroke scales the width of this stroke by `scale_factor`.
- #### style\_contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,341:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::style_contains_point(_self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, _point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  style\_contains\_point returns true if this path's style contains `point`.
- #### transform
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,77:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::transform(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., rotation~ : Double = .., scale~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., skew~ : Double = .., origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  transform provides a convenient API for a common task.
- #### translate
  ```moonbit
  :::source,gmlewis/fonts/draw/compound-path.mbt,357:::fn <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>::translate(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
  ```
  > 
  >  translate translates a CompoundPath by `v`.

## DrawError

```moonbit
:::source,gmlewis/fonts/draw/draw.mbt,7:::pub(all) type! DrawError String

```

 DrawError represents an error that occured during graphic generation.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/draw.mbt,7:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#DrawError">DrawError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/draw.mbt,7:::fn op_equal(<a href="gmlewis/fonts/draw#DrawError">DrawError</a>, <a href="gmlewis/fonts/draw#DrawError">DrawError</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/draw.mbt,7:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#DrawError">DrawError</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/draw.mbt,7:::fn output(<a href="gmlewis/fonts/draw#DrawError">DrawError</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Fill

```moonbit
:::source,gmlewis/fonts/draw/fill.mbt,3:::pub(all) struct Fill {
  color : <a href="gmlewis/fonts/draw#Color">Color</a>
}
```

 Fill defines a fill style.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/fill.mbt,21:::impl <a href="gmlewis/fonts/draw#Clonable">Clonable</a> for <a href="gmlewis/fonts/draw#Fill">Fill</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/fill.mbt,21:::fn clone(self : <a href="gmlewis/fonts/draw#Fill">Fill</a>) -> <a href="gmlewis/fonts/draw#Fill">Fill</a>
    ```
    > 
    >  clone returns a new copy of this Fill.
- ```moonbit
  :::source,gmlewis/fonts/draw/fill.mbt,5:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#Fill">Fill</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/fill.mbt,5:::fn op_equal(<a href="gmlewis/fonts/draw#Fill">Fill</a>, <a href="gmlewis/fonts/draw#Fill">Fill</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/fill.mbt,5:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Fill">Fill</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/fill.mbt,5:::fn output(<a href="gmlewis/fonts/draw#Fill">Fill</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/fill.mbt,5:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#Fill">Fill</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/fill.mbt,5:::fn to_json(<a href="gmlewis/fonts/draw#Fill">Fill</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/fill.mbt,5:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#Fill">Fill</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/fill.mbt,5:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#Fill">Fill</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/fill.mbt,9:::fn <a href="gmlewis/fonts/draw#Fill">Fill</a>::new(color~ : <a href="gmlewis/fonts/draw#Color">Color</a> = ..) -> <a href="gmlewis/fonts/draw#Fill">Fill</a>
  ```
  > 
  >  Fill::new returns a new fill style.

## Graphic

```moonbit
:::source,gmlewis/fonts/draw/graphic.mbt,3:::pub(all) enum Graphic {
  CompoundPath(<a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>)
  Group(<a href="gmlewis/fonts/draw#Group">Group</a>)
  Path(<a href="gmlewis/fonts/draw#Path">Path</a>)
}
```

 Graphic represents a drawable graphic element.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,7:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/graphic.mbt,7:::fn output(<a href="gmlewis/fonts/draw#Graphic">Graphic</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,433:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/graphic.mbt,433:::fn to_json(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > 
- ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,442:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/graphic.mbt,442:::fn from_json(json : <a href="moonbitlang/core/json#Json">Json</a>, path : <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### affine\_transform
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,21:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::affine_transform(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  affine\_transform transforms this graphic by `affine_matrix`.
- #### affine\_transform\_without\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,52:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::affine_transform_without_translation(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  affine\_transform\_without\_translation transforms this graphic by `affine_matrix`
  > without affecting the translation.
- #### all\_anchors
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,216:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::all_anchors(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Anchor">Anchor</a>]
  ```
  > 
  >  all\_anchors returns all Anchors in this Graphic.
- #### all\_compound\_paths
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,196:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::all_compound_paths(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>]
  ```
  > 
  >  all\_compound\_paths returns all CompoundPaths in this Graphic.
- #### all\_paths
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,206:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::all_paths(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Path">Path</a>]
  ```
  > 
  >  all\_paths returns all Paths in this Graphic.
- #### all\_paths\_and\_compound\_paths
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,226:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::all_paths_and_compound_paths(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>]
  ```
  > 
  >  all\_paths\_and\_compound\_paths returns all Paths and CompoundPaths in this Graphic.
- #### assign\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,246:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::assign_fill(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  assign\_fill assigns a fill to this Graphic.
- #### assign\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,268:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::assign_stroke(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  assign\_stroke assigns a stroke to this Graphic.
- #### assign\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,290:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::assign_style(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  assign\_style assigns a fill and stroke style to this Graphic.
- #### bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,80:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::bounding_box(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  bounding\_box returns the bounding box for this Graphic.
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,11:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::clone(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  clone returns a new copy of Graphic.
- #### closest\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,161:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::closest_point(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, area_of_interest : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>?
  ```
  > 
  >  closest\_point returns the closest Anchor to `point` that lies on this Graphic
  > or None.
- #### contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,339:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::contains_point(point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> ((<a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Bool)
  ```
  > 
  >  Graphic::contains\_point returns a function that returns true if this
  > Graphic contains `point`.
- #### copy\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,305:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::copy_style(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, graphic : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  copy\_style copies the fill and stroke style from `graphic`.
- #### every
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,90:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::every(items : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>], func : (<a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Bool) -> Bool
  ```
  > 
  >  Graphic::every returns true if all tests of `func` are true.
- #### first\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,364:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::first_fill(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Fill">Fill</a>?
  ```
  > 
  >  first\_fill returns the first fill from this Graphic.
- #### first\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,374:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::first_stroke(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?
  ```
  > 
  >  first\_stroke returns the first stroke from this Graphic.
- #### first\_styled
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,328:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::first_styled(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>?
  ```
  > 
  >  first\_styled returns the first Path or CompoundPath in this Graphic
  > that has either a fill or a stroke, or None.
- #### fit\_to
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,414:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::fit_to(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  fit\_to scales and translates a Graphic to fix in `box`.
- #### has\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,236:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::has_style(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Bool
  ```
  > 
  >  has\_style returns true if this Graphic has either a stroke or a fill.
- #### is\_contained\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,113:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::is_contained_by_bounding_box(box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> ((<a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Bool)
  ```
  > 
  >  Graphic::is\_contained\_by\_bounding\_box returns a function that tests
  > if a graphic is contained by the box.
- #### is\_intersected\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,129:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::is_intersected_by_bounding_box(box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> ((<a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Bool)
  ```
  > 
  >  Graphic::is\_intersected\_by\_bounding\_box returns a function that tests
  > if a graphic is intersected by the box.
- #### is\_overlapped\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,145:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::is_overlapped_by_bounding_box(box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> ((<a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Bool)
  ```
  > 
  >  Graphic::is\_overlapped\_by\_bounding\_box returns a function that tests
  > if a graphic is overlapped by the box.
- #### loose\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,70:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::loose_bounding_box(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  loose\_bounding\_box returns an approximate bounding box for all items.
  > It may not be the smallest possible bounding box, but is cheaper to compute.
- #### primitives
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,176:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::primitives(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>]
  ```
  > 
  >  primitives returns an array of primitives.
- #### remove\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,257:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::remove_fill(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  remove\_fill a fill style from this Graphic.
- #### remove\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,279:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::remove_stroke(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  remove\_stroke a stroke style from this Graphic.
- #### reverse
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,186:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::reverse(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  reverse reverses this Graphic.
- #### rotate
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,404:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::rotate(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, angle : Double) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  rotate rotates a Graphic clockwise by `angle` in degrees.
- #### scale
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,394:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::scale(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  scale scales a Graphic by `v`.
- #### scale\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,316:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::scale_stroke(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, scale_factor : Double) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  scale\_stroke scales the stroke width of this Graphic by `scale_factor`.
- #### some
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,101:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::some(items : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>], func : (<a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Bool) -> Bool
  ```
  > 
  >  Graphic::some returns true if any calls to `func` are true.
- #### style\_contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,352:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::style_contains_point(point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> ((<a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Bool)
  ```
  > 
  >  Graphic::style\_contains\_point returns a function that returns true if this
  > Graphic's style contains `point`.
- #### transform
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,35:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::transform(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., rotation~ : Double = .., scale~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., skew~ : Double = .., origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  transform provides a convenient API for a common task.
- #### translate
  ```moonbit
  :::source,gmlewis/fonts/draw/graphic.mbt,384:::fn <a href="gmlewis/fonts/draw#Graphic">Graphic</a>::translate(self : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  translate translates a Graphic by `v`.

## Group

```moonbit
:::source,gmlewis/fonts/draw/group.mbt,3:::pub(all) struct Group {
  items : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>]
}
```

 Group represents a collection of Graphics elements.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,5:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/group.mbt,5:::fn output(<a href="gmlewis/fonts/draw#Group">Group</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,5:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/group.mbt,5:::fn to_json(<a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,5:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/group.mbt,5:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### affine\_transform
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,45:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::affine_transform(self : <a href="gmlewis/fonts/draw#Group">Group</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  affine\_transform transforms this Group by `affine_matrix`.
- #### affine\_transform\_without\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,58:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::affine_transform_without_translation(self : <a href="gmlewis/fonts/draw#Group">Group</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  affine\_transform\_without\_translation transforms this Group by `affine_matrix`
  > without affecting the translation.
- #### all\_anchors
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,257:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::all_anchors(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Anchor">Anchor</a>]
  ```
  > 
  >  all\_anchors returns all Anchors in this Group.
- #### all\_compound\_paths
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,242:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::all_compound_paths(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>]
  ```
  > 
  >  all\_compound\_paths returns all compound paths in this Group.
- #### all\_paths
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,251:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::all_paths(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Path">Path</a>]
  ```
  > 
  >  all\_paths returns all Paths in this Group.
- #### all\_paths\_and\_compound\_paths
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,263:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::all_paths_and_compound_paths(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>]
  ```
  > 
  >  all\_paths\_and\_compound\_paths returns all Paths and CompoundPaths in this Group.
- #### as\_graphic
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,15:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::as_graphic(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  as\_graphic returns a Group as a Graphic.
- #### assign\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,283:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::assign_fill(self : <a href="gmlewis/fonts/draw#Group">Group</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  assign\_fill assigns a fill to this Group.
- #### assign\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,301:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::assign_stroke(self : <a href="gmlewis/fonts/draw#Group">Group</a>, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  assign\_stroke assigns a stroke to this Group.
- #### assign\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,319:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::assign_style(self : <a href="gmlewis/fonts/draw#Group">Group</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  assign\_style assigns a fill and stroke style to this Group.
- #### bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,125:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::bounding_box(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  bounding\_box returns the bounding box for all items in the Group.
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,39:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::clone(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  clone returns a new copy of this Group.
- #### closest\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,194:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::closest_point(self : <a href="gmlewis/fonts/draw#Group">Group</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, area_of_interest : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>?
  ```
  > 
  >  closest\_point returns the closest Anchor to `point` that lies on this Group
  > or None.
- #### contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,363:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::contains_point(self : <a href="gmlewis/fonts/draw#Group">Group</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  contains\_point returns true if this Group contains `point`.
- #### copy\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,332:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::copy_style(self : <a href="gmlewis/fonts/draw#Group">Group</a>, graphic : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  copy\_style copies the fill and stroke style from `graphic`.
- #### first\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,375:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::first_fill(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#Fill">Fill</a>?
  ```
  > 
  >  first\_fill returns the first fill from this Group.
- #### first\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,387:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::first_stroke(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?
  ```
  > 
  >  first\_stroke returns the first stroke from this Group.
- #### first\_styled
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,351:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::first_styled(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>?
  ```
  > 
  >  first\_styled returns the first Path or CompoundPath in this Group
  > that has either a fill or a stroke, or None.
- #### has\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,272:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::has_style(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> Bool
  ```
  > 
  >  has\_style returns true if this Group has either a stroke or a fill.
- #### is\_contained\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,163:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::is_contained_by_bounding_box(self : <a href="gmlewis/fonts/draw#Group">Group</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_contained\_by\_bounding\_box returns true if no part of the Group
  > lies beyond the box's min and max.
- #### is\_intersected\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,174:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::is_intersected_by_bounding_box(self : <a href="gmlewis/fonts/draw#Group">Group</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_intersected\_by\_bounding\_box returns true if any part of the Group
  > crosses the boundary between the inside and outside of `box`.
- #### is\_overlapped\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,184:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::is_overlapped_by_bounding_box(self : <a href="gmlewis/fonts/draw#Group">Group</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_overlapped\_by\_bounding\_box returns true if a point can be found that
  > is inside both the Graphic and the box.
- #### loose\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,88:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::loose_bounding_box(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  loose\_bounding\_box returns an approximate bounding box for all items
  > in the Group. It may not be the smallest possible bounding box, but
  > is cheaper to compute.
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,9:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::new(items~ : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>] = ..) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  Group::new returns a new group.
- #### op\_get
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,21:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::op_get(self : <a href="gmlewis/fonts/draw#Group">Group</a>, index : Int) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  op\_get is a convenience function.
- #### op\_set
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,27:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::op_set(self : <a href="gmlewis/fonts/draw#Group">Group</a>, index : Int, graphic : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> Unit
  ```
  > 
  >  op\_set is a convenience function.
- #### primitives
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,226:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::primitives(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>]
  ```
  > 
  >  primitives returns a flattened array of all Graphic primitives in this Group.
- #### remove\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,292:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::remove_fill(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  remove\_fill removes a fill style from this Group.
- #### remove\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,310:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::remove_stroke(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  remove\_stroke removes a stroke style from this Group.
- #### reverse
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,232:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::reverse(self : <a href="gmlewis/fonts/draw#Group">Group</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  reverse reverses this Group.
- #### rotate
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,413:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::rotate(self : <a href="gmlewis/fonts/draw#Group">Group</a>, angle : Double) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  rotate rotates a Group clockwise by `angle` in degrees.
- #### scale
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,406:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::scale(self : <a href="gmlewis/fonts/draw#Group">Group</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  scale scales a Group by `v`.
- #### scale\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,341:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::scale_stroke(self : <a href="gmlewis/fonts/draw#Group">Group</a>, scale_factor : Double) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  scale\_stroke scales the stroke width of this Group by `scale_factor`.
- #### style\_contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,369:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::style_contains_point(self : <a href="gmlewis/fonts/draw#Group">Group</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  style\_contains\_point returns true if this Group's style contains `point`.
- #### transform
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,70:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::transform(self : <a href="gmlewis/fonts/draw#Group">Group</a>, position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., rotation~ : Double = .., scale~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., skew~ : Double = .., origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  transform provides a convenient API for a common task.
- #### translate
  ```moonbit
  :::source,gmlewis/fonts/draw/group.mbt,399:::fn <a href="gmlewis/fonts/draw#Group">Group</a>::translate(self : <a href="gmlewis/fonts/draw#Group">Group</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Group">Group</a>
  ```
  > 
  >  translate translates a Group by `v`.

## Path

```moonbit
:::source,gmlewis/fonts/draw/path.mbt,6:::pub(all) struct Path {
  anchors : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Anchor">Anchor</a>]
  closed : Bool
  clear : Bool
  fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?
  stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?
}
```

 Path represents an open or closed path that can be stroked as an outline
or filled. A 'clear' path is sub-path of a Path that defines
regions of the filled path where no fill is added, for example in the
center of the letter 'O'.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,12:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/path.mbt,12:::fn output(<a href="gmlewis/fonts/draw#Path">Path</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,12:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/path.mbt,12:::fn to_json(<a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,12:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/path.mbt,12:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### affine\_transform
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,74:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::affine_transform(self : <a href="gmlewis/fonts/draw#Path">Path</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  affine\_transform transforms this Path by `affine_matrix`.
- #### affine\_transform\_without\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,87:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::affine_transform_without_translation(self : <a href="gmlewis/fonts/draw#Path">Path</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  affine\_transform\_without\_translation transforms this Path by `affine_matrix`
  > without affecting translation.
- #### as\_graphic
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,28:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::as_graphic(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>
  ```
  > 
  >  as\_graphic returns a Path as a Graphic.
- #### assign\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,115:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::assign_fill(self : <a href="gmlewis/fonts/draw#Path">Path</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  assign\_fill assigns a fill to this Path.
- #### assign\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,122:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::assign_stroke(self : <a href="gmlewis/fonts/draw#Path">Path</a>, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  assign\_stroke assigns a stroke to this Path.
- #### assign\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,129:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::assign_style(self : <a href="gmlewis/fonts/draw#Path">Path</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  assign\_style assigns a stroke and fill style to this Path.
- #### bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,214:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::bounding_box(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  bounding\_box returns the smallest axis-aligned bounding box that contains
  > this Path or None.
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,63:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::clone(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  clone makes a new copy of this Path.
- #### closest\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,265:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::closest_point(self : <a href="gmlewis/fonts/draw#Path">Path</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, area_of_interest : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>?
  ```
  > 
  >  closest\_point returns the closest point to `point` that lies on this Path or None.
- #### contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,338:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::contains_point(_self : <a href="gmlewis/fonts/draw#Path">Path</a>, _point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  contains\_point returns true if this Path contains `point`.
- #### copy\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,344:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::copy_style(self : <a href="gmlewis/fonts/draw#Path">Path</a>, graphic : <a href="gmlewis/fonts/draw#Graphic">Graphic</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  copy\_style copies the fill and stroke from `graphic`.
- #### first\_styled
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,352:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::first_styled(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>?
  ```
  > 
  >  first\_styled returns this Path if it is styled or None.
- #### from\_points
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,46:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::from_points(points : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Vec2">Vec2</a>], closed~ : Bool = ..) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  Path::from\_points connects a series of points with lines to form a Path.
- #### has\_style
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,362:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::has_style(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> Bool
  ```
  > 
  >  has\_style returns true if this Path has fill or stroke.
- #### is\_contained\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,369:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::is_contained_by_bounding_box(self : <a href="gmlewis/fonts/draw#Path">Path</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_contained\_by\_bounding\_box returns true if no part of this Path
  > lies beyond its min or max.
- #### is\_intersected\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,384:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::is_intersected_by_bounding_box(_self : <a href="gmlewis/fonts/draw#Path">Path</a>, _box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_intersected\_by\_bounding\_box returns true if part of this Path crosses
  > the boundary between inside and outside of `box`.
- #### is\_overlapped\_by\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,419:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::is_overlapped_by_bounding_box(self : <a href="gmlewis/fonts/draw#Path">Path</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
  ```
  > 
  >  is\_overlapped\_by\_bounding\_box returns if true if a point can be chosen
  > that is inside both the Path and `box`.
- #### loose\_bounding\_box
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,430:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::loose_bounding_box(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
  ```
  > 
  >  loose\_bounding\_box returns an approximate bounding box for this Path.
  > It may not be the smallest possible bounding box, but is cheaper to compute.
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,16:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::new(anchors~ : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Anchor">Anchor</a>] = .., closed~ : Bool = .., clear~ : Bool = .., fill? : <a href="gmlewis/fonts/draw#Fill">Fill</a>, stroke? : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  Path::new creates a new Path.
- #### op\_get
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,34:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::op_get(self : <a href="gmlewis/fonts/draw#Path">Path</a>, index : Int) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
  ```
  > 
  >  op\_get is a convenience function.
- #### op\_set
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,40:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::op_set(self : <a href="gmlewis/fonts/draw#Path">Path</a>, index : Int, anchor : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> Unit
  ```
  > 
  >  op\_set is a convenience function.
- #### primitives
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,489:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::primitives(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>]
  ```
  > 
  >  primitives returns a flattened array of Graphics primitives.
- #### remove\_fill
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,495:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::remove_fill(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  remove\_fill removes fill styling from this Path.
- #### remove\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,502:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::remove_stroke(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  remove\_stroke removes stroke styling from this Path.
- #### reverse
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,509:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::reverse(self : <a href="gmlewis/fonts/draw#Path">Path</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  reverse reverses this Path.
- #### rotate
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,550:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::rotate(self : <a href="gmlewis/fonts/draw#Path">Path</a>, angle : Double) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  rotate rotates a Path clockwise by `angle` in degrees.
- #### scale
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,543:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::scale(self : <a href="gmlewis/fonts/draw#Path">Path</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  scale scales a Path by `v`.
- #### scale\_stroke
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,519:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::scale_stroke(self : <a href="gmlewis/fonts/draw#Path">Path</a>, scale_factor : Double) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  scale\_stroke scales the width of this stroke by `scale_factor`.
- #### style\_contains\_point
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,529:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::style_contains_point(_self : <a href="gmlewis/fonts/draw#Path">Path</a>, _point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  style\_contains\_point returns true if this path's style contains `point`.
- #### transform
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,99:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::transform(self : <a href="gmlewis/fonts/draw#Path">Path</a>, position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., rotation~ : Double = .., scale~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., skew~ : Double = .., origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  transform provides a convenient API for a common task.
- #### translate
  ```moonbit
  :::source,gmlewis/fonts/draw/path.mbt,536:::fn <a href="gmlewis/fonts/draw#Path">Path</a>::translate(self : <a href="gmlewis/fonts/draw#Path">Path</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Path">Path</a>
  ```
  > 
  >  translate translates a Path by `v`.

## Stroke

```moonbit
:::source,gmlewis/fonts/draw/stroke.mbt,3:::pub(all) struct Stroke {
  color : <a href="gmlewis/fonts/draw#Color">Color</a>
  width : Double
  alignment : <a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>
  cap : <a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>
  join : <a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>
  miter_limit : Double
}
```

 Stroke defines a stroke style.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,54:::impl <a href="gmlewis/fonts/draw#Clonable">Clonable</a> for <a href="gmlewis/fonts/draw#Stroke">Stroke</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,54:::fn clone(self : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>) -> <a href="gmlewis/fonts/draw#Stroke">Stroke</a>
    ```
    > 
    >  clone returns a new copy of this Stroke.
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,10:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#Stroke">Stroke</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,10:::fn op_equal(<a href="gmlewis/fonts/draw#Stroke">Stroke</a>, <a href="gmlewis/fonts/draw#Stroke">Stroke</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,10:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Stroke">Stroke</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,10:::fn output(<a href="gmlewis/fonts/draw#Stroke">Stroke</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,10:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#Stroke">Stroke</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,10:::fn to_json(<a href="gmlewis/fonts/draw#Stroke">Stroke</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,10:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#Stroke">Stroke</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,10:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#Stroke">Stroke</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,35:::fn <a href="gmlewis/fonts/draw#Stroke">Stroke</a>::new(color~ : <a href="gmlewis/fonts/draw#Color">Color</a> = .., width~ : Double = .., alignment~ : <a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a> = .., cap~ : <a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a> = .., join~ : <a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a> = .., miter_limit~ : Double = ..) -> <a href="gmlewis/fonts/draw#Stroke">Stroke</a>
  ```
  > 
  >  Stroke::new returns a new stroke style.

## StrokeAlignment

```moonbit
:::source,gmlewis/fonts/draw/stroke.mbt,13:::pub(all) enum StrokeAlignment {
  Centered
  Inner
  Outer
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,17:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,17:::fn op_equal(<a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>, <a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,17:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,17:::fn output(<a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,17:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,17:::fn to_json(<a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,17:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,17:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#StrokeAlignment">StrokeAlignment</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

## StrokeCap

```moonbit
:::source,gmlewis/fonts/draw/stroke.mbt,20:::pub(all) enum StrokeCap {
  Butt
  Round
  Square
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,24:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,24:::fn op_equal(<a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>, <a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,24:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,24:::fn output(<a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,24:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,24:::fn to_json(<a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,24:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,24:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#StrokeCap">StrokeCap</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

## StrokeJoin

```moonbit
:::source,gmlewis/fonts/draw/stroke.mbt,27:::pub(all) enum StrokeJoin {
  Miter
  Round
  Bevel
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,31:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,31:::fn op_equal(<a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>, <a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,31:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,31:::fn output(<a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,31:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,31:::fn to_json(<a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/stroke.mbt,31:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/stroke.mbt,31:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#StrokeJoin">StrokeJoin</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

## TextAlign

```moonbit
:::source,gmlewis/fonts/draw/text.mbt,5:::pub(all) enum TextAlign {
  Left
  Center
  Right
}
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/text.mbt,9:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#TextAlign">TextAlign</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/text.mbt,9:::fn op_equal(<a href="gmlewis/fonts/draw#TextAlign">TextAlign</a>, <a href="gmlewis/fonts/draw#TextAlign">TextAlign</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/text.mbt,9:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#TextAlign">TextAlign</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/text.mbt,9:::fn output(<a href="gmlewis/fonts/draw#TextAlign">TextAlign</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## Transform

```moonbit
:::source,gmlewis/fonts/draw/transform.mbt,3:::pub(all) struct Transform {
  position : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  rotation : Double
  scale : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  skew : Double
  origin : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
}
```

 Transform represents transform arguments.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/transform.mbt,9:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#Transform">Transform</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/transform.mbt,9:::fn op_equal(<a href="gmlewis/fonts/draw#Transform">Transform</a>, <a href="gmlewis/fonts/draw#Transform">Transform</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/transform.mbt,9:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Transform">Transform</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/transform.mbt,9:::fn output(<a href="gmlewis/fonts/draw#Transform">Transform</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/transform.mbt,13:::fn <a href="gmlewis/fonts/draw#Transform">Transform</a>::new(position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., rotation~ : Double = .., scale~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., skew~ : Double = .., origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Transform">Transform</a>
  ```
  > 
  >  Transform::new returns a new identity transform.

## Vec2

```moonbit
:::source,gmlewis/fonts/draw/vec2.mbt,3:::pub(all) struct Vec2 {
  x : Double
  y : Double
}
```

 Vec2 represents a 2D vector.

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,6:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/vec2.mbt,6:::fn op_equal(<a href="gmlewis/fonts/draw#Vec2">Vec2</a>, <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,6:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/vec2.mbt,6:::fn output(<a href="gmlewis/fonts/draw#Vec2">Vec2</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,6:::impl <a href="moonbitlang/core/builtin#ToJson">ToJson</a> for <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/vec2.mbt,6:::fn to_json(<a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="moonbitlang/core/json#Json">Json</a>
    ```
    > automatically derived
- ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,6:::impl <a href="moonbitlang/core/json#FromJson">@moonbitlang/core/json.FromJson</a> for <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  * ```moonbit
    :::source,gmlewis/fonts/draw/vec2.mbt,6:::fn from_json(<a href="moonbitlang/core/json#Json">Json</a>, <a href="moonbitlang/core/json#JsonPath">@moonbitlang/core/json.JsonPath</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>!<a href="moonbitlang/core/json#JsonDecodeError">@moonbitlang/core/json.JsonDecodeError</a>
    ```
    > automatically derived

#### mooncakes-io-method-mark-Methods
- #### add
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,124:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::add(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  add adds the vector `v` to this vector.
- #### add\_scalar
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,139:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::add_scalar(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, s : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  add\_scalar adds scalar `s` to this vector.
- #### affine\_transform
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,78:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::affine_transform(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  affine\_transform transforms this Vec2 by the `affine_matrix`.
  > This is used when transforming a point or position.
- #### affine\_transform\_without\_translation
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,93:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::affine_transform_without_translation(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  affine\_transform\_without\_translation transforms this Vec2 by the `affine_matrix`
  > but without performing translation.
  > This is used when transforming a normal or tangent.
- #### almost\_equals
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,241:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::almost_equals(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, other : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, tolerance~ : Double = ..) -> Bool
  ```
  > 
  >  almost\_equals returns true if the vectors are equal within the provided tolerance.
- #### angle
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,405:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::angle(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Double
  ```
  > 
  >  angle returns the angle of this vector in degrees.
- #### angle\_radians
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,411:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::angle_radians(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Double
  ```
  > 
  >  angle\_radians returns the angle of this vector in radians.
- #### apply
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,252:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::apply(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, func : (Double) -> Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  apply applies the provided `func` to both components of this vector.
- #### ceil
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,266:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::ceil(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  ceil rounds the components of this vector to the next-higher integer.
- #### clone
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,49:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::clone(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  clone returns a new copy of this Vec2.
- #### copy
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,63:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::copy(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  copy copies `v` into this Vec2.
- #### cross
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,340:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::cross(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Double
  ```
  > 
  >  cross returns the cross product between this vector and the vector `v`.
- #### distance
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,436:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::distance(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Double
  ```
  > 
  >  distance returns the distance from this vector to `v`.
- #### distance\_squared
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,442:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::distance_squared(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Double
  ```
  > 
  >  distance\_squared returns the squared distance from this vector to `v`.
- #### div
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,193:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::div(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  div divides this vector by vector `v`.
- #### div\_scalar
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,208:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::div_scalar(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, s : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  div\_scalar divides this vector by scalar `s`.
- #### dot
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,334:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::dot(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Double
  ```
  > 
  >  dot returns the dot product between this vector and the vector `v`.
- #### floor
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,260:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::floor(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  floor rounds the components of this vector to the next-lower integer.
- #### from\_angle
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,34:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::from_angle(angle : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  Vec2::from\_angle returns a new unit vec2 from an angle in degrees.
- #### from\_angle\_radians
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,41:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::from_angle_radians(rad : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  Vec2::from\_angle\_radians returns a new unit vec2 from an angle in radians.
- #### infinity
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,16:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::infinity() -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  Vec::infinity returns a new Vec2 with infinite x and y.
- #### is\_clockwise\_from
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,418:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::is_clockwise_from(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  is\_clockwise\_from returns true if this vector lies in the 180° region
  > clockwise from `v`.
- #### is\_inf
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,462:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::is_inf(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  is\_inf returns true if either component is infinite.
- #### is\_nan
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,456:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::is_nan(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  is\_nan returns true if either component is NaN (not a number).
- #### is\_valid
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,71:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::is_valid(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  is\_valid returns whether or not this Vec2 is valid.
- #### is\_zero
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,450:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::is_zero(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
  ```
  > 
  >  is\_zero returns true if both components of this vector are 0.
- #### length
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,424:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::length(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Double
  ```
  > 
  >  length returns the length of this vector.
- #### length\_squared
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,430:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::length_squared(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Double
  ```
  > 
  >  length\_squared returns the squared length of this vector.
- #### max
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,317:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::max(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  max compares the components of this vector and `v` and sets this vector's
  > components to the maximum of the two.
- #### min
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,308:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::min(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  min compares the components of this vector and `v` and sets this vector's
  > components to the minimum of the two.
- #### mix
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,326:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::mix(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, t : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  mix linearly interpolates this vector to the vector `v` by the mixing
  > factor `t` (0..1).
- #### mul
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,170:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::mul(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  mul multiplies the vector `v` to this vector.
- #### mul\_scalar
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,185:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::mul_scalar(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, s : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  mul\_scalar multiplies scalar `s` to this vector.
- #### neg\_infinity
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,22:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::neg_infinity() -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  Vec::neg\_infinity returns a new Vec2 with negative infinite x and y.
- #### negate
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,216:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::negate(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  negate multiplies both components (in-place) by -1.
- #### new
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,10:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::new(x~ : Double = .., y~ : Double = ..) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  Vec2::new returns a new Vec2.
- #### normalize
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,347:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::normalize(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  normalize scales this vector so that its length is 1.
  > Note that this vector must already have a non-zero length.
- #### op\_add
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,133:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::op_add(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, other : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  op\_add adds vector `other` to this vector without modifying either one
  > and returns the result.
- #### op\_div
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,202:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::op_div(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, other : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  op\_div divides this vector by vector `other` without modifying either one
  > and returns the result.
- #### op\_mul
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,179:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::op_mul(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, other : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  op\_mul multiplies vector `other` to this vector without modifying either one
  > and returns the result.
- #### op\_neg
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,224:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::op_neg(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  op\_neg returns a negated copy of Vec2.
- #### op\_sub
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,156:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::op_sub(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, other : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  op\_sub subtracts vector `other` from this vector without modifying either one
  > and returns the result.
- #### project\_onto
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,393:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::project_onto(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  project\_onto projects this vector onto a non-zero vector `v`.
- #### rotate
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,357:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::rotate(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, angle : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  rotate rotates this vector clockwise by `angle` in degrees.
- #### rotate90
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,375:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::rotate90(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  rotate90 rotates this vector clockwise by 90°.
- #### rotate\_neg90
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,384:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::rotate_neg90(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  rotate\_neg90 rotates this vector counter-clockwise by 90°.
- #### rotate\_radians
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,364:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::rotate_radians(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, rad : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  rotate\_radians rotates this vector clockwise by `rad` in radians.
- #### round
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,272:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::round(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  round rounds the components of this vector to the next-higher integer.
- #### round\_to\_fixed
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,279:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::round_to_fixed(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, digits : Int) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  round\_to\_fixed rounds the components of this vector to the provided
  > number of digits.
- #### round\_to\_multiple
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,295:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::round_to_multiple(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  round\_to\_multiple rounds the components of this vector to the closes
  > multiple of `v`.
- #### set
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,55:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::set(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, x : Double, y : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  set sets the x and y components of this Vec2.
- #### sub
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,147:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::sub(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  sub subtracts the vector `v` from this vector.
- #### sub\_scalar
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,162:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::sub_scalar(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, s : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  sub\_scalar subtracts scalar `s` from this vector.
- #### transform
  ```moonbit
  :::source,gmlewis/fonts/draw/vec2.mbt,108:::fn <a href="gmlewis/fonts/draw#Vec2">Vec2</a>::transform(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., rotation~ : Double = .., scale~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., skew~ : Double = .., origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
  ```
  > 
  >  transform provides a convenient API for a common task.

## affine\_transform

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,33:::fn affine_transform(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
```

 affine\_transform transforms this Anchor by the provided `affine_matrix`.

## affine\_transform\_without\_translation

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,43:::fn affine_transform_without_translation(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, affine_matrix : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
```

 affine\_transform\_without\_translation transforms this Anchor's rotation, scale,
and skew, without affecting its translation.

## all\_anchors

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,158:::fn all_anchors(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Anchor">Anchor</a>]
```

 all\_anchors returns all anchors.

## almost\_equals

```moonbit
:::source,gmlewis/fonts/draw/vec2.mbt,241:::fn almost_equals(self : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, other : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, tolerance~ : Double = ..) -> Bool
```

 almost\_equals returns true if the vectors are equal within the provided tolerance.

## area

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,84:::fn area(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Double
```

 area represents the signed area of the bounding box (width\*height).
If min \> max, the area will be negative.

## as\_fill

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,170:::fn as_fill(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> <a href="gmlewis/fonts/draw#Fill">Fill</a>?
```

 as\_fill is a convenience function for setting a fill color.

## assign\_style

```moonbit
:::source,gmlewis/fonts/draw/compound-path.mbt,113:::fn assign_style(self : <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>, fill : <a href="gmlewis/fonts/draw#Fill">Fill</a>?, stroke : <a href="gmlewis/fonts/draw#Stroke">Stroke</a>?) -> <a href="gmlewis/fonts/draw#CompoundPath">CompoundPath</a>
```

 assign\_style assigns a stroke and fill style to this CompoundPath.

## bbox

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,19:::fn bbox(minx : Double, miny : Double, maxx : Double, maxy : Double) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
```

 bbox is a convenience function.

## boolean\_intersect

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,166:::fn boolean_intersect(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, boxes : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>]) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
```

 boolean\_intersect returns a new BoundingBox representing the intersection
of this bounding box with one or more boxes if one exists.

## bounding\_box

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,78:::fn bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
```

 bounding\_box returns a BoundingBox for this Anchor.

## canonicalize

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,102:::fn canonicalize(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
```

 canonicalize ensures that min \< max.

## center

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,59:::fn center(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
```

 center returns the center point of the bounding box (the average of min and max).

## clone

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,97:::fn clone(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 clone returns a copy of this 2D affine matrix.

## closest\_point

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,107:::fn closest_point(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>, area_of_interest? : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>?
```

 closest\_point returns the closest point to `point` or None if no point is found.
area\_of\_interest is used to focus the computation within a smaller region.

## contains\_bounding\_box

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,144:::fn contains_bounding_box(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
```

 contains\_bounding\_box returns true if `box` is contained within this bounding box.

## contains\_point

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,137:::fn contains_point(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> Bool
```

 contains\_point returns true if `point` is contained within this bounding box.

## copy

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,104:::fn copy(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, other : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 copy copies another 2D affine matrix into itself and returns itself.

## determinant

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,274:::fn determinant(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Double
```

 determinant returns the determinant of the 2D affine matrix.

## expand\_scalar

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,129:::fn expand_scalar(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, distance : Double) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
```

 expand\_scalar expands this bounding box by a scalar distance on all sides.

## expand\_to\_include\_bounding\_box

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,120:::fn expand_to_include_bounding_box(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
```

 expand\_to\_include\_bounding\_box expands this bounding box to also cover `box`.

## expand\_to\_include\_point

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,112:::fn expand_to_include_point(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, point : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>
```

 expand\_to\_include\_point expands this bounding box to include `point`.

## fill

```moonbit
:::source,gmlewis/fonts/draw/fill.mbt,15:::fn fill(color : <a href="gmlewis/fonts/draw#Color">Color</a>) -> <a href="gmlewis/fonts/draw#Fill">Fill</a>
```

 fill is a helper function.

## group

```moonbit
:::source,gmlewis/fonts/draw/group.mbt,33:::fn group(items : <a href="moonbitlang/core/array#Array">Array</a>[<a href="gmlewis/fonts/draw#Graphic">Graphic</a>]) -> <a href="gmlewis/fonts/draw#Group">Group</a>
```

 group is a convenience function.

## has\_tangent\_handles

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,141:::fn has_tangent_handles(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, tolerance~ : Double = ..) -> Bool
```

 has\_tangent\_handles returns true if this Anchor has handles that
are tangent to each other.

## has\_zero\_handles

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,152:::fn has_zero_handles(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> Bool
```

 has\_zero\_handles returns true if this Anchor has handles that are both zero.

## height

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,77:::fn height(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Double
```

 height returns the height of the bounding box.

## invert

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,116:::fn invert(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 invert inverts this 2D affine matrix.

## is\_contained\_by\_bounding\_box

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,84:::fn is_contained_by_bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
```

 is\_contained\_by\_bounding\_box returns true if this Anchor lies within `box`.

## is\_identity

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,315:::fn is_identity(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
```

 is\_identity returns true if this 2D affine matrix is the identity matrix.

## is\_inf

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,337:::fn is_inf(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
```

 is\_inf returns true if any elements of this 2D affine matrix are infinite.

## is\_intersected\_by\_bounding\_box

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,91:::fn is_intersected_by_bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
```

 is\_intersected\_by\_bounding\_box returns true if the Anchor lies on the
boundary of `box`.

## is\_invertible

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,292:::fn is_invertible(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
```

 is\_invertible returns true if this 2D affine matrix is invertible.

## is\_mirror

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,309:::fn is_mirror(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
```

 is\_mirror returns true if this 2D affine matrix mirrors either axis.

## is\_nan

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,326:::fn is_nan(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> Bool
```

 is\_nan returns true if any elements of this 2D affine matrix are NaN (not a number).

## is\_orthogonal

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,282:::fn is_orthogonal(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, tolerance~ : Double = ..) -> Bool
```

 is\_orthogonal returns true if the two basis vectors of the 2D affine matrix
are orthogonal within the provided tolerance.

## is\_overlapped\_by\_bounding\_box

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,100:::fn is_overlapped_by_bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
```

 is\_overlapped\_by\_bounding\_box returns true if the Anchor is within `box`.

## is\_uniform\_scale

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,299:::fn is_uniform_scale(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, tolerance~ : Double = ..) -> Bool
```

 is\_uniform\_scale returns true if both basis vectors of this 2D affine matrix
are of the same length.

## loose\_bounding\_box

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,72:::fn loose_bounding_box(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>?
```

 loose\_bounding\_box is a simple computation that returns a BoundingBox which
may not be the smallest possible.

## luminance

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,208:::fn luminance(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> Double
```

 luminance returns the relative luminance of this color for standard human vision.

## mix

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,198:::fn mix(self : <a href="gmlewis/fonts/draw#Color">Color</a>, c : <a href="gmlewis/fonts/draw#Color">Color</a>, t : Double) -> <a href="gmlewis/fonts/draw#Color">Color</a>
```

 mix linearly interpolates between this Color and `c` with mixing factor `t`.

## mul

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,131:::fn mul(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, m : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 mul multiplies this 2D affine matrix with another.

## mul\_without\_translation

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,153:::fn mul_without_translation(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, m : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 mul\_without\_translation multiplies this 2D affine matrix with another,
discarding the transation.

## normalize

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,255:::fn normalize(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 normalize scales the basis vectors of this 2D affine matrix
so that they have unit length.

## op\_mul

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,145:::fn op_mul(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, b : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 op\_mul multiplies two 2D affine matrices together, returning a new one.

## origin

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,245:::fn origin(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 origin translates the matrix such that the center of future
scale, rotate, and skew transformations will be `v`.

## overlaps\_bounding\_box

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,154:::fn overlaps_bounding_box(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>, box : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Bool
```

 overlaps\_bounding\_box returns true if any part of `box` overlaps this bounding box.

## pre\_mul

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,169:::fn pre_mul(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, m : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 pre\_mul multiplies another matrix `m` by this 2D affine matrix, then
stores and returns the result.

## pre\_mul\_without\_translation

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,184:::fn pre_mul_without_translation(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, m : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 pre\_mul\_without\_translation multiplies another matrix `m` by this 2D affine matrix,
discarding the translate, then stores and returns the result.

## reverse

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,125:::fn reverse(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
```

 reverse reverses this Anchor.

## rgba

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,23:::fn rgba(r : Double, g : Double, b : Double, a : Double) -> <a href="gmlewis/fonts/draw#Color">Color</a>
```

 rgba is a convenience function.

## rotate

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,208:::fn rotate(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, angle : Double) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 rotate rotates this 2D affine matrix by `angle` degrees.

## scale

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,224:::fn scale(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 scale scales this 2D affine matrix by `v`.

## scale\_scalar

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,234:::fn scale_scalar(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, s : Double) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 scale\_scalar scales this 2D affine matrix uniformly by `s`.

## set

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,182:::fn set(self : <a href="gmlewis/fonts/draw#Color">Color</a>, r : Double, g : Double, b : Double, a : Double) -> <a href="gmlewis/fonts/draw#Color">Color</a>
```

 set sets the RGBA components of this Color.

## size

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,65:::fn size(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
```

 size returns a vector representing the (width,height) of the bounding box.

## skew

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,214:::fn skew(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, angle : Double) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 skew skews the Y basis vector of this 2D affine matrix by `angle` degrees.

## stroke

```moonbit
:::source,gmlewis/fonts/draw/stroke.mbt,48:::fn stroke(color : <a href="gmlewis/fonts/draw#Color">Color</a>) -> <a href="gmlewis/fonts/draw#Stroke">Stroke</a>
```

 stroke is a helper function.

## text

```moonbit
:::source,gmlewis/fonts/draw/text.mbt,14:::fn text(text~ : String, font~ : <a href="gmlewis/fonts#Font">@gmlewis/fonts.Font</a>, align~ : <a href="gmlewis/fonts/draw#TextAlign">TextAlign</a> = .., size~ : Double = ..) -> <a href="gmlewis/fonts/draw#Graphic">Graphic</a>!<a href="gmlewis/fonts/draw#DrawError">DrawError</a>
```

 text generates a new Graphic (a Group of Group of compound\_paths) from a text
string and a font.

## to\_css\_hex\_string

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,255:::fn to_css_hex_string(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> String
```

 to\_css\_hex\_string returns a CSS-style hex string for this color.

## to\_css\_rgba\_string

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,273:::fn to_css_rgba_string(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> String
```

 to\_css\_rgba\_string returns a CSS-style "rgba()" string for this color.

## to\_css\_string

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,214:::fn to_css_string(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> String
```

 to\_css\_string returns a CSS-style string for this color.

## to\_hsva

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,293:::fn to_hsva(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> <a href="moonbitlang/core/array#Array">Array</a>[Double]
```

 to\_hsva converts this color to the HSVA color space, returning
\[hue, saturation, value, alpha\] in the range (0..1).

## to\_rgb8\_number

```moonbit
:::source,gmlewis/fonts/draw/color.mbt,283:::fn to_rgb8_number(self : <a href="gmlewis/fonts/draw#Color">Color</a>) -> UInt
```

 to\_rgb8\_number returns a bit-packed number in RGB8 format.

## to\_transform

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,362:::fn to_transform(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Transform">Transform</a>
```

 to\_transform converts this 2D affine matrix to a Transform.

## transform

```moonbit
:::source,gmlewis/fonts/draw/anchor.mbt,55:::fn transform(self : <a href="gmlewis/fonts/draw#Anchor">Anchor</a>, position~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., rotation~ : Double = .., scale~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = .., skew~ : Double = .., origin~ : <a href="gmlewis/fonts/draw#Vec2">Vec2</a> = ..) -> <a href="gmlewis/fonts/draw#Anchor">Anchor</a>
```

 transform provides a convenient API for a common task.

## translate

```moonbit
:::source,gmlewis/fonts/draw/affine-matrix.mbt,199:::fn translate(self : <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>, v : <a href="gmlewis/fonts/draw#Vec2">Vec2</a>) -> <a href="gmlewis/fonts/draw#AffineMatrix">AffineMatrix</a>
```

 translate translates this 2D affine matrix by position `v`.

## unit\_circle

```moonbit
:::source,gmlewis/fonts/draw/unit-circle.mbt,3:::fn unit_circle() -> <a href="gmlewis/fonts/draw#Group">Group</a>
```

 unit\_circle constructs a new Group representing a unit circle centered at the origin.

## unit\_square

```moonbit
:::source,gmlewis/fonts/draw/unit-square.mbt,3:::fn unit_square() -> <a href="gmlewis/fonts/draw#Group">Group</a>
```

 unit\_square constructs a new Group representing a unit square centered at the origin.

## vec2

```moonbit
:::source,gmlewis/fonts/draw/vec2.mbt,28:::fn vec2(x : Double, y : Double) -> <a href="gmlewis/fonts/draw#Vec2">Vec2</a>
```

 vec2 returns a new Vec2.

## width

```moonbit
:::source,gmlewis/fonts/draw/bounding-box.mbt,71:::fn width(self : <a href="gmlewis/fonts/draw#BoundingBox">BoundingBox</a>) -> Double
```

 width returns the width of the bounding box.
