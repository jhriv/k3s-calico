# Installing k3s with Calico

Proof-of-concept for replacing Traefik with Calico under k3s

## Prerequisites

Ansible. Tested with 2.10.15, should work with 2.9.x
make. apt-get, yum, dnf, brew install it.

## Steps

1. `vagrant up`
2. `vagrant halt`
3. Increase the disk size. See `INSTALL.md`
4. `make all`
5. `ansible-playbook site.yaml -v -D`
6. Rancher takes awhile to come up. Grab a cup of coffee, go for a quick run, come back in a bit.
7. `ansible-playbook nginx.yaml -v -D`
