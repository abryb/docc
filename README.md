docker-compose file locator and wrapper written in bash

### Installation
Just curl and save into one of directory in $PATH variable
##### global
```bash
# you may need to sudo it
curl https://raw.githubusercontent.com/abryb/docc/master/docc -o /usr/local/bin/docc
chmod +x /usr/local/bin/docc
```
##### user only
```bash
curl https://raw.githubusercontent.com/abryb/docc/master/docc -o /home/$USER/.local/bin
chmod +x /home/$USER/.local/bin
```
rembember to add /home/$USER/.local/bin to $PATH variable

### Usage
```shell
docc --help
```

### docc.sh wrapper

Example docc.sh wrapper

```bash
#!/usr/bin/env bash

# Using variables from .env file

case $1 in
    open )
        exec xdg-open http://${COMPOSE_PROJECT_NAME}.localhost ;;
    shell )
        exec docker-compose exec my-service /bin/ash ;;
esac

exec docker-compose "$@"
```
