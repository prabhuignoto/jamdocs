---
title: Props
date: 2018-09-15 07:42:34
slug: props
---

## dock

The `dock` property can be used to set the default dock position.

| Allowed Positions |
|------------------|
| `TOP`              |
| `RIGHT`            |
| `BOTTOM`           |
| `LEFT`             |

`TOP` is the default docking position when this prop is not set.

The following snippet docks the menubar to the `right`.

```bash
  <vue-dock-menu dock="RIGHT">
  </vue-dock-menu>
```

## draggable

Use this property to enable or disable dragging. Dragging is enabled by default.

The below snippet disables dragging on the Menubar

```bash
  <vue-dock-menu :draggable="false">
  </vue-dock-menu>
```

## items

Use the `items` prop to populate the menu. `items` should be a collection of [MenuItem](/menu-item-model) type.

```bash
<template>
  <vue-dock-menu :items="items">
  </vue-dock-menu>
</template>

<script>
  import { DockMenu } from "vue-dock-menu";
  import "vue-dock-menu/dist/vue-dock-menu.css";

  export default {
    name: "example",
    components: {
      DockMenu
    },
    data() {
      return {
        items = [
          {
            name: "File",
            menu: [{ name: "Open"}, {name: "New Window"}, {name: "Exit"}]
          },
          {
            name: "Edit",
            menu: [{ name: "Cut"}, {name: "Copy"}, {name: "Paste"}]
          }
        ]
      }
    }
  }
</script>
```

## on-selected

Use the `on-selected` callback to fetch the selected item.

The callback

```bash
<template>
  <vue-dock-menu :items="items" :on-selected="onSelected">
  </vue-dock-menu>
</template>

<script>
  import { DockMenu } from "vue-dock-menu";
  import "vue-dock-menu/dist/vue-dock-menu.css";

  export default {
    name: "example",
    components: {
      DockMenu
    },
    setup() {
      const onSelected = (data) => {
        console.log(data);
      }
      return  {
        onSelected
      }
    },
    data() {
      return {
        items = [
          {
            name: "File",
            menu: [{ name: "Open"}, {name: "New Window"}, {name: "Exit"}]
          },
        ]
      }
    }
  }
</script>
```