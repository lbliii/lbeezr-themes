---
title: emdash theme
date:
Description: "the emdash knowledge base theme."
author: Lawrence Lane
Tags: []
Categories: []
---


This article walks you through how to quickly get set up with [Hugo](http://gohugo.io/), a static site generator, to publish technical documentation in [Markdown](https://www.markdownguide.org/). This documentation toolchain works for organizations on any level, from open-source communities to enterprise-level tech giants.

Hugo is just one of many site generators that can be used. You're welcome to try others, such as [Jekyll](https://jekyllrb.com/), [Docusaurus](https://v2.docusaurus.io/), or [Gatsby](https://www.gatsbyjs.org/)---but Hugo is my personal favorite.

# Prerequisites

- Download a text/source-code editor. I recommend [Atom](https://atom.io/)
- Install the Markdown-Writer package for Atom & load its keybindings

---

# Set Up Hugo

## 1. Install Hugo

### Mac

1. Ensure that you have the package manager [Homebrew](https://brew.sh/) on your computer.
2. Open the terminal.
3. Run the following:
   ```shell
   brew install hugo
   ```
4. Verify your installation worked with the following command:
   ```shell
   hugo version
   ```

### Windows 10

1. Ensure that you have a package manager, such as [Chocolatey](https://chocolatey.org/), on your computer.
2. Open the Command Prompt.
3. Run the following"

    ```shell
    choco install hugo-extended
    ```
4. Verify your installation worked with the following command:

   ```shell
    hugo version
    ```

---

## 2. Create a New Site

The following steps create a folder with your site name which includes all of the basic assets needed to get started.

1. Open a terminal window.
2. Navigate to the folder you wish to create a new project in.
3. Run the following:

```shell
hugo new site [sitename]
```

Unsure of how to navigate across folders in the terminal? Jump to the [Terminal Tips](#terminal-tips) section.

---

## 3. Import a Theme

The quickest way to get started is to import an existing [theme](https://themes.gohugo.io/) that you can either use outright our modify to fit your needs.

### Find a Favorite Theme

1. Scroll through the themes and pick your favorite. Select **Demo** to preview a live version.
2. Navigate to GitHub by selecting **Download** on one of the theme pages.
3. Select the **Code** button.
4. Copy the URL provided under **Clone with HTTPS**.

### Clone the Theme

1. Open a terminal window.
2. Navigate to the `themes` folder in your project: **sitename** > **themes**.
3. Run the following:
```shell
git clone <your theme url>
git submodule update --init --recursive
```

This pulls the theme's information into your project for you to use and adds it to a `.gitmodule` file which directs your site to its resources when building.

---

## 4. Update Configuration

There are a few details we need to square away before you can preview your fresh, new site.

### Use the Example Site for Reference

Almost every Hugo theme comes with the demo site nested in its contents. This enables you to see how they built it. This also enables you to _copy_ the basic configuration in the `config.yaml` or `config.toml` file, and paste that content into your fresh, almost-empty `config` file.

1. Open your project in your text/source-code editor.
2. Expand the **themes** folder. Select the theme you installed.
3. Expand the **exampleSite** folder.
4. Open the **config** file.
5. Copy everything.
6. Navigate to your _project's_ **config** file. This is typically the last file at the bottom. It is not nested in any other folder.
7. Paste the content and save.

The structure of a config file can vary widely depending on two things: whether it's a `toml` or `yaml` file, and what features the theme has that need to be explicitly defined.

Here's the `yaml` config file for this site you're reading:

```yaml
baseURL: "https://lbeezr.com"
languageCode: "en-us"
title: "LBEEZR"
pygmentsstyle: 'monokai'
paginate: 6
social:
  github: "https://github.com/lbliii/"
  instagram: "https://www.instagram.com/lbeezr/"
  linkedin: "https://www.linkedin.com/in/mrlawrencelane/"
taxonomies:
  author: authors
    - Lawrence Lane
theme: "hugo-theme-novela"

```  

The novela theme I'm includes social media links, an author bio feature, and pagination for blog posts. You can see those defined here.

### Modify to Your Needs

1. Change the **`baseURL`** to your domain.
2. Change the **`title`** to the name of your website.
3. Change **`paginate`** rules if necessary.
4. Change the **`social`** links. Add/remove more (tiktok, etc) if supported by the theme.
5. Change the listed authors.

For this particular theme, **`author`** is a more complicated feature. It checks the filenames located in /content/authors/ against the author listed. That file contains additional information about the author, such as a bio and picture.

Here's what an author bio file might look like:

```yaml
---
title: Lawrence Lane
bio: I'm just a nugget trying to find the right dippin sauce.
avatar: /images/_index/author.png
featured: true
social:
  - title: github
    url: https://github.com/lbliii
  - title: instagram
    url: https://www.instagram.com/lbeezr/
hero: /images/_index/author.png
---
```

Remember, each theme may have different features that need setting up. What's most important to understand is the general framework --- how to define these features in your config file and, if necessary, across other project folders.

---

## 5. Create Content

Hugo typically requires that your pages exist in the **`content`** folder. It's also common for many blog-style themes to further separate your blog posts in a **`posts`** folder. Again, reference the _**exampleSite**_ found in **`/themes/your-theme/exampleSite/`**. You'll quickly get an idea of what is needed and where.

### Understand the Content Structure

Every folder in **`content`** needs a file named **`_index.md`**. This file is the dominant or introductory page for a given set of pages. We typically call this a parent-child relationship.

For example, a folder called _dogs_ might have sub-folders named _golden-retriever_, _poodle_, and _corgi_. All four of these must also have an **`_index.md`** file. They may have additional files as well, such as **`golden-retriever-adoption.md`**, **`poodle-grooming-tips.md`**, etc.

You can read a more thorough and advanced breakdown of how this works in [Hugo's documentation](https://gohugo.io/content-management/organization/).

### Understand Page Front Matter

Similarly to how you defined configuration in the config file, you must add important information to every content file that you create. This information is called front matter. Here's the front matter for this article:

```yaml
---
authors:
 - Lawrence Lane
date: 2020-07-18
title: How to Set Up Hugo for Documentation
hero: "/images/how-to-setup-hugo-for-documentation/set-up-hugo.png"
weight:
description: Learn how to setup your computer to leverage Hugo as part of a docs-as-code toolchain.
---
```
The kind of details needed in the front matter depend on your theme and features. Reference content files found in your theme's **_exampleSite_** to get an idea of what's required.  

**Note**: the three dashes before and after your front matter _are_ requried; they tell hugo to expect front matter.


### Add Your First Pages

1. Open your project in Atom.
2. Navigate to the **`content`** folder.
3. Create a new file.
4. Name the file **`_index.md`**.
5. Add front matter.
6. Write the body of your article using [Markdown syntax](https://www.markdownguide.org/cheat-sheet/).
7. Save.
8. Repeat for other pages if desired.

---

## 6. Preview Your Site

After you've configured your project and added some content, it's time to finally take a look and see what you've made. From this point on, you can always preview changes that you make using the steps below. Doing so provides you a fully-functional site that mimics how it will behave once launched publicly on a domain.

### Serve Your Site Locally

1. Open the terminal.
2. Navigate to your project folder.
3. Run the following command:
```shell
hugo server
```

If successful, you should get a printout that looks similar to this:

```h
lblane@MacBook-Pro emdash % hugo server

                   | EN  
-------------------+-----
  Pages            | 14  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  4  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 44 ms
Watching for changes in /Users/lblane/Documents/GitHub/emdash/{archetypes,content,themes}
Watching for config changes in /Users/lblane/Documents/GitHub/emdash/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

### View Your Site Locally

1. Open a web browser.
2. Navigate to the URL provided in the printout; typically `http://localhost:1313/`.

As long as your terminal window is active, any new files or changes saved in atom should update automatically in your localhost preview. If they do not update as expected, I recommend two things:

- Try a hard page refresh (cmd + shift + r)
- In the terminal window serving your site, execute the stop command (Ctrl + C) and restart it (hugo server)

---

## Summary

You now know how to do the following:

- Install Hugo on your local machine
- Use the terminal to execute Hugo CLI commands
- Use the terminal to navigate into your project folder
- Import a Hugo theme
- Define your configuration file
- Create content
- Preview your site locally

In the next article, we'll explore how to push this Hugo project into a [GitHub](https://github.com/) account, manage changes, and finally use a deployment service to publish your site online.

---

# Terminal Tips

- Use the command `cd [foldername]` to go _into_ a folder
- Use the command `cd ..` to go _backwards_ one folder.
- Use the command `cd [foldername]/[foldername]/[foldername]` to jump many levels deep more quickly.

{{< recent-posts >}}
