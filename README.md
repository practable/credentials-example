# credentials-example
An example credentials repo

This repo contains a script that will generate some example secrets for a pair of instances (`dev`, `xx0`) so as to show the directory structure expected by [admin-tools](https://github.com/practable/admin-tools). The secrets are not checked into this public repo for security. See below for production usage hints.


## Usage

Generate credentials for pair of instances (`dev`, `xx0`) by running the script:

`./create-credentials`

See the generated credentials 

```
$ grep . secret/app-example-org/dev/* 
secret/app-example-org/dev/book.pat:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
secret/app-example-org/dev/jump.pat:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
secret/app-example-org/dev/project:some-project-0000
secret/app-example-org/dev/relay.pat:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
$ grep . secret/app-example-org/xx0/*
secret/app-example-org/xx0/book.pat:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
secret/app-example-org/xx0/jump.pat:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
secret/app-example-org/xx0/project:some-project-0000
secret/app-example-org/xx0/relay.pat:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

You should carefully control access to your credentials, so this repo defaults to ignoring the generated credentials (see the advanced section below for how to change that). 

## Production usage

 Only do this if you understand the risks involved (you'll know if you know; if in doubt, don't). 
 
- install and configure [git secrets](https://github.com/msalemcode/git-secrets) to scan all repos for secrets (add these [patterns](https://github.com/timdrysdale/git-secrets-patterns))
- Fork and rename this repo, e.g. to `credentials-production` 
- set the repo to private. Double check this!
- clone to your `~/sources` directory (or wherever you keep your code)
- Generate a credential set `./create-credentials`
- edit `.gitignore` to remove `secret/`
- `git add secret/`, commit and push to your now-private repo
- create a symbolic link to `~/secret` so [admin-tools](https://github.com/practable/admin-tools) and other [practable](https://github.com/practable) scripts can find the credentials:
  ```
  eval "ln -s $HOME/sources/credentials-production/secret $HOME/secret" 
  ```




