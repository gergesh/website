# NewPipe Website Generator

Repo for the [NewPipe website](https://newpipe.schabi.org/), which includes the blog and the press kit.

All sites are based on [Bootstrap](https://getbootstrap.com) 3.3.7 and [Jekyll](https://jekyllrb.com/) 3.7.2.


## Development

#### Installation
Install Jekyll and Bundler gems through RubyGems:
```
~ $ gem install jekyll bundler
```

Navigate to the root directory of this project, dev environment:
```
bundle install
```

Navigate to this directory and build the site on the preview server:
```
~ $ jekyll serve
```

Run http://localhost:4000/blog or http://localhost:4000/press.

#### General

As this repository includes the press kit and the blog, we prefix all layouts and includes with either `press_` or `blog_`.

## Documentation

#### Categories / Tags
 
We do not make a difference between categories and tags, but only use categories.
Categories are used to tag posts, so they can be found easier.
Every tag has an overview page where you can find all posts with this tag.
Tags are also recognized as keywords by the search and posts get with these tags get an extra boost and are listed higher.
 
You can add a category / tag in the YAML header of each page:
 
 
`categories: category1`
 
`categories: [category1, category2, category3]`
 
Post with tags get the following permalink: `/blog/category1/category2/title`
 
These categories are implemented right now:
 
- release
- announcement
- talk
- download
- pinned
 
Every post which has the `announcement` category will also be shown in `press/announcements/`.

Posts with the `pinned` category appear on the right sidebar as _Also interesting_.

New categories can be implemented via an extra HTML page named `categoryName.html` and placed in `blog/`.
The new page should look like this:
 
```
---
layout: blog_category
title: categoryName
category: categoryName
---
```


##### Post thumbnails

Post thumbnails which are going to be displayed at the left side of the post, need to be registered in [_data/images.yml](_data/images.yml) (see [Image metadata](#image-metadata) to learn how to do this correctly). Thumbnails should be squarisch.

`image`          - Displays an image at the left side of the post. Use the key you registered in [_data/images.yml](_data/images.yml).

`imageHidePress` - Hides the image in the announcement page of the pres kit.


#### Image metadata

Image metadata can be set in [_data/images.yml](_data/images.yml). Ypu can display an image in a post with following snippet: 

`<img src="/img/{{ site.data.images[IMAGE_NAME].url }}" />`

``` YML
newpipe-beta:                          # IMAGE_NAME which is used to display it
  url: logo_app_beta.svg               # path to the file relative to '/img/'
  type: svg                            # file extension like 'svg', 'png' or 'jpeg'
  size: 16583                          # file size of the image in bytes
  name: NewPipe Beta logo              # image description 
  author: Schabi                       # author
  origin: https://github.com/theScrabi # optional: link to the origin of this image when it is not created by one of our teeam members
  download: /press/logo/#logo-beta     # optional: this is a link to the internal download page with an anchor to the download form '/press/logo/#logo-beta'
```


##### Page metadata

`metatitle` - The title to display in the browser `<title></title>`

`metades`   - The description to display as `<meta name="description">`

`metakey`   - Additional keywords for search engines `<meta name="keywords">`

`modified`  - The date the page was last modified. It will be displayed at the bottom of each page. Format `YYYY-MM-DD HH:MM:SS +/-TTTT`


##### Search

At the moment there is one search engine for the press kit and another one for the blog.

The variable `search` accepts following values wich modify the position in the search results:

`exclude`   - exclude the whole page from the search
