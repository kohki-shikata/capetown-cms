# Capetown CMS Architecture

**Capetown** is a modern, modular CMS designed to embrace the needs of the next generation of web development. It is built with flexibility and extensibility in mind, offering a robust override system that allows developers to customize core functionality without directly modifying it. Capetown is developed to ensure compatibility with WordPress data, allowing for seamless migration from WordPress.

See also [READ ME](../../README.md).

## Overview

Capetown CMS aims to redefine content management by providing:

- **A Future-Ready Architecture**: Built on top of Laravel, Capetown leverages a modular architecture, giving developers the flexibility to update the core system while maintaining custom features through a clear, organized override system.
- **WordPress Data Compatibility**: Capetown is being developed to support compatibility with WordPress data structures, enabling developers to transition from or integrate with WordPress seamlessly.
- **Customizable and Extensible**: With a focus on customization, Capetown allows you to override core controllers, views, and configurations effortlessly.
- **Modular Design**: Capetown is built with the idea that every component, whether themes or plugins, should be modular and easily replaceable or extendable without affecting core functionality.

## Features

### Core Features
- **Overridable Controllers & Views**: Customize or replace core logic and presentation without altering the Laravel core.
- **Modular Theme Management**: Manage themes in a clean, organized fashion, with user-defined themes overriding default ones.
- **Plugin System**: Inspired by WordPress hooks and filters, Capetown aims to offer flexible plugin-based customization.
- **SEO Customization**: Built-in support for managing SEO metadata, optimized for modern search engines.
- **Form system**: Create custom forms with ease, store submissions in the database, and send them to administrators via email for quick review.

### Future Features
- **Hooks & Filters**: A full-fledged system for extending Capetown’s functionality, similar to WordPress's powerful hooks.
- **Multi-Site Support**: Seamlessly manage multiple websites or domains from one Capetown instance.
- **Custom Post Types**: Flexible custom post type management for structured content (planned).
- **WordPress Importt**: Support for importing WordPress data, making migration straightforward.

## License

Capetown CMS is an open-source project, released under the [MIT license](../LICENSE). We welcome contributions and feedback to help shape this CMS into a powerful and modern solution for web development.

# Capetown CMS - Architecture Overview

>[!NOTE]
>This section is under consideration.

Capetown CMS is designed with a modular and extensible architecture, ensuring flexibility for developers while maintaining a strong foundation in Laravel. This document outlines the core concepts and structural organization of Capetown CMS, focusing on the extendability and customizability through the use of modular components.

## Core Principles

1. **Modularity**: Every feature in Capetown, from themes to plugins and core functionality, is modular. This allows developers to extend or override specific components without affecting the overall system integrity.
   
2. **Override Mechanism**: Capetown provides a robust override system for controllers, views, and configuration files. This system ensures that the core framework remains untouched while allowing users to build custom functionality on top of it.

3. **Compatibility with WordPress Data**: Capetown is developed with the goal of maintaining compatibility with WordPress's data structures, enabling easy migration and integration for existing WordPress users.

## High-Level Architecture

### 1. Core Structure
The core of Capetown CMS is built on top of the Laravel framework, with custom extensions to allow for overriding core functionalities. Key components include:

- **Controllers**: Responsible for handling HTTP requests. These can be overridden by user-defined controllers located in the `app/Http/Controllers` directory.
- **Models**: Data interactions are handled through Laravel's Eloquent ORM, providing a powerful abstraction for database management.
- **Views**: Blade templates are used for rendering HTML, and user-defined views in themes can override default views.
  
### 2. Override System
Capetown’s override system allows users to customize controllers, views, and configurations. The override mechanism follows a layered approach:

1. **Laravel Core**: The base system remains intact and is located in the `vendor` directory.
2. **Capetown Core**: Extensions and customizations provided by Capetown are located in the `capetown/` directory. These are intended as extensions to the Laravel framework.
3. **User Overrides**: The user-defined components that override Capetown’s core logic reside in the `app/` directory.

For example, if a user wishes to override a core controller, they simply define a new controller in `app/Http/Controllers/`, and the Capetown system will automatically prioritize the user’s version over the core.

### 3. Theme Management
Capetown supports full theme customization through a clean and structured theme management system.

### 4. Plugin System (Planned)
Capetown will introduce a plugin system inspired by WordPress's hooks and filters, allowing developers to add or modify functionality without touching the core code. This system will include:

- **Actions**: Allow developers to inject additional functionality at specific points in the system.
- **Filters**: Enable modification of data before it is rendered or processed.

## Configuration Management

Capetown uses a hybrid approach for configuration management. While most configuration files reside in the `config/` directory, certain settings can be stored and managed in the database for dynamic updates.

## Future Features and Architecture

Capetown CMS is designed with the future in mind. Below are key features planned for future releases, along with their architectural implications:

### 1. Hooks & Filters (Planned)
Capetown will implement a system of hooks and filters, similar to WordPress, to allow developers to extend or modify the system's behavior without directly modifying the core code.

- **Hooks**: Provide a way to run custom code at specific points during execution (e.g., when saving a post).
- **Filters**: Allow modification of data (e.g., modifying post content before it is displayed).

### 2. Multi-Site Support (Planned)
Capetown will support multi-site installations, where administrators can manage multiple websites from a single Capetown instance. Each site will be differentiated by its domain or subdomain.

- **Architecture**: Multi-site support will involve extending Laravel's routing and database systems. Each site will have its own configurations, themes, and potentially unique database tables.
- **User Management**: Administrators will have the ability to manage user roles and permissions across different sites.

### 3. Custom Post Types (Planned)
Capetown will introduce custom post types, providing users with the flexibility to create structured content (e.g., portfolios, testimonials) in addition to the standard blog posts.

- **Architecture**: Custom post types will be managed through configuration files or the admin panel and will be stored in dedicated database tables, allowing for full customization of fields, taxonomies, and relationships.

## Directory Structure

Here’s an example of the expected directory structure for a typical Capetown installation:

**This is under consideration. NOT FINALIZED!**

```
/root-dir/
├─ /app # The area where users can freely customize and override
│  ├─ /themes
│  │  ├─ /default_theme       # If same name of theme exists, overrides core theme
│  │  └─ /user_theme       # Of course, users can freely create their original theme.
│  └─ /plugins       # Plugins provide additional functions beyond the standard functions of Capetown CMS.
│     ├─ /plugin-a
│     └─ /plugin-made-by-user
├─ /core # The user must never update or delete any files below this area.
│  ├─ /capetown       # The core features of Capetown CMS. The newer version of this app is installed in this directory with the new version number.
│  │  └─ /capetown-0.2.0
│  │     ├─ /themes
│  │     │  └─ /default_theme
│  │     └─ /plugins
│  └─ /laravel       # The basement of Capetown of Laravel core packages. The newer version of laravel is installed in this directory with the new version number.
│     ├─ /laravel-11.0.2
│     └─ /laravel-12.0.0
├─ /media       # Binary files uploaded by users are automatically stored in directories with three levels of random names, making it difficult to guess other filenames and file paths.
│  └─ /1012
│     └─ /2093
│        └─ /8977
│           └─ /user-uploaded.png
├─ /cache
└─ /config
   └─ /capetown.php       # Capetown CMS's config file.

```

### Key Directories:
- **app/**: Contains user-defined overrides for controllers and service providers.
- **capetown/**: The core Capetown CMS logic, including the default controllers, future plugin system, and other core components.
- **config/**: Configuration files for Capetown, including global settings and theme-related configurations.
- **resources/views/**: Stores themes and view templates, allowing user-defined theme overrides.
- **database/migrations/**: Handles database migrations for core tables and future plugin integrations.

## Conclusion

Capetown CMS is designed to offer developers a flexible and modular system that can be easily extended, customized, and maintained. With features like a robust override system, future multi-site support, and WordPress data compatibility, Capetown aims to be a powerful tool for modern web development.
