+++
title = "Install emacs from source on ubuntu 19.04"
author = ["Steve Kallestad"]
lastmod = 2019-05-26T15:05:03-07:00
tags = ["install"]
categories = ["emacs"]
draft = false
weight = 2005
+++

The first step is to install all of the requirements to the build:

```shell
sudo apt install \
     build-essential \ # development tools
     libncurses-dev libncurses5-dev \ # tools for text-based user interfaces
     libtiff-dev \ # image support
     libgif-dev \
     libpng-dev \
     imagemagick libmagickwand-dev imagemagick-common \
     libcairo2-dev \
     librsvg2-dev \
     libx11-dev \ # x-windows support
     libgtk-3-dev \
     xaw3dg-dev \
     libxpm-dev \
     libgconf-2-4 \
     libgpm-dev \
     libotf-dev \ # fonts
     libm17n-dev \ # multi-lingual support
     libgnutls28-dev \ # TLS
     libmailutils-dev \ # mail support
     mailutils \
     libxml2-dev \ # xml support
```

A few notes on the above step.

-   `build-essential` is overkill, but it covers all of the requirements for the
    build and alleviates the need to ferret out the necessary tools and package names.
-   I'm not entirely certain that `imagemagick` and `imagemagick-common` are
    necessary.  It was my third try enabling imagemagick when I got it working.
-   `libcairo2-dev` is required for the "--with-cairo" configuration option.  My
    configuration does not require it, but I included it in case I need it down
    the road.
-   `mailutils` and `libmailutils-dev` are required for email integration.  If
    you don't use emacs with email, you can get rid of them.

From here, download the source from a nearby mirror and extract it:

```shell
CURRENT_VERSION=26.2
wget http://ftpmirror.gnu.org/emacs/emacs-${CURRENT_VERSION}.tar.xz
# also download the signature
wget http://ftpmirror.gnu.org/emacs/emacs-${CURRENT_VERSION}.tar.xz.sig
gpg --verify emacs-${CURRENT_VERSION}.tar.xz emacs-${CURRENT_VERSION}.tar.xz.sig
tar -xvf emacs-${CURRENT_VERSION}.tar.xz
```

compile the source

```shell
CURRENT_VERSION=26.2
cd emacs-${CURRENT_VERSION}
./configure --with-cairo
make
make install
```

Once you have compiled, the `-dev` packages are no longer needed - at least
until the next installation so at this point they can be removed.  I generally
do not do this on my personal machine, but in a docker environment or any
environment where you are looking to save space, it's a step you want to take
to clean things up.  You might want to uninstall other unnecessary items.

I didn't take this step, you may need to troubleshoot.

```shell
CURRENT_VERSION=26.2
sudo apt-get remove build-essential \ # development tools
     libncurses-dev libncurses5-dev \ # tools for text-based user interfaces
     libtiff-dev \ # image support
     libgif-dev \
     libpng-dev \
     imagemagick libmagickwand-dev imagemagick-common\
     libcairo2-dev \
     librsvg2-dev \
     libx11-dev \ # x-windows support
     libgtk-3-dev \
     xaw3dg-dev \
     libxpm-dev \
     libgconf-2-4 \
     libgpm-dev \
     libotf-dev \ # fonts
     libm17n-dev \ # multi-lingual support
     libgnutls28-dev \ # TLS
     libmailutils-dev \ # mail support
     libxml2-dev \ # xml support

cd ..
rm -rf ./emacs-${CURRENT_VERSION}
rm ./emacs-${CURRENT_VERSION}.tar.xz
```

Of course, if you are really looking into minimizing space, it is much cleaner
to have a separate build environment and build your own binary package,
including only files that are absolutely necessary in that package.

And if you are looking into maximizing performance, you will want to configure
the system with only those dependencies that are important for your use case.
And you will want to use a higher level of compiler optimization, and along
with that optimization run a full suite of tests to ensure that no undefined
behavior results from it.

My use case for emacs is very general.  I tend to do a lot of builds within my
personal and development environments that have common dependencies.  And I
tend to re-build emacs on whims.  I don't keep it updated as releases come
out - if I'm in the middle of a big project I don't want to risk it.  But,
sometimes I do want to take advantage of a new feature and I never want to get
left too far behind, as migration gets more and more cumbersome over time.
