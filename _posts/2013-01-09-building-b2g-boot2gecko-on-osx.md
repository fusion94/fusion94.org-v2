---
layout: post
title: "Building B2G (Boot2Gecko) on OSX"
date: 2013-01-09 10:37
comments: true
categories: [Open Source, Mobile, Boot2Gecko, Mozilla]
---

So I've been interested in the [Boot2Gecko](https://wiki.mozilla.org/B2G) project for awhile and wanted to see if I could get an app running on [Steroids](http://www.appgyver.com/steroids) that would run under B2G.

To accomplish this I needed to get the B2G desktop emulator up and running so I could actually develop something.

Below is the method I had to use to get it up and running with OSX (Mountain Lion).

## Prerequisites

You will need the following installed to get started.

* Git
* Brew
* Autoconf
* Yasm

For this to build properly you're going to have to force `brew` to download and install `autoconf-2.13`. This can be accomplished by placing the `autoconf.rb` code listed below into your Formula folder located at `/usr/local/Library/Formula/`.

{% highlight ruby %}
require 'formula'

class Autoconf < Formula
  url 'http://ftp.gnu.org/gnu/autoconf/autoconf-2.13.tar.gz'
  homepage 'http://www.gnu.org/software/autoconf/'
  md5 '9de56d4a161a723228220b0f425dc711'`

  def install
    system "./configure", "--program-suffix=213",
                          "--prefix=#{prefix}",
                          "--infodir=#{info}"
    system "make install"
  end
end
{% endhighlight %}

Once this is accomplished just use `brew` to install both `autoconf` and `yasm`

{% highlight bash %}
brew install autoconf

brew install yasm
{% endhighlight %}

## Getting the code
There are two different pieces needed to get the desktop emulator up and running. First there is Mozilla-central. This will contain the b2g executable. The second component needed is gaia. This is the user interface for the b2g phone.

{% highlight bash %}
// Get mozilla-central repo and save it to folder called mozilla-central
git clone https://github.com/mozilla/mozilla-central.git

// Get gaia repo and save to folder called gaia
git clone https://github.com/mozilla-b2g/gaia.git gaia
{% endhighlight %}

## Building Mozilla Central
__Create a mozconfig__

You will need to create a mozconfig file before building. cd into the mozilla-central directory and create a file called “mozconfig”. Then add the following to it and save.

{% highlight bash %}
mk_add_options MOZ_OBJDIR=../build
mk_add_options MOZ_MAKE_FLAGS="-j9 -s"

ac_add_options --enable-application=b2g
ac_add_options --disable-libjpeg-turbo

# This option is required if you want to be able to run Gaia's tests
ac_add_options --enable-tests

# turn on mozTelephony/mozSms interfaces
ac_add_options --enable-b2g-ril
{% endhighlight %}

__Build__

While still in the mozilla-central directory build the source code. Now go get a beer or some coffee as this will take a long time.

{% highlight bash %}
make -f client.mk build
{% endhighlight %}

When complete you should see a build folder outside of your mozilla-central directory.

## Building Gaia
Now that we have mozilla-central working we need to build a profile for gaia. Navigate into the gaia directory that was created when doing a git clone from above. Now we can build with the following command.

{% highlight bash %}
make
{% endhighlight %}

A lot of stuff will happen but if everything works out you should have a “profile” folder in your gaia directory.

## Running the emulator
To run thhe b2g emulator you're going to need to pass in the profile generated in the gaia folder.

{% highlight bash %}
cd build/dist/B2G.app/Contents/MacOS/

./b2g -profile /path/to/gaia/profile
{% endhighlight %}

## Conclusion

It really wasn't that hard to get this up and running under OSX. In a future blog post I'll discuss getting a [Steroids](http://www.appgyver.com/steroids) application un and running under B2G but for now here are a few screenshots.

__B2G Lock Screen__

![](/images/blog/b2g-1/b2g_lock_screen.png)

__B2G Home Screen__

![](/images/blog/b2g-1/b2g_home_screen.png)

__B2G Marketplace__

![](/images/blog/b2g-1/b2g_marketplace.png)
