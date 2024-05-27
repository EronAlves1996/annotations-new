`docker run -ti --entrypoint /bin/sh YOUR_IMAGE`

Jumping as sudo:

```sh
docker exec -u root -t -i container_id /bin/bash
```