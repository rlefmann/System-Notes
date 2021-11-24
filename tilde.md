tilde.club homepage
===================

## Access

```
ssh -o "IdentitiesOnly=yes" -i ~/.ssh/<privatekey> <username>@tilde.club
```

## Syncing website with rsync

Copy remote directory to local machine:

```
rsync -avzh -e "ssh -i ~/.ssh/<privatekey>" <username>@tilde.club:public_html/ .
```

Sync to remote server (switch source and destination in the previous command):

```
rsync -avzh -e "ssh -i ~/.ssh/<privatekey>" . <username>@tilde.club:public_html/
```
