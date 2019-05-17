---
title: "How to Setup Gh Pages"
date: 2019-05-15T14:08:56-05:00
draft: false
---
## GitHub repo creation

- Create git repo in github. For this example we will use "gh-pages".

## Setup

- Install hugo: https://gohugo.io/getting-started/installing

- Create site:
```
hugo new site gh-pages
cd gh-pages
```

- Initialize repo: 
```
git init
```

- Add theme as submodule, e.g. 
```
git submodule add https://github.com/mtn/cocoa-eh-hugo-theme themes/cocoa-eh-hugo-theme
```

- Copy config.toml template
```
cp themes/cocoa-eh-hugo-theme/exampleSite/config.toml .
```

- Modify `config.toml` to include: 
```
  baseurl = "https://pages.github.io/<username>/gh-pages/"
  ## OR org gh pages is enabled *and* domain has been verified, then use
  baseurl = "https://doxmx.org/gh-pages/"
  publishDir = "docs"
```

- Create content:
```
hugo
```

- Commit changes:
```
git add docs/** archetypes/** config.toml
git commit -m "First build" .
```

- Add remote repo:
```
git remote add origin git@github.com:<username>/gh-pages.git

## OR the org

git add remote origin git@github.com:doxmx/gh-pages.git
```

- Push changes: 
```
git push origin master
```


## Enabling GitHub Pages on the repository

- Enable GH pages https://github.com/&lt;username&gt;/gh-pages/settings
  Choose: Source: "master branch /docs folder"

- Page should be available at: https://pages.github.io/&lt;username&gt;/gh-pages/

  OR

- When using an org and a validated domain: https://doxmx.org/gh-pages/

## Adding a new page:

- Create a new post:
```
hugo new posts/how-to-setup-gh-pages.md
```

- Edit its content:
```
${EDITOR} content/posts/how-to-setup-gh-pages.md
```

- Build content:
```
hugo
```

- Verify content is displaying as intended:
```
hugo server -D
```

- Once happy the content is ready to be built, but first change the header from `draft: true` to `draft: false` and rebuild
```
hugo
```

- Commit the changes and push:
```
git add content/posts/how-to-setup-gh-pages.md docs/**
git commit -m "Create how to for gh pages" .
git push origin master
```


