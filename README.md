# docker-samba

[![Latest Github release](https://img.shields.io/github/release/rugarci/docker-samba.svg)](https://github.com/rugarci/docker-samba/releases/latest)
[![Image size](https://img.shields.io/docker/image-size/rugarci/samba)](https://hub.docker.com/r/rugarci/samba)
[![Docker Pulls](https://img.shields.io/docker/pulls/rugarci/samba.svg)](https://hub.docker.com/r/rugarci/samba)

Samba in Docker inspired on https://github.com/dperson/samba/ and https://github.com/uPagge/samba

Tested on Raspberry Pi 3, 4

## Usage

```yaml

samba:
  image: rugarci/samba:main
  container_name: samba
  command: '-s "public;/shared;yes;no;yes" -p -n'
  environment:
    - USERID=0
    - GROUPID=0
    - WORKGROUP=WORKGROUP
  ports:
    - 139:139
    - 445:445
  deploy:
    resources:
      limits:
        cpus: '0.5'
        #memory: 50M
  volumes:
    - /mnt/disk1/public:/shared:z
  restart: unless-stopped
```

