# Rancher
Unicorn signal forwarder / USR2 restart manager for services like Supervisor, Upstart, and Foreman

This script helps manage unicorn by passing signals on to it and keeping its own process alive when unicorn doing its "always up" restarts, mainly this is used to keep things like foreman, upstart, and supervisor happy.

This is intended as a lighter bash alternative to Unicorn Herder (https://github.com/gds-operations/unicornherder) but just for unicorn.

```
 rancher <pid file> <command>
   <pid file>   the pid file location where unicorn places its pid file
   <command>    the unicorn command to run e.g. bundle exec unicorn -c ./config/unicorn.rb
```

Rancher outputs a pid file named "rancher.pid" in the same directory as the pid file it is watching if it can and in /tmp if it cant. So you can send signals to unicorn through rancher using something like:

```
kill -USR2 $(cat /tmp/rancher.pid)
kill -TTIN $(cat /tmp/rancher.pid)
kill -TTOU $(cat /tmp/rancher.pid)
kill -HUP $(cat /tmp/rancher.pid)
kill -TERM $(cat /tmp/rancher.pid)
kill -QUIT $(cat /tmp/rancher.pid)
```
