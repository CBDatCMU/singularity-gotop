Bootstrap: docker
From: ubuntu:16.04

IncludeCmd: yes

%runscript
    exec /bin/bash "$@"

%post
    echo "Update aptitude"
    /usr/bin/apt-get update && apt-get install -y --no-install-recommends apt-utils
    /usr/bin/apt-get update --fix-missing
    /usr/bin/apt-get install -y curl git
    git clone --depth 1 https://github.com/cjbassi/gotop /tmp/gotop
    /tmp/gotop/scripts/download.sh
    mv gotop /usr/local/bin
    rm -rf /tmp/gotop

####################################################################################
%appenv gotop
    APP=/usr/local/bin/gotop
    export APP

%apphelp gotop
    For more information about goto visit https://github.com/cjbassi/gotop

%apprun gotop
    gotop "$@"
