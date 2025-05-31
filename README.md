# /admin

A local-first CMS generator and configuration management interface for static sites, built with [Hugo](https://gohugo.io). It supports Decap CMS (formerly NetlifyCMS), StaticJsCMS, and SveltiaCMS, and is based on [theNewDynamic's](https://www.thenewdynamic.com) [hugo-module-tnd-netlifycms](https://github.com/theNewDynamic/hugo-module-tnd-netlifycms).

Admin can be extended to support any other static site generator or text-file-configured or -fed software.

## Prerequisites
- Hugo (version 0.130.0 or higher) ([Installation instructions](https://gohugo.io/installation))
- Git ([Installation instructions](https://github.com/git-guides/install-git))
- A Hugo site tracked by Git. To create one:
    ```bash
    hugo new site my-awesome-site
    cd my-awesome-site
    git init
    hugo mod init github.com/username/my-awesome-site
    # Replace my-awesome-site with your site directory, and username with yours.
    # Your site doesn't need to be on GitHub yet.
    ```

## Installation
1. Import the module into your Hugo site's configuration. Add `github.com/basa-casa/admin` to your `module.imports`.

   Example for `hugo.toml` (or `config.toml`):
   ```toml
   [module]
     [[module.imports]]
       path = "github.com/basa-casa/admin"
   ```
   Example for `config.yaml` (or `config.yml`):
   ```yaml
   module:
     imports:
       - path: github.com/basa-casa/admin
   ```
2. Copy the example admin page and its configuration from `exampleSite/content/admin/_index.md` into your project's `content/admin/` directory.
3. In your new `content/admin/_index.md` file, modify the `cascade.config` object in the front matter. This object is a Hugo front matter cascade block that defines settings for the admin panel. It controls which static CMS backend is used (e.g., Decap CMS, SveltiaCMS) and configures global settings for the admin interface and its sub-sections.

## Usage
### Getting Started
1. Run `hugo server`
1. Open [http://localhost:1313/admin/help](http://localhost:1313/admin/help)

### /admin

This is your blank slate! Most small sites will likely want all of their collections imported here.

### Custom Output Formats
The admin module defines several custom output formats in its `config.yml` that can be utilized within your Hugo site:
- **`help`**: Accessible via `/admin/help`, this format likely provides help documentation and guidance for using the admin panel.
- **`scms_debug`**: This format is probably used for debugging CMS configurations. You might access it via a path like `/admin/scms_debug.yml` (or similar, depending on your setup) to inspect generated configurations.
- **`scms_config`**: This could be used for exporting or viewing the main CMS configuration in YAML format (e.g., `config.yml` for SveltiaCMS or Decap CMS).
- **`scms_field`**: This format might relate to rendering or inspecting individual field configurations within the CMS, potentially useful for dynamic form generation or validation.

These formats allow for flexible interaction with the CMS configuration and admin panel functionalities.

### YAML Support
The module's `config.yml` also registers `application/yaml` with the `yml` suffix. This means you can use `.yml` files for your configurations, which is often preferred for its readability.

## JSON Schema for Configuration

The project uses JSON Schemas, located in the `src/schemas/` directory (e.g., `adminPage.schema.json`), to define the structure and validation rules for its configurations. These schemas are crucial for:
- Ensuring that configuration files (like the `cascade.config` in your `content/admin/_index.md`) are correctly structured.
- Potentially driving the generation of forms or providing contextual help within the admin interface.
- Enabling autocompletion and validation in code editors that support JSON Schema.

It's important to keep these schemas up-to-date with the evolving features of the CMS backends (Decap CMS, SveltiaCMS, etc.) and any custom configurations you introduce.

> When extending or modifying admin panel configurations, please review and update the relevant JSON Schema files in the `src/schemas/` directory (primarily `adminPage.schema.json`). Ensure the schemas include all pertinent JSON Schema options for each property, such as `type`, `enum`, `pattern`, `description`, `default`, and `examples`. Cross-reference the latest documentation from Decap CMS and SveltiaCMS repositories to incorporate any new properties or changes. Aim for comprehensive, accurate schemas that follow best practices.