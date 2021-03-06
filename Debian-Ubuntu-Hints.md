## Caution: Content Not Actively Maintained

This page is migrated from the [old sup wiki](http://supmua.org/history/).
Much of this page is probably outdated and not applicable to sup since
v0.13.

## Native Package

There is a Debian package for Sup called "sup-mail". Ubuntu 9.10
(Karmic) offers this package in the universe repository. This
installs Sup 0.8.1; you can also install Sup 0.9 using the deb from
the newer
[Lucid repository](http://packages.ubuntu.com/lucid/sup-mail).
For older versions of Ubuntu (or newer versions of Sup), you'll
have to use Ruby Gems or install by hand.



## Recommended Method

*Tested so far on: Ubuntu 8.04 (Hardy)*

It is best to install gems from source, rather than using aptitude.
As explained in the
[Ubuntu community wiki for installing Rails](https://help.ubuntu.com/community/RubyOnRails)
- which also has gems as a prerequisite - if you do not, then
aptitude and gems conflict horribly.

To install gems from source:

     sudo aptitude install ruby-full build-essential
     # To get the latest version, see http://rubyforge.org/frs/?group_id=126
     wget http://rubyforge.org/frs/download.php/38646/rubygems-1.2.0.tgz
     tar -zxvf rubygems-1.2.0.tgz
     cd rubygems-1.2.0/
     sudo ruby setup.rb
     sudo ln -s /usr/bin/gem1.8 /usr/bin/gem
     sudo gem update --system

Then to install sup:

     # We need this extra package
     sudo aptitude install libncurses5-dev libncursesw5-dev
     sudo gem install sup
     sup



## Troubleshooting in Ubuntu 8.04

When I tried to run sup following the recent instructions it gave
me the following error:

     $ sup
     /usr/local/lib/site_ruby/1.8/rubygems.rb:578:in `report_activate_error': Could not find RubyGem hoe (>= 1.7.0) (Gem::LoadError)
        from /usr/local/lib/site_ruby/1.8/rubygems.rb:134:in `activate'
        from /usr/local/lib/site_ruby/1.8/rubygems.rb:158:in `activate'
        from /usr/local/lib/site_ruby/1.8/rubygems.rb:157:in `each'
        from /usr/local/lib/site_ruby/1.8/rubygems.rb:157:in `activate'
        from /usr/local/lib/site_ruby/1.8/rubygems.rb:49:in `gem'
        from /usr/bin/sup:18

The solution is simple, install hoe:

     sudo gem install hoe

You're done :).

## On Debian systems

Simply:

     sudo aptitude install sup-mail
     sup-mail

### If you have encoding problems

There's
[an open bug about it](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=520374)
which suggests to install libncurses-ruby1.8 from
[this repository](http://apt.rupamsunyata.org/sup/).

## Alternate Instructions

In order to run Sup and to build all the gems at install time, you
will probably need the following packages installed:

* libcurses-ruby
* libncurses-ruby
* librmail-ruby (In Ubuntu 7.10 and 8.04 that package doesn't exists, use librmail-ruby1.8 instead)
* ruby
* ruby1.8-dev (in order to build the required gems)
* rubygems

Note that if you install Sup via Ruby Gems, by default all binaries
will be places in /var/lib/gems/1.8/bin/, and by default that is
NOT in your path. You will have to add that to your path if you
want to run Sup, or explicitly type /var/lib/gems/1.8/bin/sup every
time.

I installed sup via gem today on my machine (Ubuntu 7.10.), there
was no need to add sup to the PATH. *(in Ubuntu 8.04 neither)*
Installing was done by:

      sudo aptitude install libncurses-ruby
      sudo aptitude install libncurses5-dev
      sudo gem install sup # And Y to all questions



### Alternate instructions elsewhere on the net

[Using Bleeding-edge Sup on Ubuntu](http://blogs.igalia.com/aperez/2008/11/using-bleeding-edge-sup-on-ubuntu/)
(covers Ubuntu 8.10)


## On Intrepid

Additionally to the above, I had to do this:

     sudo gem install echoe
     sudo gem install hoe
     sudo aptitude install libopenssl-ruby
     sudo aptitude install uuid-dev # for xapian

And as mentioned above, /var/lib/gems/1.8/bin/ was not in my PATH
(and confusingly, there is a different package called "sup"
available via aptitude, which is not what you want).



## On Ubuntu 10.10 Maverick

Here's what I needed to do on Ubuntu 10.10:

     sudo add-apt-repository ppa:xapian-backports/xapian-1.2
     sudo apt-get update
     sudo apt-get install -y ruby ruby-dev rubygems libncurses-ruby libncurses5-dev libncursesw5-dev librmail-ruby1.8 git-core build-essential libxapian22 libxapian-ruby1.8
     sudo gem install trollop gettext lockfile mime-types ncursesw
     git clone git://gitorious.org/sup/mainline.git sup
     cd sup
     ruby -I lib bin/sup



## On Ubuntu 11.04 Natty

I just tried one of the tricks already listed above for a debian
install; worked for me:

     sudo apt-get install sup-mail



### Getting ncursesw

I had a bit of difficulty getting non-ASCII UTF-8 characters to
display correctly, and sup was complaining about ncursesw being
unavailable.

Because I don't need a cutting-edge ruby environment on this
machine, I installed the Ubuntu packaged rubygems, then used that
to `sudo gem install ncursesw` (IIRC I needed install
libncursesw5-dev as well).

The final change was to manually edit /usr/bin/sup-mail and add the
instruction "require 'rubygems'" on the second line, to allow
sup-mail to pick up the installed gem.



