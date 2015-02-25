---
layout: post
title: New post from rake file
published: true
date:  2015-02-25 01:13:50
categories: jekyll
---

I added a simple rake task to create a new post. First I tried [this plugin](https://github.com/jekyll/jekyll-compose) but this seems only work with Jkyll 3.0 Beta.
Here is the rake file slightly modified from [this example](http://stackoverflow.com/questions/22687085/jekyll-simplest-possible-rakefile-to-create-new-post).

{% highlight ruby %}
require 'time'

desc 'create a new post'
task :post do
  title = ENV['title'] || "new-post"
  slug = "#{Date.today}-#{title.downcase.gsub(/[^\w]+/, '-')}"

  file = File.join(
                   File.dirname(__FILE__),
                   '_posts',
                   slug + '.markdown'
                   )

  File.open(file, "w") do |f|
    f << <<-EOS
---
layout: post
title: #{title}
date: #{Date.today.strftime(%Y-%m-%d %H:%M:%S)}
published: true
categories:
---
EOS
  end
  puts file
end
{% endhighlight %}
