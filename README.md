# MastoPurge
*Purges Mastodon accounts by deleting old posts and favs.*

MastoPurge connects to your Mastodon account and automatically mass-deletes your old posts and favs.

MastoPurge is executed as a command line application on your own PC. You do not need to rely on third parties.

**Please note:**
* Deleting hundreds or thousands of posts can take a long time due to Mastodon API limits/throttling
* There is no guarantee that your federated toots are deleted on every foreign instance

## Reference

This is a fork of https://github.com/ThomasLeister/mastopurge/ which has been archived due to Mastodon's [auto-delete](https://github.com/mastodon/mastodon/pull/16529) feature. However, this feature does not cover favs.

## Compile and run from source:

(Golang must be set up)

    go run mastopurge.go

## Usage instructions

1. Download and run MastoPurge (see above)
2. Enter the domain name of your Mastodon home instance
3. MastoPurge will ask you to visit a certain URL. Open this URL in your web browser
4. Authorize MastoPurge to access your Mastodon account. A Code will be displayed.
5. Enter the code into MastoPurge
6. Select a timespan of your choice. Posts from this time range will *not* be deleted. Older posts will be removed. _(Note: "pinned posts" will **not** be deleted!)_
7. Wait. Removing hundreds or thousands of posts can take a long time due to API limits.
8. MastoPurge will remember your account the next time you use it. No more authentication needed. If you want to use another account, delete the `.mastopurgesettings` file.


### Non-interactive mode

After you have run Mastopurge in interactive mode, once (see instructions above), you will be able to run it in non-interactive mode, if you like. This mode enables you to run Mastopurge automatically e.g. as a Crob Job.

Example:

```
./mastopurge --noninteractive --maxage "30 days"
```

### Dry-run mode

If you'd like to check whether Mastopurge works properly (without actually deleting your posts!), you can try the "dry run mode":

```
./mastopurge --noninteractive --maxage "30 days" --dryrun
```

### Favourites

If you want to undo favourites, add the `--favs` parameter:

```
./mastopurge --maxage "365 days" --favs
```

### Verbose output

If you are really curious about some internals, add verbose output:

```
./mastopurge --maxage "365 days" --verbose
```
