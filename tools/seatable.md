- install directory: `/opt/seatable`
- config: 
  - script `<install>/conf/seatable_settings.py`
  - files: *<install>/seatable-data/seatable/conf/*
    - all rate limits can be changed here
    - restart after changes
- `docker exec -d seatable /shared/seatable/scripts/seatable.sh`: admin script
    - `start|stop|restart`: restart on config change
- data docker volumes:
    - `<install>/mysql-data`: DB
    - `<install>/seatable-data`: seatable (log and config of nginx and seatable)
- different api tokens for different requests
  - for base operations: base token (generated from: API-token, Account-Token, Invite-Link, External-Link)
    - valid 3 days
    - has read/write permissions
  - for account operations: account-token (generated from username+password)
    - add new base
    - add group member
    - list collaborators of base

# webhooks
- every change of a base --> record sent to an URL

# forms
- can be used to add columns to a table

# model
## columns
- types:
  - **long-text** for daily documentation
  - **date** for timstamps
  - **link** for calendar
  - **button** for adding to a cell/executing a command

## link
- bidirectional: changes on either side show up on th other
- no links between bases

# nginx
- config: */opt/seatable/seatable-data/seatable/conf/nginx.conf*
- logs:
  - */opt/nginx-logs/dtable<service>.access.log*
  - */opt/nginx-logs/dtable<service>.error.log*
