# Jira connect

This project is forked from https://github.com/atlassian/gajira-login

Please use the offical project if possible, unless you are having same troubles:

* With Jira Server and API V2
* Using [Personal Access Tokens (PAT)](https://confluence.atlassian.com/enterprise/using-personal-access-tokens-1026032365.html)

## What this project can do

* This is a `Github action` project
* Store Jira login credentials for later user by other Github Jira actions
* Use Personal Access Tokens (PAT) instead of password or API token
* Not support Jira cloud now, please try offical project

## Usage
An example workflow to create a Jira issue for each `//TODO` in code:

```yaml
on: push

name: Jira Example

jobs:
  build:
    runs-on: ubuntu-latest
    name: Jira Example
    steps:
    - name: Jira connect
      uses: govcms-extras/github-action-jira-connect@main
      env:
        JIRA_BASE_URL: ${{ secrets.JIRA_BASE_URL }}
        JIRA_USER_EMAIL: ${{ secrets.JIRA_USER_EMAIL }}
        JIRA_API_TOKEN: ${{ secrets.JIRA_API_TOKEN }}
```

----

## Action Spec:

### Enviroment variables
- `JIRA_BASE_URL` - URL of Jira instance. Example: `https://<yourdomain>.atlassian.net`
- `JIRA_API_TOKEN` - **Access Token** for Authorization. Example: `HXe8DGg1iJd2AopzyxkFB7F2` ([How To](https://confluence.atlassian.com/cloud/api-tokens-938839638.html))
- `JIRA_USER_EMAIL` - email of the user for which **Access Token** was created for . Example: `human@example.com`

### Arguments
- None

### Writes fields to config file at $HOME/jira/config.yml
- `email` - user email
- `token` - api token
- `baseUrl` - URL for Jira instance

### Writes fields to CLI config file at $HOME/.jira.d/config.yml
- `endpoint` - URL for Jira instance
- `login` - user email

### Writes env to file at $HOME/.jira.d/credentials
- `JIRA_API_TOKEN` - Jira API token to use with CLI
