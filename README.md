# DFBnc Dockerfile

This is a dockerised version of [DFBnc](https://github.com/ShaneMcC/DFBnc/).

## Usage

Create a named volume to persist data:

```bash
docker volume create --name dfbnc-data
```

Pull the image for the desired version of DFBnc:

```bash
docker pull csmith/dfbnc:0.4
```

Start a container, exposing ports as needed:

```bash
docker run -d --name dfbnc \
              --restart always \
              -p 33263:33263 \
              -v dfbnc-data:/var/lib/dfbnc \
              csmith/dfbnc:0.4
```

The container exposes these ports:

  * 33262 (unencrypted IRC connection)
  * 33263 (encrypted IRC connection) 

To enable encrypted connections you will need to follow the instructions
on the [DFBnc wiki](https://github.com/ShaneMcC/DFBnc/wiki/SSL-Listen-Hosts).
