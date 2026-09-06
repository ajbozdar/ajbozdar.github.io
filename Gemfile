# frozen_string_literal: true

source "https://rubygems.org", cooldown: 7
 gem 'jekyll'
 gem 'jekyll-paginate'

require 'rbconfig'
  if RbConfig::CONFIG['target_os'] =~ /(?i-mx:bsd|dragonfly)/
  gem 'rb-kqueue', '>= 0.2'
end
