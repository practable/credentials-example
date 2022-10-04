# credentials-example
An example credentials repo - DO NOT USE IN PRODUCTION. 

You should carefully control access to your credentials, so this repo defaults to ignoring the generated credentials (see the advanced section below for how to change that). 

## Usage

Generate your credentials by running the script:

`./create-credentials`

See the generated credentials by running the script:
`grep . secret/*`

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




