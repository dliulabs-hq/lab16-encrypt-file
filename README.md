# lab16-encrypt-file

[Encrypt a file for GitHub Actions](https://www.gab.lc/articles/encrypt_file_for_github_actions/)

[GitHub Actions - Encrypted Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets#limits-for-secrets) 

## Setup GnuPG

```
brew install gnupg
```

## Encrypt a file

```
gpg --symmetric --cipher-algo AES256 --batch --passphrase "<password>" some_file.json
```

```
$ls | gpg --multifile --encrypt

for x in *; do 
  gpg -r (yourencrytionkey.com) -o $x.pgp -e $x
done

FOR %i in (C:\GPGFILES\*.gpg) do (gpg --batch --yes --passphrase key123 --output "%i.txt" --decrypt "%i")
`
for file in $(ls | grep -v ".gpg"); do gpg -c --cipher-algo AES256 --compress-algo 1 --batch --passphrase "<password>" $file && rm -f $file; done
```

```
pushd input
echo "hello, world\n"
echo "hello, world"
echo "hello, world\!"
echo "hello, world\!" > test.txt
gpg --symmetric --cipher-algo AES256 --batch --passphrase "<password>" test.txt
popd

gpg --symmetric --cipher-algo AES256 --batch --passphrase "<password>" some_file.json
gpg --symmetric --cipher-algo AES256 --batch --passphrase "<password>" some_file.json

