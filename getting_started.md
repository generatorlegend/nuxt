---
title: Getting Started with Nuxt.js
description: Learn how to install Nuxt.js, create a new project, and start building your application
---

# Getting Started with Nuxt.js

Welcome to Nuxt.js! This guide will walk you through the process of setting up your first Nuxt.js project and introduce you to some basic concepts.

## Prerequisites

Before you begin, make sure you have the following installed on your system:

- Node.js (version 14.x or higher)
- npm (usually comes with Node.js) or yarn

## Installation

To create a new Nuxt.js project, you can use the `create-nuxt-app` command. Open your terminal and run:

```bash
npx create-nuxt-app my-nuxt-project
```

Replace `my-nuxt-project` with your desired project name.

## Project Setup

The installation wizard will ask you a series of questions to customize your project. Here are some key options:

1. Choose your preferred package manager (npm or yarn)
2. Select your UI framework (e.g., Tailwind CSS, Bootstrap, Vuetify)
3. Choose your preferred testing framework
4. Select additional features like TypeScript support or Progressive Web App (PWA) functionality

After answering these questions, the wizard will create your project and install the necessary dependencies.

## Project Structure

Once your project is created, you'll see a directory structure similar to this:

```
my-nuxt-project/
├── assets/
├── components/
├── layouts/
├── pages/
├── plugins/
├── static/
├── store/
├── nuxt.config.js
└── package.json
```

Here's a brief overview of each directory:

- `assets/`: Contains uncompiled assets like LESS, SASS, or JavaScript.
- `components/`: Vue components used in your pages.
- `layouts/`: Application layouts.
- `pages/`: Your application views and routes.
- `plugins/`: JavaScript plugins to run before instantiating the root Vue.js application.
- `static/`: Directly served static files.
- `store/`: Vuex store files.
- `nuxt.config.js`: Nuxt.js configuration file.

## Running the Development Server

To start the development server, navigate to your project directory and run:

```bash
cd my-nuxt-project
npm run dev
```

Your Nuxt.js application will now be running at `http://localhost:3000`.

## Basic Concepts

### Pages

Nuxt.js automatically generates routes based on the files in your `pages/` directory. For example:

- `pages/index.vue` will be accessible at `/`
- `pages/about.vue` will be accessible at `/about`
- `pages/posts/_id.vue` will be accessible at `/posts/:id`

### Layouts

Layouts are stored in the `layouts/` directory and can be used to change the look and feel of your app. The default layout is defined in `layouts/default.vue`.

### Components

Vue components in the `components/` directory are automatically imported and can be used in your pages without explicitly importing them.

### Nuxt Configuration

The `nuxt.config.js` file is where you configure various aspects of your Nuxt.js application, such as:

- Global CSS files
- Plugins to load
- Modules to use
- Build configuration

Here's a simple example of a `nuxt.config.js` file:

```javascript
export default {
  // Global page headers
  head: {
    title: 'My Nuxt.js Project',
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
    ],
  },
  
  // Global CSS
  css: [
    '~/assets/css/main.css'
  ],
  
  // Plugins to load before mounting the App
  plugins: [
    '~/plugins/my-plugin.js'
  ],
  
  // Auto import components
  components: true,
  
  // Modules for dev and build
  buildModules: [
    '@nuxtjs/eslint-module',
  ],
  
  // Modules
  modules: [
    '@nuxtjs/axios',
  ],
}
```

## Next Steps

Now that you have your Nuxt.js project set up, you can start building your application! Here are some suggestions for what to do next:

1. Create some pages in the `pages/` directory
2. Add a custom layout in the `layouts/` directory
3. Create reusable components in the `components/` directory
4. Explore Nuxt.js modules to add additional functionality to your app

For more detailed information, check out the [Nuxt.js documentation](https://nuxtjs.org/docs/get-started/installation).

Happy coding with Nuxt.js!