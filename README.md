# CARPC

## Description

This repository contains ***CARPC*** manifest files and description how to build it.

## Sync and build instructions.


### Defining variables:

<pre>
ROOT_DIR="/mnt/host/tda/carpc/"

REPO_TOOL_URL="https://storage.googleapis.com/git-repo-downloads/repo"
REPO_TOOL="./repo"

declare -A MANIFEST=(
   ["URL"]="https://github.com/dterletskiy/carpc-manifest.git"
   ["BRANCH"]="main"
   ["NAME"]="default.xml"
)
</pre>


### Create and go to source directory:

<pre>
mkdir -p ${ROOT_DIR}
cd ${ROOT_DIR}
</pre>


### Install repo tool:

<pre>
curl ${REPO_TOOL_URL} > repo
chmod a+x repo
</pre>


### Sync ***CARPC*** project:

<pre>
${REPO_TOOL} --trace init --manifest-url=${MANIFEST[${URL}]}  --manifest-name=${MANIFEST[${NAME}]}  --manifest-branch=${MANIFEST[${BRANCH}]} --depth=1
${REPO_TOOL} --trace sync --current-branch --no-clone-bundle --no-tags --fetch-submodules
</pre>

### Build ***CARPC*** project using build script:

Configure project:

<pre>
source/do.sh --action=config
</pre>

Build project with all targets:

<pre>
source/do.sh --action=build
</pre>

Build specific target:

<pre>
source/do.sh --action=build --target=[target]
</pre>

Deploy:

<pre>
source/do.sh --action=install
</pre>

Clean:

<pre>
source/do.sh --action=clean
</pre>

Hard clean:

<pre>
source/do.sh --action=pure
</pre>
