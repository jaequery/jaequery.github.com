---
layout: post
title: "Pagination in Ruby on Rails"
date: 2013-02-08 11:16
comments: true
categories: rails
---

I haven't tried it out yet but it looks like Rails uses a gem called "kaminari" for dealing with pagination.
Here is a nice video tutorial on usage at [Railscast](http://railscasts.com/episodes/254-pagination-with-kaminari)

Basically it involves doing:

- Bash

`
bundle
rails g kaminari:views default
`

- update Gemfile to include the kaminari gem

`
gem 'kaminari'
`

- update controller (products_controller.rb)

`
@products = Product.order("name").page(params[:page]).per(5)
`

- update locales (config/locales/en.yml)

```
en:
  hello: "Hello world"
  views:
    pagination:
      previous: "&lt; Previous"
      next: "Next &gt;"
      truncate: "..."
```

- print pagination from view (products/index.html.erb)

`
<%= paginate @products %>
`
