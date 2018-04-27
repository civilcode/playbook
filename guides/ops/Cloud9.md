Connect
=======

Setup an EC2 instance
---------------------
Create first an EC2 instance from a Debian-based flavor.
- Make sure that the EC2 is available publicly via SSH. Then, copy the SSH Key provided by Cloud9 when trying to connect to an existing instance in `~/.ssh/authorized_keys`
- Install a capable machine depending on the project. A project using Docker extensively requires both extra hard-drive space and memory.

Install zsh
-----------

``` {.shell}
sudo apt-get install zsh
sudo chsh -s $(which zsh) ubuntu
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

Install asdf
------------

``` {.shell}
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.4.3
echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.zshrc
echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.zshrc
```

Install nodejs (required by Cloud9)
-----------------------------------

``` {.shell}
asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git
bash ~/.asdf/plugins/nodejs/bin/import-release-team-keyring
```

Install python 2.7
------------------

``` {.shell}
sudo apt-get install python2.7
```

Install erlang
--------------

``` {.shell}
asdf plugin-add erlang https://github.com/asdf-vm/asdf-erlang.git
sudo apt-get install build-essential auto-conf libncurses5-dev libssh-dev unixodbc-dev m4
asdf install erlang 20.3
asdf global erlang 20.3
```

Install elixir
--------------

``` {.shell}
sudo apt-get install unzip
asdf plugin-add elixir https://github.com/asdf-vm/asdf-elixir.git
asdf install elixir 1.6.4
asdf global elixir 1.6.4
```

Install Ruby
------------

``` {.shell}
asdf plugin-add ruby https://github.com/asdf-vm/asdf-ruby.git
asdf install ruby 2.5.1
asdf global ruby 2.5.1
```

Install Go
----------

``` {.shell}
asdf plugin-add golang https://github.com/kennyp/asdf-golang.git
asdf install golang 1.9
asdf global golang 1.9
```

Install Hub
-----------

``` {.shell}
gem install bundler
git clone https://github.com/github/hub.git
cd hub
bundle install
make install prefix=/usr/local

#OR
go get github.com/github/hub
sudo cp ~/.golang/bin/hub /usr/local/bin
```

Cache credentials for a minute
------------------------------

``` {.shell}
git config --global credential.helper 'cache --timeout=3600'
```

Add aliases to \~/.gitconfig
----------------------------

    [alias]
            co = checkout
            st = status
            ci = commit
            cis = commit -S
            df = diff
            dfc = diff --cached
            quick-amend = amend --no-edit
    [push]
            default = current






Format watcher for linux
--------------------------------
Install inotify tools
``` {.shell}
sudo apt-get install inotify-tools
```

Script skeleton for incremental `mix format` when a file is touched.
``` {.bash}
#!/bin/bash

inotifywait -m ~/environment -e modify,create -e moved_to |
    while read path action file; do
        if [[ $file =~ \.ex$ ]]; then
                echo "('$action') The file '$path/$file' will be formatted"
                mix format $path/$file
        fi
    done
```
