---
title: 'Modules and Plugins Usage'
description: 'Learn how to use and create Nuxt.js modules and plugins, integrate third-party libraries, and extend Nuxt.js functionality.'
---

# Modules and Plugins Usage in Nuxt.js

Nuxt.js provides powerful ways to extend its functionality through modules and plugins. This guide will help you understand how to use existing modules, create custom plugins, and develop your own Nuxt.js modules.

## Table of Contents

1. [Understanding Modules and Plugins](#understanding-modules-and-plugins)
2. [Using Nuxt.js Modules](#using-nuxtjs-modules)
3. [Creating Custom Plugins](#creating-custom-plugins)
4. [Developing Nuxt.js Modules](#developing-nuxtjs-modules)
5. [Integrating Third-Party Libraries](#integrating-third-party-libraries)

## Understanding Modules and Plugins

Modules and plugins are two ways to extend Nuxt.js functionality:

- **Modules**: Modules are functions that run when Nuxt.js is initializing. They can customize the build process, add runtime hooks, and integrate external libraries.
- **Plugins**: Plugins are JavaScript files that run before instantiating the root Vue.js application. They are useful for adding Vue plugins, injecting functions or constants, and more.

## Using Nuxt.js Modules

To use a Nuxt.js module, you need to add it to the `modules` section in your `nuxt.config.js` file:

```javascript
export default {
  modules: [
    // Using package name
    '@nuxtjs/axios',
    
    // Relative to your project srcDir
    '~/modules/awesome.js',
    
    // Providing options
    ['@nuxtjs/google-analytics', { ua: 'UA-XXXXXXXX-X' }],
    
    // Inline definition
    function () { }
  ]
}
```

## Creating Custom Plugins

To create a custom plugin:

1. Create a new file in the `plugins` directory, e.g., `plugins/my-plugin.js`:

```javascript
export default ({ app }, inject) => {
  // Inject $myPlugin(msg) in Vue, context and store.
  inject('myPlugin', msg => console.log(`Hello ${msg}!`))
}
```

2. Add the plugin to the `plugins` section in `nuxt.config.js`:

```javascript
export default {
  plugins: ['~/plugins/my-plugin']
}
```

Now you can use `this.$myPlugin` in your Vue components.

## Developing Nuxt.js Modules

To create a Nuxt.js module, use the `defineNuxtModule` function:

```javascript
import { defineNuxtModule } from '@nuxt/kit'

export default defineNuxtModule({
  meta: {
    name: 'my-module',
    configKey: 'myModule'
  },
  defaults: {
    // Default options
  },
  setup (options, nuxt) {
    // Your module logic here
  }
})
```

This structure allows you to define meta information, default options, and the setup function for your module.

## Integrating Third-Party Libraries

To integrate a third-party library:

1. Install the library: `npm install some-library`

2. Create a plugin file, e.g., `plugins/some-library.js`:

```javascript
import Vue from 'vue'
import SomeLibrary from 'some-library'

Vue.use(SomeLibrary)
```

3. Add the plugin to `nuxt.config.js`:

```javascript
export default {
  plugins: ['~/plugins/some-library']
}
```

Now you can use the library in your Nuxt.js application.

Remember to consult the documentation of specific modules or libraries for detailed integration instructions, as they may have unique setup requirements.