#### IP Address of the container
```bash
docker inspect <container> -f '{{ json .NetworkSettings.Networks }}'
```

#### Clean docker logs
```bash
sudo docker inspect <container> -f '{{ .LogPath }}' | sudo xargs truncate -s 0
```
```bash
sudo sh -c 'truncate -s 0 /var/lib/docker/containers/*/*-json.log'
```
