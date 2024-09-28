# /admin

A local-first CMS generator and configuration management interface for any static site made with love, [Hugo](https://gohugo.io), NetlifyCMS, StaticJsCMS, and now SveltiaCMS, and based on [theNewDynamic's](https://www.thenewdynamic.com) [hugo-module-tnd-netlifycms](https://github.com/theNewDynamic/hugo-module-tnd-netlifycms). 

Admin can be extended to support any other static site generator or text-file-configured or fed software.

## Prerequisites
 - [ ] Hugo ([Installation instructions](https://gohugo.io/installation))

 - [ ] Git ([Installation instructions](https://github.com/git-guides/install-git))

 - [ ] A Hugo site tracked by Git
    ```bash
    hugo new site my-awesome-site
    cd my-awesome-site
    git init
    hugo mod init github.com/username/my-awesome-site

    # "Replacing my-awesome-site with your site directory, and username with yours. Don't worry, your site doesn't already have to be on GitHub."
    ```

## Installation
1. Import `github.com/basa-casa/admin` to your hugo config. 
1. Copy `/exampleSite/content/admin/_index.md` into your project
1. In your new file, modify the `cascade.config` object to reflect your project. This controls the static cms backend and other settings common to each sub-cms.

## Usage
### Getting Started
1. Run `hugo server`
1. Open [http://localhost:1313/admin/help](http://localhost:1313/admin/help)

### /admin

This is your blank slate! Most small sites will likely want all of their collections imported here. 

More docs to come!