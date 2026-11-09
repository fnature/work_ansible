# work_ansible
ansible for work

## Kitty

`work_ansible_debian.yaml` imports the sibling playbook `kitty.yaml`.
It installs the latest official stable Kitty under `~/.local/kitty.app` when
missing or older than 0.28.0, then adds a user-local application launcher with
the official icon. Run it as your desktop user, without sudo.

Preview only the Kitty changes:

```sh
ansible-playbook -i localhost, -c local work_ansible_debian.yaml --tags kitty --check --diff
```

Apply only the Kitty changes:

```sh
ansible-playbook -i localhost, -c local work_ansible_debian.yaml --tags kitty
```

Or run the standalone playbook directly:

```sh
ansible-playbook -i localhost, -c local kitty.yaml
```

A compatible existing installation is kept and subsequent runs make no changes.
To explicitly update it to the latest stable release:

```sh
ansible-playbook -i localhost, -c local kitty.yaml -e kitty_update=true
```

The official installer requires network access, `curl` or `wget`, and `tar` with
xz support. The `kitty` tag skips Homebrew, system packages, and Teams. It does
not remove the Debian Kitty package, change shell PATH, set a default terminal,
or launch a terminal window. Reopen Kitty after an update.
