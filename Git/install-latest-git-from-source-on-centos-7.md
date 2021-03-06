# Install Latest Git from Source on CentOS 7

#### Purpose
* `sudo yum install git` may install the old version of Git.
* To get latest version of Git, install git from source is a good idea.

#### Steps
1. Install "Development Tools"

        sudo yum groupinstall "Development Tools"

* It'll install tools to build Git(e.g. autoconf, gcc, make...)
* It'll also install an old version git(we need to run `git clone` for [git repo](https://github.com/git/git/)

2. Install Extra Dependencies
    * `sudo yum install zlib-devel perl-ExtUtils-MakeMaker asciidoc xmlto`

3. Install `libcurl-devel` to add HTTPS support for Git
    * `sudo yum install libcurl-devel`

4. Get source of git

           git clone git@github.com:git/git.git
           // List remote tags
           git tag -l
           // choose the tag of latest release(e.g. v2.15.0)
           git checkout -b v2.15.0 v2.15.0

5. Make git

        make configure
        ./configure --prefix=/usr/local
        make all doc
        sudo make install install-doc install-html

6. Setup git

        git config --global user.name "Your Name"
        git config --global user.email "xx@example.com"
        git config --global color.ui true

7. Set VISUAL and EDITOR env variables
  
        // Ex: /etc/profile or ~/.bashrc
        export VISUAL=vim
        export EDITOR="$VISUAL"

#### References
* [How To Install Git on a CentOS 6.4 VPS](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-a-centos-6-4-vps)
 

