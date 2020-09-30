# CodiMD

Used Fork: (https://github.com/hackmdio/codimd)

## Configuration

Edit file `.env` to your needs

Mandatory values: `DB_PASSWORD` and `CMD_SESSION_SECRET`

(https://hackmd.io/c/codimd-documentation/%2Fs%2Fcodimd-configuration)

## After deploying

### Correcting file permissions

Ensure proper permissions on the volume
Reference: (https://hackmd.io/c/codimd-documentation/%2Fs%2Fcodimd-docker-deployment)

To upload images to local volume, it’s important to setup proper permission for volume or the server won’t able to write into it.

Please allow user named hackmd in the docker to access the volume, which user id and group id are uid=1500, gid=1500.
You can change the volume permission though this command:

`chown -R 1500:1500 /var/lib/docker/volumes/<volume_dir>/_data`

### User management

First, enter running docker container

```sh
docker exec -it codimd /bin/bash
```

Add user

```
hackmd@023981483df:~/app$ ./bin/manage_users --pass <pwd> --add <email>
```

Delete user

```
hackmd@023981483df:~/app$ ./bin/manage_users --del <email>
```

## Deploying

Starting

`docker-compose up -d`

Stopping

`docker-compose down`
