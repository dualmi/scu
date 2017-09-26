# SSH Connection Utility (SCU)
Utility which provides faster way to jump in to your remote host than regular 'ssh'.

### Prerequisites

SCU is a bash script written with Bash 4 as add-on over standart ssh clients so it should be run under bash and openssh must be installed.

### Installing

Put this script into bin directory like ~/bin or /usr/local/bin and make it executable (chmod a+x ...)

## Usage

### First run

Host list should be stored in separate file in home directory and called .scurc (~/.scurc)
To get a configuration example you can run

```
~$ scu init
```
and .scurc will be generated with three hosts to show you how it can be filled in.
This command can be done only if file doesn't exists.

### How to connect

After you done with you hosts list in .scurc there are three things you can do:
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

