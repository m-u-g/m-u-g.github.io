require "time"

##########
# Config #
##########

# Common
public_dir      = "_site"    # compiled site directory
posts_dir       = "_posts"   # directory for blog files

#######################
# Working with Jekyll #
#######################

task :default do
    system "rake --tasks"
end

desc "Initial setup"
task :install do |t, args|
  system "bundle install"
end

desc "Generate jekyll site"
task :generate do
  puts "## Generating site"
  system "JEKYLL_ENV=production bundle exec jekyll build"
end

desc "preview the site in a web browser"
task :preview do
  puts "## Generate and serve site"
  system "bundle exec jekyll serve"
end

# usage `rake new_post` or `rake new_post 'Title for the post'
desc "Create a new post"
task :new_post do |t, args|

  date = DateTime.parse(Time.now.to_s).strftime("%Y-%m-%d")

  title = get_stdin("Enter the post title: ")
  title_slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')

  file_name = "#{date}-#{title_slug}.md"
  file_path = "#{posts_dir}/#{file_name}"

  puts "Creating new post at #{file_path}"

  content = <<-CONTENT
---
layout: post
title:  "#{title}"
date:   #{date} 12:00:00 +0100
categories:
---
CONTENT

  File.open(file_path, "w+") do |f|
    f.write(content)
  end
end

#########
# Utils #
#########

def get_stdin(message)
  print message
  STDIN.gets.chomp
end
