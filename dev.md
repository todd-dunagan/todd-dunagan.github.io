# Dev
## Installables
### [Brew](https://brew.sh)
### [Oh My Zsh!](https://github.com/ohmyzsh/ohmyzsh)
```
plugins=(
 git'
 github
 golang
 helm
 jira
 kubectl
 mvn
 history
 zsh-autosuggestions
)
```
#### [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#oh-my-zsh)

### [Raycast](https://raycast.com)
* Set default fallback commands

## Tools
#### Postman
#### IntelliJ
#### VSCode

## CLI
### Grep
#### Recursive search with include / exclude
```
grep -r "[test to find]" . --exclude-dir={[array of vals]} --include="*.[file_ext]"
```

### Backend Processes 
#### Using `launchctl` for scheduled processes/jobs
* Navigate to: `~/Library/LaunchAgents`
* Create `.plist` file here
* Load and enable the the plist file via: `launchctl bootstrap gui/[uid] [filename].plist`

#### List processes
`launchctl list |grep [qualified path]`

#### Disable scheduled processes
`launchctl bootout gui/[uid] [filename].plist`

### Bash CheatSheet
https://devhints.io/bash

### Docker
Alias | Command | Description
----- | ------- | -----------
dils | docker image ls | List docker images
dcin | docker container inspect | Display detailed information on one or more containers
dlo | docker container logs | Fetch the logs of a docker container
dcls | docker container ls | List all the running docker containers
dclsa | docker container ls -a | List all running and stopped containers

from: https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/docker

### Kubernetes (K8s)
Alias | Command | Description
----- | ------- | -----------
kgpa | kubectl get all, all namespaces pods | List all pods in ps output format network info etc.
kgsa | kubectl get svc, all namespaces | List all services including
klf | kubectl logs -f | Stream the logs for a container or resource (follow)
kgp | kubectl get pods | List all pods in ps output format
kgpl | kgp -l | Get pods by label. Example: kgpl "app=myapp" -n myns
kgpn | kgp -n | Get pods by namespace. Example: kgpn kube-system
kdp | kubectl describe pods | Describe all pods
kl | kubectl logs | Print the logs for a container or resource

from: https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/kubectl

### Snippets + Hints

#### Bash
I've googled these types of snippets many time over the years. From an amalgam of web content.
#### Handling parameters in bash script
```
while [[ "$1" =~ ^- && ! "$1" == "--" ]]; do case $1 in
  -h | --help)
    display_help
    ;;
  # add options following the above pattern
esac; shift; done
```
#### Adding help to a script
Trigger the following by adding an option to your argument handler, most likely with a `-h` option.
```
me=`basename "$0"` # gets name of this file

display_help() {
    echo "Usage: ${me} [option...]" >&2
    echo
    echo "   -a, --[long name for a]              [description of a]"
    echo "   -b, --[long name for b]              [description of b]"
    echo
    # echo some stuff here for the -a or --add-options
    exit 0
}
```
#### Find a script and edit in Vim
```
vim $(which [script-name])
```
