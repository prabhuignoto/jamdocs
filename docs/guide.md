---
title: Guide
date: 2018-09-15 07:42:34
slug: guide
---

### ⚡ Populating the Menu

Use the `items` prop to create simple or nested menus of your liking.

Please refer [MenuItemModel](/menu-item-model) for a complete list of menu item properties.

- To include a divider, set an empty item object with `isDivider` property set to `true`.
- To disable an item, set `disable` to `true`.

Here we create a simple menu structure with `Edit` and `Open Recent` having sub menus.


```bash
  <template>
    <vue-dock-menu>
      :items="items"
    </vue-dock-menu>
  </template>

  <script>
    import { DockMenu } from "vue-dock-menu";
    import "vue-dock-menu/dist/vue-dock-menu.css";

    export default defineComponent({
      name: "MenuExample",
      components: {
        DockMenu
      },
      data()  {
        return {
          items: [
            { name: "New" },
            { isDivider: true },
            {
              name: "Edit",
              menu: {
                name: "edit-items",
                disable:  true
              },
            },
            { isDivider: true },
            {
              name: "Open Recent",
              menu: {
                name: "recent-items",
              },
            },
            { isDivider: true },
            { name: "Save", disable: true },
            { name: "Save As..." },
            { isDivider: true },
            { name: "Close" },
            { name: "Exit" },
          ]
        }
      }
    })
  </script>
```

<br />

### 🎨 Custom color scheme

use the `theme` prop to customize the colors of the menu bar.

```bash
  <vue-dock-menu
    :items="items"
    :on-selected="selected"
    :theme="{
      primary: '#001B48',
      secondary: '#02457a',
      tertiary: '#018abe',
      textColor: '#fff'
    }"
  />
```

| Property  | Description                               |
|-----------|-------------------------------------------|
| `primary`   | changes the primary color of the menubar  |
| `secondary` | prop to change the menu color.            |
| `tertiary`  | modifies the hover color of the menu item |
| `textColor` | text color of the menu item when hovered. |

<br />

### 🎭 Icon support

Each menu item can be iconified and the component uses slots to inject the icons.

Pass individual icons (or images) as templates marked with a unique `slot id`. please make sure the `ids` match the  `iconSlot` property in the items array.

```bash
<template>
  <vue-dock-menu
    :items="items"
    :on-selected="selected"
  >
    <template #file>
      <img
        src="../assets/file.svg"
        alt="file"
        :style="style"
      >
    </template>
    <template #window>
      <img
        src="../assets/window-maximize.svg"
        alt="file"
        :style="style"
      >
    </template>
  </vue-dock-menu>
</template>

<script>
  import { DockMenu } from "vue-dock-menu";
  import "vue-dock-menu/dist/vue-dock-menu.css";

  export default defineComponent({
    name: "MenuExample",
    components: {
      DockMenu
    },
    data()  {
      return {
        items: [
          { name: "New File", iconSlot: "file" },
          { name: "New Window", iconSlot: "window" },
        ]
      }
    }
  })
</script>
```

This works seamlessly even for `nested` menu structure. Make sure the `slot ids` match and the component will render the icons appropriately.

```bash
<vue-dock-menu
  :items="items"
  :on-selected="selected"
>
  <template #window>
    <img
      src="../assets/window-maximize.svg"
      alt="file"
      :style="style"
    >
  </template>
</vue-dock-menu>

<script>
  import { DockMenu } from "vue-dock-menu";
  import "vue-dock-menu/dist/vue-dock-menu.css";

  export default defineComponent({
    name: "MenuExample",
    components: {
      DockMenu
    },
    data()  {
      return {
        items: [
          { name: "New File",
          subMenu: [{ name: "New Window", iconSlot: "window" }]},
        ]
      }
    }
  });
</script>
```
