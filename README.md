[![Dependencies Status](https://david-dm.org/logerfo/target-label-action/dev-status.svg)](https://david-dm.org/logerfo/target-label-action?type=dev)

# Target Label Action
This action will check if the pull request target branch matches with its labels.

## Setting up
Create a file named `.github/workflows/target-label.yml`.

### Minimal Configuration
```yml
name: Target Label
on: 
  pull_request:
    types: [labeled, unlabeled]
    
jobs:
  build:
    name: Target Label
    runs-on: ubuntu-16.04
    steps:
    - uses: actions/checkout@master
    - uses: Logerfo/target-label-action@0.0.1
      with:
        github-token: ${{ secrets.GITHUB_TOKEN }}
```

### Complete configuration
All values are default.
```yml
name: Target Label
on: 
  pull_request:
    types: [labeled, unlabeled]
    
jobs:
  build:
    name: Target Label
    runs-on: ubuntu-16.04
    steps:
    - uses: actions/checkout@master
    - uses: Logerfo/target-label-action@0.0.1
      with:
        github-token: ${{ secrets.GITHUB_TOKEN }} # The `GITHUB_TOKEN` secret.
        config-path: .github/target-label.yml # The path of the addtional configurations file.
        apply: never # `never` to never apply labels;
                     # `first` to always apply the first label;
                     # `single` to only apply when the number of labels is one.
```

### Additional configurations file
You also need create a additional configuration file. The default path is `.github/target-label.yml`, but you can change it in the action configuration file, as shown above.  
The file must follow the following structure:
```yml
target-branch: [labels]
```
For example:
```yml
master: [bug, enhancement]
dev: [feature]
```

### Auto update
You can use (at your own risk) the `release` branch instead of the specific version tag.  
Never user `master`, since the distribution file does not exist in this branch and the action will always fail.

## Changelog
Click [here](CHANGELOG.md).

## Contributing
If you have suggestions for how close-label could be improved, or want to report a bug, open an issue! We'd love all and any contributions.

For more, check out the [Contributing Guide](CONTRIBUTING.md).

## Donate

<img src="https://i.imgur.com/ndlBtuX.png" width="200">

BTC: 1LoGErFoNzE1gCA5fzk6A82nV6iJdKssSZ
