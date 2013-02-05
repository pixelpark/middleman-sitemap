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

## html sitemap
If you need a sitemap or list of all your middleman pages, then you create a **sitemap.html.erb** with the following content:

```ruby
<% root_url = data.sitemap.url %>
<ul>
    <% sitemap.resources.each do |page| %>
        <% if page.url =~ /\.html/ %>
            <li><a href="<%= "#{root_url}#{page.url}" %>"><%= "#{root_url}#{page.url}" %></a></li>
        <% end %>
    <% end %>
</ul>
```

If you dont wanna have layout at this page, dont't forget to add:
```ruby
page "/sitemap.html", :layout => false
```
to your **config.rb**.