---
title: Dropdown
layout: page
nav_order: 6
parent: Elements
---

# Dropdown

| XI Element | UITK Element |
| ------------------------- |
| [XIDropdown](#xidropdown) | [DropdownField](https://docs.unity3d.com/Manual/UIE-uxml-element-DropdownField.html){:target="_blank" rel="noopener"} |

---

## XIDropdown

An element that allows the selection between multiple items.

### Fields

| Field   | Type           | Description                                    |
| ------------------------------------------------------------------------- |
| Label            | string         | Name of the field                     |
| Index            | int            | Current item index                    |
| Text             | string         | Current item text                     |
| Value            | string         | Current string text shown             |
| Choices          | List\<string>  | List of dropdown choice items         |

### Events

| Event                   | Description                                     |
| ------------------------------------------------------------------------- |
| ChangeEvent\<int>       | Executed whenever the `Index` changes           |
| ChangeEvent\<string>    | Executed whenever the `Text` changes            |
