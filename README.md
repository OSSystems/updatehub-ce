UpdateHub Community Edition
===========================

> This is community edition of [UpdateHub](https://updatehub.io).
An end-to-end solution for large scale over-the-air update of devices.

<img align="center" src="docs/device_list.png"/>

## Usage

The product unique identifier is required to allow the device to communicate
with the updatehub-ce-server. You can generate a new unique identifier
running the following command:

```
openssl rand -hex 32
```

If you are creating a product based on the Yocto Project, you should use the
`UPDATEHUB_PRODUCT_UID` variable inside your distribution, or the `conf/local.conf`.

### Running the server

```
$ docker run updatehub/updatehub-ce-server --help
Usage:
  updatehub-ce-server [flags]

Flags:
      --db string         Database file (default "updatehub.db")
  -h, --help              help for updatehub-ose-server
      --password string   Admin password (default "admin")
      --port int          Port (default 8080)
      --username string   Admin username (default "admin")
```
