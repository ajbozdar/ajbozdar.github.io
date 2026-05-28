---
# lang: [zh, ru, ar]
layout: post
title: Give a title
slug: set permalink here
date: YYYY-MM-DD HH:MM
lastmod: YYYY-MM-DD HH:MM
excerpt: Write an excerpt
image: '/images/add-image-path'
categories: [Language, Science, Technology, Engineering, Mathematics, Essay, Anecdote]
tags: [workflow, hobby, study]
# code: true
# math: true
# sticky: true
# hidden: true
---
## why multiple ruby versions
https://stackoverflow.com/questions/5213878/two-versions-of-ruby-installed-how-to-fix-tha
Mac OS 10.6 installs Ruby 1.8.7 for its own use. You're free to use it, but understand that Apple put it there for a reason, and modifying or removing it could break the app it's supporting, which you probably won't realize until some point in the future when you've forgotten what you did. Try: find /usr -name '*.rb' to see for yourself. As recommended below, use RVM to manage your Ruby installs.

https://developer.fedoraproject.org/tech/languages/ruby/ruby-installation.html

https://larrysanger.org/2019/01/how-to-delete-ruby-and-rails-and-other-gems-from-ubuntu-18-04/
# HOW TO DELETE RUBY AND RAILS (AND OTHER GEMS)
apt-get purge ruby2.5
aptitude purge ruby
rm -rf /usr/local/lib/ruby
rm -rf /usr/lib/ruby
rm -f /usr/local/bin/ruby
rm -f /usr/bin/ruby
rm -f /usr/local/bin/irb
rm -f /usr/bin/irb
rm -f /usr/local/bin/gem
rm -f /usr/bin/gem

rm -rf /home/radicalbee/.gem/ruby
rm -rf /home/radicalbee/.codeintel/db/ruby
rm -rf /usr/local/bin/rails
rm -rf /var/lib/gems/
rm -rf /home/radicalbee/.bundle/
rvm implode
rm -rf ~/.rvm
unset rvm_path
# THEN DO THIS TO MAKE SURE YOU'RE CLEAN:
# sudo find / -name 'rvm' -name 'rbenv' -name 'ruby' -name 'rails' -name 'gem'
# sudo find / -name 'rbenv'
# sudo find / -name 'ruby'
# sudo find / -name 'rails'
# sudo find / -name 'gem'
# sudo find / -name 'railties'
# cat ~/.bash_profile ~/.bashrc ~/.profile ~/.zshrc ~/.mkshrc ~/.zlogin | grep 'rvm\|rbenv\|ruby\|rails\|gem\|railties' # search for keywords in your bash profiles--they might need to be deleted
# env | grep rvm_path # ensure it's unset


$ sudo dnf install @development-tools
  Now install ruby using rbenv then
$ sudo dnf install ruby-devel zlib-devel

E-E-A-T stands for Experience, Expertise, Authoritativeness, and Trustworthiness.
## Create an essay outline.
Drafting a personal essay outline first can help you lay out the main points and tone of the message you are trying to share. Your outline will help you figure out early on if this specific moment is worth writing about. Whichever topic you choose for your essay, it must have had a strong emotional impact on you or have taught you a lesson in some way.
## Start with your intro.
Include your hook, state your thesis, and form an emotional connection with the reader. Set your audience up for what your piece will be about and give them something to look forward to.
## Fill your body paragraphs.
Use sensory details about the sequence of events surrounding your thesis to guide the reader through your personal essay. Build up your personal story here to eventually lead the reader to your main point.
## Be specific.
A descriptive essay about a significant moment in your life is much more engaging than a general overview of something that happened to you. Provide the details necessary about real life characters or any particular feelings experienced.
## Include a conclusion. 
Summarize what you learned from your experience and what message you hope to pass on to the reader. It might be a difficult or unsettling revelation, but ending on a generally positive or hopeful note can help it feel more aspirational or uplifting.
## Proofread your work.
Aside from checking spelling and grammar, make sure your intent is clear and your narrative is easy to follow. No matter how good your writing skills are, it’s always helpful to reread your own work and ensure you’ve solidified your story.


It seems things do not work as they should.

![img_alt]({{ page.image }}){:width="800" height="xxx"}

**something**

$$
\ne
$$

```
code
```
