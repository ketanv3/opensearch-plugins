- [Managing OpenSearch Plugins](#managing-opensearch-plugins)
  - [Install GH](#install-gh)
  - [Install Meta](#install-meta)
  - [Check Out Plugins](#check-out-plugins)
  - [Get Repo Info](#get-repo-info)
  - [Add a New Plugin](#add-a-new-plugin)
  - [Create or Update Labels in All Plugin Repos](#create-or-update-labels-in-all-plugin-repos)
  - [Create an Issue in All Plugin Repos](#create-an-issue-in-all-plugin-repos)

## Managing OpenSearch Plugins

We use [meta](https://github.com/mateodelnorte/meta) to manage OpenSearch plugins as a set.

### Install GH

Install and configure GitHub CLI from [cli.github.com/manual/installation](https://cli.github.com/manual/installation). Authenticate with `gh auth login` and ensure that it works, e.g. `gh issue list`.

### Install Meta

```sh
npm install -g meta
```

### Check Out Plugins

```sh
cd plugins
meta git update
```

Use `meta git pull` to subsequently pull the latest revisions.

### Get Repo Info

```sh
plugins> meta gh issue list
```

### Add a New Plugin

```sh
cd plugins
meta project import new-plugin git@github.com:opensearch-project/new-plugin.git
```

### Create or Update Labels in All Plugin Repos

Install [ghi](https://github.com/stephencelis/ghi), e.g. `brew install ghi`.

```
meta exec "ghi label 'backwards-compatibility' -c '#773AA8'
```

This makes it easy to create version labels.

```
meta exec "ghi label 'untriaged' -c '#fbca04'"
meta exec "ghi label 'v1.0.0' -c '#d4c5f9'"
meta exec "ghi label 'v1.1.0' -c '#c5def5'"
meta exec "ghi label 'v2.0.0' -c '#b94c47'"
```

### Create an Issue in All Plugin Repos

Create a file for the issue body, e.g. `issue.md`.

```
meta exec "gh issue create --label backwards-compatibility --title 'Ensure backwards compatibility with ODFE' --body-file ../issue.md"
```
