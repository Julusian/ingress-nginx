1. `cd images/nginx`
1. Modify the `CC_OPTS` for the x86_64 arch to `CC_OPT+=' -m64 -mtune=core2'`
1. Add `--with-luajit-xcflags='-mno-sse4.2' \` to the `WITH_FLAGS` variable
1. `REGISTRY=julusian/nginx-ingress TAG=base-amd64 make container`
1. `docker tag  julusian/nginx-ingress/nginx:base-amd64  julusian/nginx-ingress:base-amd64`
1. `docker push julusian/nginx-ingress:base-amd64`
1. `cd ../..`
1. `BASEIMAGE=julusian/nginx-ingress:base-amd64 ARCH=amd64 TAG=v0.25.0-nosse42 REGISTRY=julusian/nginx-ingress make build container`
1. `docker tag julusian/nginx-ingress/nginx-ingress-controller-amd64:v0.25.0-nosse42 julusian/nginx-ingress:v0.25.0-nosse42`
1. `docker push julusian/nginx-ingress:v0.25.0-nosse42`
