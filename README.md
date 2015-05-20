# Rancher
Unicorn signal forwarder / USR2 restart manager for services like Supervisor, Upstart, and Foreman

This script helps manage unicorn by passing signal on to it and keeping its own process alive when unicorn doing its "always up" restarts, mainly this is used to keep things like foreman, upstart, and supervisor happy.

This is intended as a lighter bash alternative to Unicorn Herder (https://github.com/gds-operations/unicornherder) but just for unicorn.

```
 rancher <pid file> <command>
   <pid file>   the pid file location where unicorn places its pid file
   <command>    the unicorn command to run e.g. bundle exec unicorn -c ./config/unicorn.rb
```
