Git
===

## User setup

```
git config --global user.name "Raoul Lefmann"
git config --global user.email "raoul.lefmann@gmail.com"
git config --global github.user "rlefmann"
git config -l
```

## Save GitHub username and password

```
git config --global credential.helper store
```

## GitHub personal access token

- Go to the https://github.com/settings/tokens (Settings -> Developer settings -> Personal access tokens)
- Generate new token
- Copy the token `ghp_...`

Then run `git pull` in one of your repositories. When prompted for the password, enter the `ghp_...` token as password. Note that your passwords will be stored in a plaintext file `~/.git-credentials`. 


## SSH key (unsure if this still works)

A more secure way is to create an ssh key for Github.  Go to github.com -> Settings -> SSH and GPG keys -> New SSH Key. Now save your private key to your computer.

Then, if the private key is saved as `id_rsa` in the `~/.ssh/` directory, we add it for authentication as such:

```
ssh-add -K ~/.ssh/id_rsa
```

## References

- https://www.edgoad.com/2021/02/using-personal-access-tokens-with-git-and-github.html
- https://stackoverflow.com/questions/35942754/how-to-save-username-and-password-in-git-gitextension
