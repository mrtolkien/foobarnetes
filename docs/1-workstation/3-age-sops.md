# Age + SOPS setup

[Original tutorial](https://github.com/k8s-at-home/flux-cluster-template/#-setting-up-age)

## Create an Age Private + Public key

The Age key will encode all the secrets in our repository. The following command creates a private and public keys pair and moves it to where it's expected

```shell
age-keygen -o age.agekey
mkdir -p ~/.config/sops/age
mv age.agekey ~/.config/sops/age/keys.txt
```

## Save the public key

During the process that we just did, or inside the `~/.config/sops/age/keys.txt` file, you can see your **public key**. Save it somewhere as we will need it again in a few minutes when creating our `.sops.yaml` configuration file.

## Load the secret in your shell

Export the `SOPS_AGE_KEY_FILE` variable in your shell config file (`bashrc`, `zshrc`, `config.fish`):

```shell
export SOPS_AGE_KEY_FILE=~/.config/sops/age/keys.txt
```

Don't forget to reload your shell or source your shell config file afterwards!

## SOPS basic setup

`SOPS` relies on a file called `.sops.yaml` being at the root of your `git` repository to know what it needs to encode.

For starters, you can use this very simple `.sops.yaml` file that will:

- Encode every file called `*.sops.yaml`
- Encode all its fields
- Use the keys you just created

Do not forget to substitute **your own public key** in the `age_public_key` field:

```yaml
# .sops.yaml
creation_rules:
  - path_regex: .*.sops\.ya?ml
    key_groups:
      - age:
          - age_public_key
```

If you want to be more granular you can use the `encrypted_regex` flag as defined [in the SOPS documentation](https://github.com/mozilla/sops#encrypting-only-parts-of-a-file), which lets you select which keys get encoded.

## Usage

### Shell

You can call `sops --encrypt` and `sops --decrypt` by hand on individual files:

```shell
sops --encrypt --in-place file.sops.yaml
sops --decrypt --in-place file.sops.yaml
```

### VS Code extension

The [SCode SOPS extension](https://marketplace.visualstudio.com/items?itemName=signageos.signageos-vscode-sops) makes using SOPS-encrypted files a breeze.

Any file that fits the regex will be automatically encoded in-place, and you will be able to edit it directly like it was a plaintext file.

## Pre-commit

More importantly, we can make sure all files that fit our `creation_rules` in `.sops.yaml` are properly encoded before they are committed.
