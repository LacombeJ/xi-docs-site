---
title: Heading
layout: page
nav_order: 10
parent: Elements
---

# Heading

| XI Element | UITK Element |
| ------------------------- |
| [XIHeading](#xiheading) | Heading (xi provided element) |

The `Heading` UITK element is part of the XI namespace.

---

## XIHeading

A label element that displays a heading with a size and layout margins based on the level. When the level is set on a heading, that element gets applied with the corresponding class name. For example, if the level is "2" the element will have a class of `.h2` which can also be accessed with selector `Heading.h2`.

### Fields

| Field   | Type           | Description                                    |
| ------------------------------------------------------------------------- |
| Text             | string         | String that the heading displays      |
| Level            | int            | Integer from 1-6 that determines the heading class |


### Events

*(none)*

