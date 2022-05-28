# lab16-encrypt-file

[Encrypt a file for GitHub Actions](https://www.gab.lc/articles/encrypt_file_for_github_actions/)

[GitHub Actions - Encrypted Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets#limits-for-secrets) 

See the [workflow file](https://github.com/dliulabs-hq/lab16-encrypt-file/actions/workflows/encrypt-file.yml)

## Setup GnuPG

```
brew install gnupg
```

## Encrypt a file

```
gpg --symmetric --cipher-algo AES256 --batch --passphrase "<password>" some_file.json
```

```
for file in $(ls | grep -v ".gpg"); do gpg -c --cipher-algo AES256 --compress-algo 1 --batch --passphrase "<password>" $file && rm -f $file; done
```
