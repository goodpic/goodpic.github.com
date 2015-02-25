---
layout: post
title: Open GUI Emacs to create a new post for jekyll
published: true
categories: jekyll
---

I slightly updated [Rake task to create a new post of jekyll](http://en.goodpic.com/2015/02/25/new-post-from-rake-file.html). This will open the created new file with the GUI version of Emacs.

{% highlight ruby %}
  ENV['EDITOR'] ||= 'open -a /Applications/Emacs.app'
  exec("#{ENV['EDITOR']} #{file}")
{% endhighlight %}

I also followed [this post to enable yasnippets](http://calas.github.io/2009/11/20/using-yasnippets-in-markdown-mode.html) on Emacs markdown mode. Added this code to .emacs.el

{% highlight lisp %}
(defun markdown-unset-tab ()
  "markdown-mode-hook"
  (define-key markdown-mode-map (kbd "<tab>") nil))
(add-hook 'markdown-mode-hook '(lambda() (markdown-unset-tab)))
{% endhighlight %}

and finally add some aliases to .zshrc.

{% highlight bash %}
alias bxj="bundle exec jekyll"
alias bxjs="bundle exec jekyll server"
alias gpom="git push origin master"
alias gcm="git commit -m "
alias gaa="git add ."
{% endhighlight %}
