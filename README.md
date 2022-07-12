# ansible-devbox-fmdj

All I know so far about `Ansible` is you can use it to configure a machine (virtual or not, but it seems to be more used for physical machines than for virtual ones).

It is the equivalent of a programmable Sys Admin, or of Docker but for a machine - if understand correctly.

## Concepts de base

### Noeuds du réseau

Décrits [ici](https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html), je retiens surtout qu'il y à des noeuds de contrôle qui vont configurer ou maintenir à jour des noeuds hôtes.

#### Les noeuds de contrôle

Font tourner les scripts tels que: `ansible-playbook` , `ansible`, `ansible-vault`
