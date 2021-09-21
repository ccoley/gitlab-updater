# [Gitlab Updater](https://git.codingallnight.com/chris/gitlab-updater)

This tool upgrades GitLab Omnibus to the most recent patch version of the previous minor version. GitLab maintains security fixes for the 3 most recent minor versions, but the latest minor version frequently has regressions.

For example, if the available versions are as follows:

    10.2.1  <-  Latest version
    10.2.0
    10.1.2  <-  Target version, most stable, still secure
    10.1.1
    10.1.0

then the previous minor version is 10.1.x and this tool will upgrade GitLab Omnibus to the latest patch version in the 10.1.x family.

> This tool will update the APT package cache, so it must be run as root or with `sudo`

## Usage

> Use the `-h` flag to see full usage documentation.

To update the Gitlab Omnibus package all you have to do is run this command, which will install the appropriate version and run the normal Gitlab update process.

```sh
$ sudo gitlab-updater/update-gitlab
Upgrading from 10.0.7-ce.0 to 10.1.2-ce.0
...
```

### Dry Run Mode

You can run the tool in dry-run mode using the `-d` flag to see if an update is available and to see what version will be chosen as the update target.

```sh
$ sudo gitlab-updater/update-gitlab -d
APT cache is stale; updating...

Would upgrade from 10.0.7-ce.0 to 10.1.2-ce.0
```

### Making Tool Globally Executable

The tool can be made available to multiple users by deploying it to the `/usr/local/bin/` directory on your server.

```sh
$ sudo mv gitlab-updater/update-gitlab /usr/local/bin/update-gitlab
$ sudo chmod +x /usr/local/bin/update-gitlab
```

You can also create a symlink to make the tool executable under multiple names.

```sh
$ ln -s /usr/local/bin/update-gitlab /usr/local/bin/gitlab-update
```



[_modeline]: # ( vi: set ts=4 sw=4 et wrap ft=markdown: )
