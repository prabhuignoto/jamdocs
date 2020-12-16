---
title: MenuItem Model
date: 2018-09-15 07:42:34
slug: menu-item-model
---

> The Menu item model represents a single menu item

<br />

### name

Name of the Menu item model.

```bash
type: String
```

### disable (optional)

Disables the Menu item.

```bash
type: Boolean
```

### isDivider (optional)

Adds a divider (separator) between the menu items.

```bash
type: Boolean
```

### menu (optional)

Adds a nested sub menu.

```bash
type: MenuItem  (self)
```
