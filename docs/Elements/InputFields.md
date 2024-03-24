---
title: Input Fields
layout: page
nav_order: 4
parent: Elements
---

# Input Fields

### Elements

| XI Element | UITK Element |
| ------------------------- |
| [XITextField](#xitextfield) | [TextField](https://docs.unity3d.com/Manual/UIE-uxml-element-TextField.html){:target="_blank" rel="noopener"} |
| [XIIntegerField](#xiintegerfield) | [IntegerField](https://docs.unity3d.com/Manual/UIE-uxml-element-IntegerField.html){:target="_blank" rel="noopener"} |
| [XIFloatField](#xifloatfield) | [FloatField](https://docs.unity3d.com/Manual/UIE-uxml-element-FloatField.html) |
| [XIVector2Field](#xivector2field) | [Vector2Field](https://docs.unity3d.com/Manual/UIE-uxml-element-Vector2Field.html){:target="_blank" rel="noopener"} |
| [XIVector3Field](#xivector3field) | [Vector3Field](https://docs.unity3d.com/Manual/UIE-uxml-element-Vector3Field.html){:target="_blank" rel="noopener"} |
| [XIVector4Field](#xivector4field) | [Vector4Field](https://docs.unity3d.com/Manual/UIE-uxml-element-Vector4Field.html){:target="_blank" rel="noopener"} |

---

## XITextField

An element that allows users to edit a string / line of text

#### Fields

| Field            | Type           | Description                           |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Value            | string         | Text value of the input field         |

#### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<string>    | Executed whenever the `Value` changes           |




## XIIntegerField

An element that allows users to edit an integer value

#### Fields

| Field            | Type           | Description                           |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Value            | int            | Integer value of the input field      |

#### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<int>       | Executed whenever the `Value` changes           |




## XIFloatField

An element that allows users to edit a float value

#### Fields

| Field            | Type           | Description                           |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Value            | float          | Float value of the input field        |

#### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<float>     | Executed whenever the `Value` changes           |




## XIVector2Field

An element that allows users to edit a Vector2 value

#### Fields

| Field            | Type           | Description                           |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Value            | Vector2        | Vector2 value of the input field      |

#### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<Vector2>   | Executed whenever the `Value` changes           |




## XIVector3Field

An element that allows users to edit a Vector3 value

#### Fields

| Field            | Type           | Description                           |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Value            | Vector3        | Vector3 value of the input field      |

#### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<Vector3>   | Executed whenever the `Value` changes           |




## XIVector4Field

An element that allows users to edit a Vector4 value

#### Fields

| Field            | Type           | Description                           |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Value            | Vector4        | Vector4 value of the input field      |

#### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<Vector4>   | Executed whenever the `Value` changes           |
