# Setting up Google drive sync with RClone

```
rclone config
```

* `n` to create a new remote
* call it `googledrive`
* use auto config
* create an empty directory `~/Drive`

## Syncing to and from google drive

```
alias sync_from_drive="rclone sync googledrive: ~/Drive"
alias sync_to_drive="rclone sync ~/Drive googledrive:"
```

Be careful to call `sync_from_drive` when you start working and `sync_to_drive` when you stop working.

To see, what changes will be made, use the `--dry-run` argument.
