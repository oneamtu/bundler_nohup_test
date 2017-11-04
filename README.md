Test for bundler - nohup interaction. Useful for debugging a weird signaling behavior in bundler > 1.12.5.

Usage example:

```
[19:56:44] oneamtu:test $ nohup bundle exec rake loop_de_loop >> loop.log 2>&1 &
[1] 7657
[19:56:52] oneamtu:test $ kill -hup 7657
[1]  + 7657 exit 1     nohup bundle exec rake loop_de_loop >> loop.log 2>&1
```

Full debug info:

```
[19:56:02] oneamtu:test $ nohup rake loop_de_loop >> loop.log 2>&1 &
[1] 7553
[19:56:27] oneamtu:test $ kill -hup 7553
[19:56:34] oneamtu:test $ kill -kill 7553
[1]  + 7553 killed     nohup rake loop_de_loop >> loop.log 2>&1
[19:56:44] oneamtu:test $ nohup bundle exec rake loop_de_loop >> loop.log 2>&1 &
[1] 7657
[19:56:52] oneamtu:test $ kill -hup 7657
[1]  + 7657 exit 1     nohup bundle exec rake loop_de_loop >> loop.log 2>&1
[19:56:59] oneamtu:test $ bundle exec nohup rake loop_de_loop >> loop.log 2>&1 &
[1] 7746
[19:57:12] oneamtu:test $ kill -hup 7746
[19:57:17] oneamtu:test $ kill -kill 7746
[1]  + 7746 killed     bundle exec nohup rake loop_de_loop >> loop.log 2>&1

[6:09:53] oneamtu:test $ nohup --version
nohup (GNU coreutils) 8.25
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Jim Meyering.
```


## Environment

```
Bundler       1.16.0
  Platforms   ruby, x86_64-linux
Ruby          2.4.2p198 (2017-09-14 revision 59899) [x86_64-linux]
  Full Path   /home/oneamtu/.asdf/installs/ruby/2.4.2/bin/ruby
  Config Dir  /home/oneamtu/.asdf/installs/ruby/2.4.2/etc
RubyGems      2.6.13
  Gem Home    /home/oneamtu/.asdf/installs/ruby/2.4.2/lib/ruby/gems/2.4.0
  Gem Path    /home/oneamtu/.gem/ruby/2.4.0:/home/oneamtu/.asdf/installs/ruby/2.4.2/lib/ruby/gems/2.4.0
  User Path   /home/oneamtu/.gem/ruby/2.4.0
  Bin Dir     /home/oneamtu/.asdf/installs/ruby/2.4.2/bin
Tools
  Git         2.7.4
  RVM         not installed
  rbenv       not installed
  chruby      not installed
```

## Bundler Build Metadata

```
Built At          2017-10-31
Git SHA           10f20fa33
Released Version  true
```

## Bundler settings

```
path
  Set for your local app (/home/oneamtu/test/test/.bundle/config): "vendor/bundle"
disable_shared_gems
  Set for your local app (/home/oneamtu/test/test/.bundle/config): true
```

## Gemfile

### Gemfile

```ruby
source 'https://rubygems.org'

gem 'rake', '~> 11.0'
```

### Gemfile.lock

```
GEM
  remote: https://rubygems.org/
  specs:
    rake (11.3.0)


```
