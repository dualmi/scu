# SSH Connection Utility (SCU)
Utility which provides faster way to jump in to your remote host than regular 'ssh' using Ansible yaml inventory or own hosts list.

### Prerequisites

SCU is a bash script written with Bash 4+ (and yq 4+ for yaml) as add-on over standart ssh client.

### Installing

Put this script into bin directory like ~/bin or /usr/local/bin and make it executable (chmod a+x ...)

```
mkdir ~/bin/
curl https://raw.githubusercontent.com/dualmi/scu/master/bin/scu -o ~/bin/scu
chmod a+x ~/bin/scu
```

## Usage

### First run

Config file should be stored in home directory and called .scurc (~/.scurc)
To get a configuration example you can run
```
~$ scu init
```
and 2 files .scurc and .scurc.yaml will be generated as examples.
This command can be done only if file doesn't exists.

### Ansible inventory

You could use yaml Ansible inventory and set variables `ansible_host`, `ansible_port`, `ansible_user` and `ansible_ssh_common_args`.

Inventory example:
```
all:
  children:
    my_company:
      vars:
        ansible_user: root
        ansible_port: 22
      children:
        firstgroup:
          hosts:
            example-host-yaml:
              ansible_host: 192.168.1.1
            example-host-yaml-args:
              ansible_user: admin
              ansible_host: 192.168.2.2
              ansible_port: 3333
              ansible_ssh_common_args: '-o ProxyCommand="ssh -W %h:%p -q ssh-tunnel@10.10.2.2 -p 2222"'
```

### How to connect

After you done with you hosts list there are three things you can do:
1. View full list of your hosts, just run
```
~$ scu
```
and you will see something like that:
```
	SSH Connection Utility with predefined hosts list

		Usage: /home/username/bin/scu <host number|host name>

Available hosts:
1: example-line-one	2: example-host-one	3: example-host-two	

```

2. Connect to your host using name or list number:
```
~$ scu 2
```
or
```
~$ scu example-host-one
```

3. Search your host by part of its name:
```
~$ scu host

	SSH Connection Utility with predefined hosts list

		Usage: /home/username/bin/scu <host number|host name>

Available hosts:
2: example-host-one	3: example-host-two	
```

## Other info

### Licence

This project is licensed under GPL 3 License - see [https://www.gnu.org/licenses/gpl-3.0.en.html]
