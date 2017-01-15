# teamcrypt

Encrypt data for secure sharing between teammates.

## Installation + Setup

```sh
git clone https://github.com/BrandonRomano/teamcrypt.git
cp teamcrypt/teamcrypt /usr/local/bin
```

Also, you'll have to set up an environment variable `TEAMCRYPT_SECRET`.  You can export this in your `~/.bashrc` or `~/.bash_profile`:

```
export TEAMCRYPT_SECRET="MY-TEAMS-SECRET"
```

Note, this secret must be the same for all users you plan to share with.

## Usage

```
teamcrypt, version 1.0.0

usage: man [-e encrypt] [-d decrypt]

  e encrypt : encrypt the stdin and output result to stdout
  d decrypt : decrypt the stdin and output result to stdout
```

## Examples

### Sharing Passwords

```
echo "secret-password" | teamcrypt -e
> U2FsdGVkX18/mczXJ0tobBq9yd2tCfmQgRPxUuwzUn3yIEEeENVjHw4vqvBOLa5D
```

```
echo "U2FsdGVkX18/mczXJ0tobBq9yd2tCfmQgRPxUuwzUn3yIEEeENVjHw4vqvBOLa5D" | teamcrypt -d
> secret-password
```

### Sharing Files

```
cat attack-plans.txt | teamcrypt -e > attack-plans.txt.enc
```

```
cat attack-plans.txt.enc | teamcrypt -d
> kill all humans
```

## License

[MIT](LICENSE.md)
