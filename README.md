# Shell Tools
Command line utilities and wrappers, useful to keep the programmers away from the GUI devil.

These tools are intended for a ZSH environment, if you still use BASH update yourself.

Windows users should install and configure WSL (1 or 2); no Unix prompt, no tools.

## Base installation
Clone the project and add the bin folder to the PATH **before** the system /bin and /usr/bin.

The wrapper tools require the main tools (mvn, svn, kubectl, etc.), install them as need.

Install the required open source tools according to your operating system.

### MacOS required tools
    brew install fzf bat jq yq dialog git-delta

### Linux/WSL required tools 
    sudo apt update
    sudo apt install fzf bat jq dialog

Download and install deb package from https://github.com/dandavison/delta/releases/latest
    
### Linux specific installations
    snap install yq

### WSL specific installations
    sudo wget -qO /usr/local/bin/yq https://github.com/mikefarah/yq/releases/latest/download/yq_linux_amd64
    sudo chmod a+x /usr/local/bin/yq

## Environment configuration
Some tools are *wrappers* for the original executable, and must be provided with the **absolute path** of their original counterpart; if not configured, they assume a default, suitable only for a standard Linux/WSL environment (MacOS requires configuration).

Some tools need only a *_HOME variable, and will stop with an error if missing.

Place the following snippet in your .zshrc/.zprofile script, and edit it according to your configuration.

**NOTE:** Every path **MUST** be absolute.

    export KUBECTL_EXECUTABLE=/usr/bin/kubectl
    export MAVEN_EXECUTABLE=/usr/bin/maven
    export SVN_EXECUTABLE=/usr/bin/svn
    export KAFKA_HOME=...
    export FLINK_HOME=...
    export ZOOKEEPER_HOME=...
    
    # Ubuntu/Debian systems
    alias bat=batcat
    
## Edit function
Some tools emit a command line snippet. I you want the text automatically placed on the command line, add the following function to your .zshrc

    edit() {
        print -z $( $* )
    }
    
Prepend *edit* to your command line to capture and edit the tool output.
