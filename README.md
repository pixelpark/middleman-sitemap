middleman-sitemap
=================

Howto auto sitemap generation in middleman.

First of all, you need to have the **builder gem** installed.
You can do this via console:
```shell
gem install builder
```
or add to your **Gemfile**:
```ruby
gem "builder"
```
in your **config.rb** you need to require **'builder'**,

```ruby

require 'builder'
```
and remove the layout from your sitemap.xml via:
```ruby
page "/sitemap.xml", :layout => false
```

Next, create a **sitemap.yml** file in your **data** folder with this content:
```ruby
url: http://localhost:4567
```
and replace the url with your domain.
Next, copy the **sitemap.xml.builder** in your project root folder.
Now, start your middleman server, and take a look at **http://localhost:4567/sitemap.xml**

