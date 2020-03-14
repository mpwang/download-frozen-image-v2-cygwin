# download-frozen-image-v2-cygwin

shell script to download docker image layers from hub.docker.com

origin source from [moby download-frozen-image-v2.sh ](https://github.com/moby/moby/blob/master/contrib/download-frozen-image-v2.sh)

modify to enable it to run on cygwin / msys2

# prerequisite

script requires (jq)[https://stedolan.github.io/jq/] and (golang)[https://golang.org/] installed

## install
### cygwin
use Cygwin installer run setup.exe to select packages to install

### msys2
    # install jq
    pacman -S mingw-w64-x86_64-libwinpthread-git
    pacman -Sy mingw-w64-x86_64-jq
    # install go
    pacman -Sy mingw-w64-x86_64-go

## setup
make sure jq and go in under `PATH`, and export `GOROOT`

on `msys2` jq go is installed under `/mingw64/bin`

edit `~/.bashrc`, and `/mingw64/bin` to PATH

    export PATH="/mingw64/bin:$PATH"
    export GOROOT="/mingw64/lib/go"


# usage

    # ./download-frozen-image-v2-cygwin.sh <dir> <repo>:<tag>
    ./download-frozen-image-v2-cygwin.sh hello hello-world:latest
    
    tar -cC 'hello' . > hello.image
    # load docker image
    docker load < hello.image

