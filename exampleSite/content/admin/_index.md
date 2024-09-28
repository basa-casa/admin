---
title: Admin
collections:
  - import: collection admin
    collection_type: import
menus: 
  - admin
  - adminHelp
# CMS.md files beneath this one inherit these options
cascade:
  cms: https://unpkg.com/@sveltia/cms/dist/sveltia-cms.js # The JS CMS that reads Netlify CMS-descendant config.yml files. Decap requires adding local backend configuration in conifg.backend below. https://unpkg.com/decap-cms@^3.0.0/dist/decap-cms.js #
  outputs:
    # The CMS page
    - HTML 
    # the config: key turns into a config.yml file
    - scms_config 
    # The markdown below the frontmatter printed to {{ .filename }}/help/index.html and 
    - help 
  config: # Common settings for each CMS config.yml file. Override in individual {{CMS}}/index.md file.
    backend:
      branch: main
      name: github
      repo: basa-casa/admin
    media_folder: assets/img
    public_folder: img
    site_url: ../../
    display_url: /
    logo_url: "/img/admin.png"
draft: false
---
Welcome to `/admin/help`!
