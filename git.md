Git
===

## Save GitHub username and password

```
git config --global credential.helper store
```

Then run `git pull` in one of your repositories. Note that your passwords will be stored in a plaintext file `~/.git-credentials`. 

A more secure way is to create an ssh key for Github.  Go to github.com -> Settings -> SSH and GPG keys -> New SSH Key. Now save your private key to your computer.

Then, if the private key is saved as `id_rsa` in the `~/.ssh/` directory, we add it for authentication as such:

```
ssh-add -K ~/.ssh/id_rsa
```

Source: https://stackoverflow.com/questions/35942754/how-to-save-username-and-password-in-git-gitextension
