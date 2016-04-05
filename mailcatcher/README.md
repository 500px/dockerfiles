# Mailcatcher
A minimal Docker image to run [Mailcatcher](https://mailcatcher.me/). Based on Alpine Linux.

# `Dockerfile` links
* [latest](https://github.com/pwyliu/dockerfiles/blob/master/mailcatcher/Dockerfile)

# How To Use This Image
The default command this image runs is: 

```bash
/usr/bin/mailcatcher --smtp-ip=0.0.0.0 --http-ip=0.0.0.0 --http-port=1080 --smtp-port=1025 --foreground
```

You may override the argument string by passing in a new arg string as shown below:

```bash
# Runing Mailcatcher with defaults
docker run -p 127.0.0.1:1080:1080 -p 127.0.0.1:1025:1025 500px/mailcatcher

# Running Mailcatcher, passing in a different arg string
docker run -p 127.0.0.1:1080:8080 -p 127.0.0.1:1025:1025 500px/mailcatcher --smtp-ip=0.0.0.0 --http-ip=0.0.0.0 --http-port=8080 --smtp-port=1025 --foreground
```

# Mailcatcher License
View the [Mailcatcher license information](https://github.com/sj26/mailcatcher/blob/master/LICENSE).

## Contributing
[Submit a PR](https://github.com/pwyliu/dockerfiles)
