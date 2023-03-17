- ssh logins:
    - `ssh -p 2222 eric.starke@web01.washabich.de`
    - `ssh -p 2222 eric.starke@web02.washabich.de`
    - `ssh -p 2222 eric.starke@infra01.washabich.de`
- php logs: `cat /var/log/php8.1-fpm.log`

# error handling
- delete: *node_modules* folder
- call: `sh ./fix-permissions.sh`
- call: `sh ./build.sh` directly