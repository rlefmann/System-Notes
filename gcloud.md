Google Cloud Setup
==================

Download Google Cloud SDK for Linux

## Add commands to path and shell completion

Add the following lines to your `.bashrc` or `.zshrc`:

```
# The next line updates PATH for the Google Cloud SDK.
if [ -f '/home/lefmann/Downloads/Google-Cloud/google-cloud-sdk/path.zsh.inc' ]; then . '/home/lefmann/Downloads/Google-Cloud/google-cloud-sdk/path.zsh.inc'; fi

# The next line enables shell command completion for gcloud.
if [ -f '/home/lefmann/Downloads/Google-Cloud/google-cloud-sdk/completion.zsh.inc' ]; then . '/home/lefmann/Downloads/Google-Cloud/google-cloud-sdk/completion.zsh.inc'; fi
```
