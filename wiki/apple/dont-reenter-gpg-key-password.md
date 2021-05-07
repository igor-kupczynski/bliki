---
title: Create a gpg key and don't reenter its password on macos
---

# Create a gpg key and don't reenter its password on macos

## Macos prerequisites to avoid reentering password all the time

* Install pinentry-mac (UI to enter passwords for gpg keys)

        brew install pinentry-mac


* Update/create `~/.gnupg/gpg-agent.conf`

        pinentry-program /usr/local/bin/pinentry-mac


* Update/create `~/.gnupg/gpg.conf`

        use-agent


* Add to `~/.zshrc` or `~/.bashrc`

        export GPG_TTY=$(tty)
        gpgconf --launch gpg-agent


### If gpg gives you errors later on try starting a new shell and then

        gpgconf --kill gpg-agent
        gpgconf --launch gpg-agent
        echo "foo" | gpg --clearsign


## Generate key pair with multiple emails

* Generate key with the first email

        gpg --full-gen-key
        # You can select 1 for general purpose, or 4 for commit signing only
        # Put your first email
        # Add a passphrase


* (optional) Save passphrase and the fingerprint to 1password / password manager 

* List key details

        gpg --list-secret-keys --keyid-format SHORT


* Add other emails

        gpg --edit-key <key-id>


* Then on gpg prompt

        gpgp> adduid
        # type the second email
        gnupg> uid 2  # or other UID
        gnupg> trust
        # Type "5" (for "I trust ultimately")
        gnupg> save


## Keybase
* (optional) Store the key on Keybase  (alt: store it in a password manager?)

        keybase pgp list
        keybase pgp push-private <fingerprint>
        keybase pgp select --multi


* Load the key from Keybase on another laptop

        keybase pgp list
        keybase pgp pull-private <fingerprint>


## Reference

* https://withblue.ink/2020/05/17/how-and-why-to-sign-git-commits.html
