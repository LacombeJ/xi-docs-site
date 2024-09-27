---
title: Console
layout: page
nav_order: 11
parent: Elements
---

# Console (Experimental)

| XI Element              | UITK Element                  |
| ----------------------- | ----------------------------- |
| [XIConsole](#xiconsole) | Console (xi provided element) |

The `Console` UITK element is part of the XI namespace.

---

## XIConsole

A console display that shows Unity log messages. This element is experimental and in development. It currently does not implement virtualization or memory management.

### Fields

| Field      | Type | Description                                   |
| ---------- | ---- | --------------------------------------------- |
| UnityLog   | bool | Console should log and display unity messages |
| Collapse   | bool | Console should collapse log messages          |
| MaxEntries | bool | Maximum number of log messages displayed      |

### Events

*(none)*
