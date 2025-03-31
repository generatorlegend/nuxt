---
title: Using Components in Nuxt.js
description: Learn how to create, use, and organize components in your Nuxt.js applications
---

# Using Components in Nuxt.js

Components are essential building blocks in Nuxt.js applications. They allow you to create reusable UI elements and organize your code more efficiently. This guide will walk you through the process of creating, using, and organizing components in your Nuxt.js projects.

## Auto-Import Feature

Nuxt.js provides an auto-import feature for components, which simplifies the process of using components in your application. When you create a component in the `components/` directory, Nuxt.js automatically imports and registers it for use throughout your application.

## Creating Components

To create a component:

1. Create a new `.vue` file in the `components/` directory.
2. Define your component using the standard Vue.js component structure.

Example:

```vue
<!-- components/MyButton.vue -->
<template>
  <button class="my-button" @click="handleClick">
    {{ text }}
  </button>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      default: 'Click me'
    }
  },
  methods: {
    handleClick() {
      this.$emit('button-click')
    }
  }
}
</script>

<style scoped>
.my-button {
  /* Add your styles here */
}
</style>
```

## Using Components

To use a component in your pages or other components, simply include it in your template. Thanks to the auto-import feature, you don't need to manually import the component.

Example:

```vue
<!-- pages/index.vue -->
<template>
  <div>
    <h1>Welcome to my Nuxt.js app</h1>
    <MyButton text="Click me!" @button-click="handleButtonClick" />
  </div>
</template>

<script>
export default {
  methods: {
    handleButtonClick() {
      console.log('Button clicked!')
    }
  }
}
</script>
```

## Component Organization

Nuxt.js provides flexibility in organizing your components. Here are some best practices:

1. **Flat structure**: For smaller projects, you can keep all components in the root of the `components/` directory.

2. **Nested directories**: For larger projects, you can create subdirectories to group related components:

   ```
   components/
   ├── ui/
   │   ├── Button.vue
   │   └── Input.vue
   ├── layout/
   │   ├── Header.vue
   │   └── Footer.vue
   └── features/
       ├── UserProfile.vue
       └── ProductList.vue
   ```

   Nuxt.js will automatically import components from nested directories, maintaining the directory structure in the component names. For example, `ui/Button.vue` would be used as `<UiButton />`.

3. **Global components**: Place components that are used across multiple pages in the `components/global/` directory. These components will be automatically registered as global components.

## Lazy-Loading Components

For performance optimization, you can lazy-load components that are not immediately needed. To do this, prefix the component name with `Lazy` when using it:

```vue
<template>
  <div>
    <h1>Welcome to my Nuxt.js app</h1>
    <LazyMyHeavyComponent v-if="showHeavyComponent" />
  </div>
</template>
```

This will only load the component when it's needed, improving initial page load times.

## Best Practices for Component Reusability

1. **Keep components small and focused**: Each component should have a single responsibility.
2. **Use props for configuration**: Make your components flexible by accepting props for customization.
3. **Emit events for communication**: Use custom events to communicate changes to parent components.
4. **Use slots for flexible content**: Utilize slots to allow parent components to inject custom content.
5. **Document your components**: Add comments or use JSDoc to describe your component's props, events, and usage.

By following these guidelines and leveraging Nuxt.js's powerful component system, you can create maintainable and efficient applications with reusable UI elements.