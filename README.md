# Introduction #

A cross-vendor configuration distribution tool. This is useful for pushing
ACLs or other pieces of configuration to network elements. It can also be used
to send commands to a list of devices and gather the results.

# Install #

To run this tool you will need to install several modules not part of the
Python standard library, all of which should be easily installable via pip,
easy\_install, or distribution package:

  * pexpect
  * paramiko
  * progressbar
  * gflags

# Examples #

Push the configurations in /tmp/foo and /tmp/bar to two devices, 192.168.192.1
and router1.foo.com. Push cannot guess what vendor is in use, but you could
change the default vendor flag at the top if you only use one vendor. This
example forces the use of the username 'dude' rather than your own.

> ./push.py --targets 192.168.192.1,router1.foo.com --vendor ios --user dude \
> /tmp/foo /tmp/bar

Send a 'show version' command to the list of devices. Output will be sprayed to
STDOUT. Target names must be resolvable on your machine.

> ./push.py --targets [r1](https://code.google.com/p/ldpush/source/detail?r=1),[r2](https://code.google.com/p/ldpush/source/detail?r=2),[r3](https://code.google.com/p/ldpush/source/detail?r=3),[r4](https://code.google.com/p/ldpush/source/detail?r=4) --vendor ios --command 'show version'

Use filenames to determine the name of the target device. The string file name
must be resolvable.

> ./push.py --devices\_from\_filenames --vendor ios devicefiles/