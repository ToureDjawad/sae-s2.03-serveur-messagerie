# Serveur de messagerie d'entreprise | SAÉ 2.03

Installation et configuration d'un serveur de messagerie interne sous Debian pour une PME fictive (EuroBD), dans le cadre de la SAÉ 2.03 « Installation de services réseau » du BUT Informatique (IUT d'Aix-Marseille, site d'Arles).

**Auteur :** Djawad TOURE ISSAHOU (travail individuel)

## Contenu

| Document | Description |
| --- | --- |
| [`rapport-technique.pdf`](rapport-technique.pdf) | Procédure complète en 8 pages, de la machine virtuelle aux tests |
| [`note-comparative.pdf`](note-comparative.pdf) | Comparaison de trois solutions de messagerie et recommandation |
| [`presentation.pdf`](presentation.pdf) | Synthèse pour la direction |

## Environnement

- Debian 13 dans une machine virtuelle VirtualBox, poste hôte Windows
- Deux cartes réseau : NAT pour Internet, réseau privé hôte `192.168.56.0/24` en adressage fixe
- Postfix 3.10 (SMTP), Dovecot 2.4 (IMAP et POP3), stockage Maildir
- Domaine interne `eurobd.lan`, client Mozilla Thunderbird

## Étapes couvertes

1. Plan d'adressage et configuration des interfaces (`/etc/network/interfaces`)
2. Installation et configuration de Postfix (`main.cf` : `myhostname`, `mydomain`, `home_mailbox = Maildir/`)
3. Installation et configuration de Dovecot (`10-mail.conf`, `10-auth.conf`)
4. Création des boîtes aux lettres des salariés
5. Tests en ligne de commande (`telnet localhost 25`, `mail.log`) puis depuis Thunderbird
6. Dépannage : ports à l'écoute (`ss -tlnp`), configuration effective (`doveconf -n`)
