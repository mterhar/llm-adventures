# Git Setup

1. Set your name and email.
2. Set your access token

## 1. Set your name and email

```shell
git config --global user.name First Last
git config --global user.email my-email@domain.com
```


## 2. To make good use of GitHub, you'll want a local token.

In GitHub, [create a token that can read-write repos](https://github.com/settings/personal-access-tokens).

Locally, run the command to set the credential hepler

```shell
git config --global credential.helper manager
```

And then when you run `git push` to save your work back to the server, it will ask for the username and token.
