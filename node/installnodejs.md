                                                                  # install nodejs

ref: [download](https://nodejs.org/en/download/)

1. way 1

```
> wget https://nodejs.org/dist/v6.9.4/node-v6.9.4-linux-x64.tar.xz
> xz -d node-{version}.tar.xz
> tar -xvf node-{version}.tar
> mv node-{version} node
> sudo mv node /usr/local
> chown -R root.root node
> ln -s /usr/local/node/bin/node /usr/local/bin/node
> ln -s /usr/local/node/bin/npm /usr/local/bin/npm
> node -v
> npm -v
```

+ way 2

```
> tar xvf node-v0.10.28.tar.gz 
> cd node-v0.10.28 
> ./configure 
> make && make install 
> cp /usr/local/bin/node /usr/sbin/ 

> node -v 
```

