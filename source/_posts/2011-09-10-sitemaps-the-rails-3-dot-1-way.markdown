---
layout: post
title: "Sitemaps: the rails 3.1 way"
date: 2011-09-10 19:07
comments: true
categories: [ruby, rails, web]
---

Having a sitemap for your website is a nice convention, it helps search engines find, index and build
an hierarchy of your pages and it also gives you some control of what content is parsed and how often.
At Ruby Studio we regard sitemaps as a mandatory aspect of development and SEO and always include them
in the apps we build, even if it’s a simple app with no much dynamic content, such as our
[current homepage](http://rubystudio.net/).

So what is our preferred method of incorporating sitemaps in rails applications? There is a really
easy way, by using a gem that is actively maintained and fully compatible with rails 3.1. As an extra
benefit, the gem is really well documented. It’s called [sitemap_generator](http://rubygems.org/gems/sitemap_generator).

Here’s how to get going with it in a few easy steps:

- Add `gem 'sitemap_generator'` to your Gemfile and run `bundle`. This will install the gem
- Run `rake sitemap:install` to setup the gem. This will generate a `config/sitemap.rb` file which is your
sitemap configuration descriptor file. You can run this task on your development machine and there will be
no need to repeat the process for production.
- Open your `sitemap.rb` file to define the pages you need included in your sitemap. Only the root home page
is included by default. In your `sitemap.rb` file you'll find initially a block of code:

``` ruby
SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
......
end
```
- Edit the file, inserting into the block the links to your pages or resources like this:

``` ruby
SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add '/contact_us'
  Content.find_each do |content|
    add content_path(content), :lastmod => content.updated_at
  end
end
```
As you can see from the example, static pages are added by a simple add declaration, and dynamic content can
be easily added by a nested block selector, polling your rails models and extracting blogs, articles or any
other dynamic assets you might have in your app. Neat and easy!

There are a number of supporter options you can add to your configuration to fine tune the crawling
frequency, priority, etc, such as:

``` ruby
add '/contact_us', :changefreq => 'monthly'
add '/about', :priority => 0.75
```

The full list is available in the [gem documentation](http://rdoc.info/github/kjvarga/sitemap_generator/master/frames).

- After writing the configuration, you’re ready to actually generate your sitemaps. Run `rake sitemap:refresh`.
This will create the sitemaps and put them in your public/ folder, appropriately compressing them with gzip
and naming them by default: `sitemap_index.xml.gz, sitemap1.xml.gz`, etc
- Next you should add the path to your sitemap in your `robots.txt` file, so that the spiders can find it
automatically: `Sitemap: http://www.example.com/sitemap_index.xml.gz`
- Upon a sitemap generation, the script automatically notifies (pings) major search engines (Google, Yahoo,
Bing, Ask, SitemapWriter) that a new sitemap is available. In development you can disable the notification
by using instead `rake sitemap:refresh:no_ping`
- That’s all, you’re now ready to rumble with your new shiny sitemaps. In production you can add a crontab
entry (either manually, or using the [whenever](http://rubygems.org/gems/whenever) gem) for the rake task
to automatically re-generate your sitemaps on, say, a daily basis. Here’s an example of raw crontab entry:

``` sh
0 5 * * * /bin/bash -l -c 'cd /path/to/webapp && RAILS_ENV=production rake -s sitemap:refresh --silent'
```
Or an example whenever entry:

``` ruby
# config/schedule.rb
every 1.day, :at => '5:00 am' do
  rake "-s sitemap:refresh"
end
```

The whole setup and deployment process takes some 15 minutes and is really flexible and configurable.
No more reasons to skip on this important part of search engine optimization and web development
best practices.
