
# Jekyll Overview

This site uses the Jekyll Theme. For more information on Jekyll, please see the subsections below.

## Demo

Live demo on Github Pages: [https://sighingnow.github.io/jekyll-gitbook](https://sighingnow.github.io/jekyll-gitbook)

[![Jekyll Themes](https://img.shields.io/badge/featured%20on-JekyllThemes-red.svg)](https://jekyll-themes.com/jekyll-gitbook/)

## Why Jekyll with GitBook

GitBook is an amazing frontend style to present and organize contents (such as book chapters
and blogs) on Web. The typical to deploy GitBook at [Github Pages][1]
is building HTML files locally and then push to Github repository, usually to the `gh-pages`
branch. It's quite annoying to repeat such workload and make it hard for people do version
control via git for when there are generated HTML files to be staged in and out.

This theme takes style definition out of generated GitBook site and provided the template
for Jekyll to rendering markdown documents to HTML, thus the whole site can be deployed
to [Github Pages][1] without generating and uploading HTML bundle every time when there are
changes to the original repo.

# Site Implementation 

## Basic File Types

There are five file types that should be edited to implement the functionality of this site. I will discuss them from most likely to edit to least likely to edit. 

### Posts, Pages, and Other files

These are the base files that make up the individual pages of the site. Before getting into their structure and content, there are a few dynamics to address.

1. In the left-hand menu, the content order will always be (1) `Home-page.md` (discussed below), (2) all files in the `_post` folder, (3) all files in the `_pages` folder, and (4) all files in the `_others` folder.

2. Within the `_post` folder, the individual markdown (`.md`) files are re-ordered based on the date in their name and NOT the data in the frontmater of the file. 
    - All `_post` files must be in the following format: `YYYY-MM-DD-Name_of_File.md`.
    - If it does not start with `YYYY-MM-DD-`it will not appear in the site.
    - As you can see, I have added files by category (year) with space for file addition.

#### Overall Markdown Format

**Frontmatter**

All files must begin with a 'frontmatter' section. Without this section, the markdown file will not be converted into html, and the page will not appear on the site. 

The standard frontmatter section for a `_post` is: 

```markdown 
---
title: 1 Foundational Readings
author: Graham Ambrose
date: 2026-06-20
category: Jekyll
layout: post
tag: 
  - Name of contributor 1
  - Name of contributor 2
  - ...
---
```

The `title` is what will appear in the left-hand menu and will be the heading for the rendered page.

The `author`, `date`, and `category` are not manditory but are nice for reference.

The `layout` should not change with the file type -- i.e., other and page should also use `post`

Finally, we will leverage `tag` to keep track of contributors' names. If a resource is added, the contributor's names should be added to the `-` list on a new line. This is leveraged to create the leader board in the `leaders.md` file.

**Basic Structure**

The overall structure of the page is the same as basic mark down. For example, the following code:

```markdown
# Heading #1
Text

---
## Heading #2
- Text
- Text

---
### Heading #3
1. Text
2. Text

---
#### Heading #4
1. Text
    - Text
    - Text
2. Text

---
##### Heading #5
Text

```

results in:

# Heading #1
Text

---
## Heading #2
- Text
- Text

---
### Heading #3
1. Text
2. Text

---
#### Heading #4
1. Text
    - Text
    - Text
2. Text

---
##### Heading #5
Text

**Resource Card**

The following is the template for all resource cards:

```markdown
> 
> ##### Add a Resource Here!
>
>🌐  **Link:** [Stand-in Link to Home Page](https://ambro034.github.io/Big_Book_of_Complex_Governance/)  
>
><i>Authors</i>
>
>Description of the resource here
>
> <div style="text-align: right"><i> submitted by YOU! </i></div>
```

Resulting in:

> 
> ##### Add a Resource Here!
>
>🌐  **Link:** [Stand-in Link to Home Page](https://ambro034.github.io/Big_Book_of_Complex_Governance/) 
>
><i>Authors</i>
>
>Description of the resource here
>
> <div style="text-align: right"><i> submitted by YOU! </i></div>

Each line should start with a `>`. If there is a return, you will need a new `>`. If there is a break in `>`,  it will result in a new card. For example:

```markdown
> 
> ##### Resource Here #1
> Text

> 
> ##### Resource Here #2
> Text
```

Results in:

> 
> ##### Resource Here #1
> Text

> 
> ##### Resource Here #2
> Text

## License

This work is open sourced under the Apache License, Version 2.0.

Copyright 2019 Tao He.
