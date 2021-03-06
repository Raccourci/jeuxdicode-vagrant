jeuxdicode-vagrant
==================

## 1) Utilisez son terminal favoris

Pour les utilisateurs de Windows, nous vous conseillons d'installer Babun

+ [http://babun.github.io/](http://babun.github.io/)

Une fois installer ne pas oublier de le lancer mode "administrateur".
Vous devez ensuite installer un lot de plugins complémentaires dans le terminal lancé par Babun

### Installation annexe

```
pact install git
pact install gettext
pact install libsasl2
pact install ca-certificates
```

### Configuration GIT

```
git config --global user.name "your name"
git config --global user.email "your@email.com"
```

### Installation clé SSH

Déposer votre clé SSH (id_rsa + id_rsa.pub) dans le répertoire .babun/cygwin/<<VOTRE USER WINDOWS>>/home/.ssh de Babun.
Si vous n'en avez pas, générer là avec la commande

```
ssh-keygen -t rsa
```

## 2) Installation de Vagrant et Virtualbox

### Télécharger les versions conseillées

+ [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) - v4.3.18
+ [http://downloads.vagrantup.com/](http://downloads.vagrantup.com/) - v1.6.5

### Installation annexe

Une fois installer lancer la commande suivante pour automatiquement
mettre en place les extensions de Virtualbox sur les nouvelles VMs.

```
vagrant plugin install vagrant-vbguest
```

## 3) Ajouter l'outil de provision "Puppet"

Pour lié le dépôt Vagrant et le dépôt Puppet, nous utilisons les sous-modules GIT.
Pour les mettre à jour dans le futur, utilisez ces commandes :

```
git pull
git submodule update --init --recursive
```

## 4) Config SSH pour se connecter dans la VM (~/.ssh/config)

```
Host jeuxdicode.dev
    ForwardAgent yes
    HostName 192.168.50.20
    User admin
    IdentityFile "~/.ssh/id_rsa"
```