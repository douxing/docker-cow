# Docker Cow

A docker repo for [COW proxy](https://github.com/cyfdecyf/cow).

## Build

``` shell
    cd /path/of/Dockerfile
	docker build .	
```

## Usage

``` shell
    docker run -d --restart=always -p ${HOST_PORT|:${CONTAINER_PORT} --name cow-client -v ${/path/to/.cow}:/root/.cow -w /root/.cow douxing/cow	
```

example:

rc file:

> listen = http://0.0.0.0:7777
>
> proxy = ${SERVER_URL}
>
> userPasswdFile = cowpass.txt # optional

``` shell
    docker run -d --restart=always -p 7777:7777 --name cow-client -v $HOME/.cow:/root/.cow -w /root/.cow douxing/cow	
```

**tip**: -w is optional and used for files like userPasswdFile,
COW use [os.Open](https://github.com/cyfdecyf/cow/blob/41c0fb157c8b939b724ae0d58dad3a1b7cd2e811/auth.go#L139) inside.
If not set, /root/.cow is used.

**best practice** Just put every thing inside ```$HOME/.cow``` will be okay.

Check the [COW proxy wiki](https://github.com/cyfdecyf/cow/wiki/Running-cow-with-docker-with-C-S) for more tips.
