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