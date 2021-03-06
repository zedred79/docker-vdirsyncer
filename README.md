## docker-vdirsyncer
A docker container (deabian based) which syncs your CalDAV/CardDAV calendars/addressbooks periodically.

This docker app uses [pimutils/vdirsyncer](https://vdirsyncer.pimutils.org/) to synchronize your CalDAV/CardDAV calendars/addressbooks between two servers.

### Getting started

1. create a vdirsyncer configuration file. See file [_config.example_](https://github.com/pimutils/vdirsyncer/blob/master/config.example) and [vdirsyncer docs](https://vdirsyncer.pimutils.org/)
2. adapt docker-compose.yml to use your configuration file
3. start the container via:
```docker-compose up -d```

Be happy! The container will synchronize your calendars/addressbooks every 15 minutes.

### docker-compose example

```
version: '3'
services:

  vdirsyncer:
    image: zedred/vdirsyncer
    container_name: vdisyncer
    volumes:
      - ./your_config_file:/home/vds/.config/vdirsyncer/config
    restart: unless-stopped
```
