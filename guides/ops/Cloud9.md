Connect
=======

Setup an EC2 instance
---------------------
Create first an EC2 instance from a Debian-based flavor.
- Make sure that the EC2 is available publicly via SSH. Then, copy the SSH Key provided by Cloud9 when trying to connect to an existing instance in `~/.ssh/authorized_keys`
- Install a capable machine depending on the project. A project using Docker extensively requires both extra hard-drive space and memory.

Installation script
-------------------
The script will install zsh and setup a elixir/phoenix development environment.

```
cd
wget https://raw.githubusercontent.com/civilcode/laptop/master/cloud9
chmod a+x cloud9
./cloud9
```


Format watcher for linux
--------------------------------

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
