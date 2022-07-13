# ansible-devbox-fmdj

All I know so far about `Ansible` is you can use it to configure a machine (virtual or not, but it seems to be more used for physical machines than for virtual ones).

It is the equivalent of a programmable Sys Admin, or of Docker but for a machine - if understand correctly.

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

Ansible travaille en faisant transiter ses commandes via ssh, comme on le fairait à la main finalement,
simple, éprouvé, universe et robuste.

Donc côté client il n'y a qu'un serveur ssh à installer (et zut, moi qui voulais ajouter automatiquement la clef plublique
de ma nouvelle machine de dev via `ansible`, comment je fais alors? Bon une fois l'installation d'ssh ça doit se faire...)

Du côté hôte, il n'y a qye `python3` et son module `ansiblbe` à installer en plus d'SSH.
Je rappelle à ceux qui ne le sauraient pas comment on installe un serveur (et un clien tant qu'à faire)

## Installation du  serveur / client SSH (Secure Shell) sur toutes les machines du réseau

Je suppose que vous disposez d'une distribution proche d'un Ubuntu récent (donc variante de Debian plus ou moins récente),
sinon vous sauriez déjà comment on fait ça, ou alors vous n’utiliseriez pas une distro non standard :).

**Pour s'assurer qu'on travaille avec un distro Ubuntu ou Debian récente**

```bash
  lsb_release -a
```

Moi ça me donne ça :

```txt

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy
```

On est bien sur Ubuntu, ouf! Si vous êtes sur une autre distro, vous devriez vérifier que vous êtes bien sur une distro,

Du moment que votre distro est bien basée sur Debian, tout devrait marcher
comme indiqué dans ce mini tutoriel, si ce n'est pas le cas,
il se peut que certaines commandes soient différentes et que vous deviez fouiller un peu la doc.


**Petit point Culture G. sur Ubuntu :**

- Les versions son numérotées comme ça avec leur année et mois de sortie.
- Chaque version d'une année paire est une version dite LTS (Long Term Support)
  et reçoit donc comme son nom l'indique des mises à jour plus longtemps que les autres.
  [Voir ici sur le site officiel](https://www.ubuntu.com/news/lts-release-notes/)

#### Le minimum vital à savoir sur SSH

[SSH](https://fr.wikipedia.org/wiki/Secure_Shell) pour `secure shell` désigne à la fois un protocole et
un ensemble de programmes permettant (entre autres) de se connecter
en ligne de commande à un serveur distant, de façon tout à fait sécurisée.

**Installation des paquets SSH**

La commande suivante installe le serveur SSH standard :

```bash
  sudo apt install openssh-server
```

Pas la peine d'installer, le client, il est déjà installé dans toute
distro qui se respecte.

Supposons que je veuille me connecter à un serveur sur mon réseau local,
par exemple au PC du salon depuis mon portable, il suffit de faire :

**NOTE:** En règle générale, évitez de taper votre mot de passe dans une ligne de commande
  avant d'avoir appuyé sur la touche `Enter` pour confirmer votre commande, c'est à la commande de
  vous demander votre mot de passe, pas à vous de le lui donner. Le risque est que si vous entriez par
  exemple `ssh toto:password@example.com` dans votre terminal, la ligne totale finira dans un log quelconque,
  et votre mot de pa
**Se connecter à un serveur distant**

```bash
  ssh <login>@<host>
```

**NOTE:** En règle générale, évitez de taper votre mot de passe dans une ligne de commande
  avant d'avoir appuyé sur la touche `Enter` pour confirmer votre commande, c'est à la commande de
  vous demander votre mot de passe, pas à vous de le lui donner. Le risque est que si vous entriez par
  exemple `ssh toto:password@example.com` dans votre terminal, la ligne totale finira dans un log quelconque,
  et votre mot de passe sera potentiellement divulgué si le log fuite.

### Sur l'hôte

On commence par installer ansible en suivant [le guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installation-guide).
Supposons que je veuille me connecter à un serveur sur mon réseau local,
par exemple au PC du salon depuis mon portable, il suffit de faire :


**Se connecter à un serveur distant**

```bash
  ssh <login>@<host>
```

**NOTE:** En règle générale, évitez de taper votre mot de passe dans une ligne de commande
  avant d'avoir appuyé sur la touche `Enter` pour confirmer votre commande, c'est à la commande de
  vous demander votre mot de passe, pas à vous de le lui donner. Le risque est que si vous entriez par
  exemple `ssh toto:password@example.com` dans votre terminal, la ligne totale finira dans un log quelconque,
  et votre mot de passe sera potentiellement divulgué si le log fuite.

#### On vérifie les deps

Sous un Ubuntu récent on fait juste:

```bash
sudo apt install python3-pip
python3 -m pip -V # juste histoire d'avoir la version, j'ai la 22.qqch et la doc a la 21.des.brouettes, on va dire que ça va aller
```

#### Et on installe `Ansible`

Passage obligé par la création d'un environnement virtuel pour python...

```bash
python3 -m pip install --user ansible
# on vérifie
ansible --version
# ça foi
python3 -m pip -V # juste histoire d'avoir la version, j'ai la 22.qqch et la doc a la 21.des.brouettes, on va dire que ça va aller
```re chez moi parce que le binaire est pas en PATH
# osef parce que ça fait partie des choses fastidieuses à configurer,
# je le note pour plus tard
```

### Trucs qu'on veut automatiser

## La mise à jour du `PATH`

- Ajouter `$HOME/.local/bin` à `$PATH`
- Installer VSCode: `sudo snap install code --classic`

## Lancer sa première commande d'un noeud de contrôle vers des hôtes