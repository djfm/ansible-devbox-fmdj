# ansible-devbox-fmdj

All I know so far about `Ansible` is you can use it to configure a machine (virtual or not, but it seems to be more used for physical machines than for virtual ones).

It is the equivalent of a programmable Sys Admin, or of Docker but for a machine - if understand correctly.rr

-------

Tout ce que je sais pour l'instant d'`Ansible` c'est que c'est un peu comme un Admin Sys programmable, ou un Docker au niveau de la machine plutôt que
celui du programme.

## Concepts de base

### Noeuds du réseau

Décrits [ici](https://docs.ansible.com/ansible/latest/network/getting_started/basic_concepts.html), je retiens surtout qu'il y à des noeuds de contrôle qui vont configurer ou maintenir à jour des noeuds hôtes.

#### Les noeuds de contrôle

Font tourner les scripts tels que: `ansible-playbook` , `ansible`, `ansible-vault`

#### Les noeuds hôtes

À ce que je comprends, on n'a pas trop à y toucher, c'est justement le but, ils sont gérés par les noeuds de contrôle!

## Installation

Ansibible travaille en faisant transiter ses commandes via ssh, comme on le fairait à la main finalement,
simple, éprouvé, universe et robuste.

Donc côté client il n'y a qu'un serveur ssh à installer (et zut, moi qui voulais ajouter automatiquement la clef plublique
de ma nouvelle machine de dev via `absible`, comment je fais alors? Bon une fois l'installation d'ssh ça doit se faire...)

Du côté hôte, il n'y a qye `pytbon3` et son module `ansiblbe` à installer en plus d'SSH.
Je rappèle à ceux qui ne le sauraient pas comment on installe un serveur (et un clien tant qu'à faire)

## Installation du  serveur / client SSH (Secure Shell) sur toutes les machines du réseau

Je supppose que vous disposez d'une distrubution proche d'un Ubuntu récent (donc variante de Debian plus ou moins récente),
sinon vous sauriez déjà commennt on fait ça, ou alors vous n'utiiliseriez pas une distro non standarde :).

**Pour s'assurer qu'on travaille avec un distro Ubuntu ou Debian récente**

```bash
  lsb_release -a
```

Moi ça me donne ça

```
```




### Sur l'hôte

On commence par installer ansible en suivant [le guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installation-guide).

#### On vérifie les deps

Sous un Ubuntu récent on fait juste:
```
sudo apt install python3-pip
python3 -m pip -V # juste histoire d'avoir la version, j'ai la 22.qqch et la doc a la 21.des.brouettes, on va dire que ça va aller
```

#### Et on installe `Ansible`

Passage oblibgé par la création d'un environnement virtuel pour python...
```bash
python3 -m pip install --user ansible
# on vérifie
ansible --version
# ça foire chez moi parce que le binaire est pas en PATH
# osef parce que ça fait partie des choses tidieuses à configurer,
# je le note pour plus tard
```bash

### Trucs qu'on veut automatiser

## La mise à jour du `PATH`

- Ajouter `$HOME/.local/bin` à `$PATH`
- Installer VSCode: `sudo snap install code --classic`

## Lancer sa première commande d'un noeud de contrôle vers des hôtes


