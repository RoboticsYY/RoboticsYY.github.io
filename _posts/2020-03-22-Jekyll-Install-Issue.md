---
layout: default
title: Jekyll Install Issue on Ubuntu 18.04
---

[Jekyll](https://github.com/jekyll/jekyll) is a blog-aware static site generator in Ruby.

When installing Jekyll by running the commands:

```bash
gem install bundler jekyll
```
for the first time. It would probably get the error:

```bash
Fetching: bundler-2.1.4.gem (100%)
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /var/lib/gems/2.5.0 directory.
```

from the terminal. Obviously, `sudo` is needed here to run the commands. However, running the commands as supper-user would bring some other issues, that difficult to be altered in future. Thus, it's better to [run Jekyll as Non-Superuser (no sudo!)](https://jekyllrb.com/docs/troubleshooting/#no-sudo), by adding the following lines to the end of your .bashrc file:

```bash
# Ruby exports

export GEM_HOME=$HOME/gems
export PATH=$HOME/gems/bin:$PATH
```

Now, if everything is right, it would be possible to install and run Jekyll to create the first example of Jekyll website:

```bash
gem install bundler jekyll

jekyll new my-awesome-site

cd my-awesome-site

bundle exec jekyll serve

# => Now browse to http://localhost:4000
```
