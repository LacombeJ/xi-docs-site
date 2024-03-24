---
title: Radio Button
layout: page
nav_order: 7
parent: Elements
---

# Radio Button

| XI Element | UITK Element |
| ------------------------- |
| [XIRadioButton](#xiradiobutton) | [RadioButton](https://docs.unity3d.com/Manual/UIE-uxml-element-RadioButton.html){:target="_blank" rel="noopener"} |
| [XIRadioButtonGroup](#xiradiobuttongroup) | [RadioButtonGroup](https://docs.unity3d.com/Manual/UIE-uxml-element-RadioButtonGroup.html){:target="_blank" rel="noopener"} |

---

## XIRadioButton

An element that can be pressed to toggle on.

### Fields

| Field   | Type           | Description                                    |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Value            | bool           | Boolean value of the radio button     |

### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<bool>     | Executed whenever the `Value` changes            |




## XIRadioButtonGroup

An element that contains a selection of radio buttons where one can be selected as an option.

### Fields

| Field   | Type           | Description                                    |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Index            | int            | Current item index                    |
| Text             | string         | Current item text                     |

### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<int>       | Executed whenever the `Index` changes           |
| ChangeEvent\<string>    | Executed whenever the `Text` changes            |

