# OpenWRT feeds for my Raspberry PI

## Prerequisites

* Install the [OpenWRT SDK](https://openwrt.org/docs/guide-developer/using_the_sdk)

## Build process

```sh
cat >> feeds.conf.default <<EOF
src-git custom https://github.com/nmasse-itix/openwrt-feeds.git
EOF
./scripts/feeds update -a
./scripts/feeds install nginx-tls
make menuconfig
make package/feeds/custom/nginx-tls/download
make package/feeds/custom/nginx-tls/prepare
make package/feeds/custom/nginx-tls/compile
make package/index
```

For the rest, see [Nginx with TLS on OpenWRT](https://www.itix.fr/blog/nginx-with-tls-on-openwrt/).
