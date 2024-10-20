
# to have settings that are specific to a project by passing the --local option to the config command. A config.toml file will be automatically created when you first run poetry config command. 
# create the virtualenv in a folder named .venv within the root directory of the project.
% poetry config virtualenvs.in-project true --local
# Type: boolean, Default: None
# If set to true, the virtualenv will be created in a folder named .venv within the root directory of the project.

# list the current configuration
% poetry config --list

% poetry new github-workflows-containers --src  # src layout, the code in an additional src/ parent folder
% cd github-workflows-containers
% poetry add requests
% poetry add mkdocs
# to add a dependency to a group
% poetry add pytest --group test
# to remove a package
% poetry remove <package-name>
% poetry install            # optional, only after you manually modify the pyproject.toml
% poetry env info           # display information
% poetry env info --path    # display path information

# to remove the cache folder Ubuntu ~/.cache/pypoetry/virtualenvs or macOS ~/Library/Caches/pypoetry/cache
% poetry cache clear --all .
% poetry show               # to list all the available packages

# poetry virtualevn do take up space, if you decide to remove the virtualenv
% poetry env list   # find the name, then run poetry env remove
% poetry env remove <env-name>
% poetry env remove --all   # to delete all virtual environments at once

# to generate requirements.txt file
% poetry export -f requirements.txt --output requirements.txt
# building packages With poetry
# Step 1: Configure the pyproject.toml
# Step 2: Add Files to Your Package
# Step 3: Build the Package
% poetry build
# there are two types of files: a wheel (\*.whl), which is a built distribution that can be installed quickly, and a source archive (\*.tar.gz), which includes your source code and can be built by the end-user.
# Step 4: Verify Your Build -- to check the contents of your distribution files to ensure everything is included as expected.
# Step 5: Ready for Distribution
# Use poetry publish to upload it to a package index like PyPI, or a custom repository.

# Bumps the minor version of your project (according to semantic versioning). Similar for MAJOR or PATCH .
% poetry version minor
# to spin up a virtual environment shell within the current terminal (creates one if it doesn’t exist)
% poetry shell
# to exist the sehll
% exit

# to run your tests with Poetry, from the project root, with or without flags
% poetry run pytest -v -s



# docker files
% mkdir dockerdir
% cd dockerdir
% touch entrypoint.sh   # vim text editor to add content
% touch dockerfile      # vim text editor to add content

# push to GitHub ghcr stand for github container registry
% docker login --username zhaohuiwang --password ghp_oKD...lWH ghcr.io
% curl -v -u $USER:$CR_TOKEN https://ghcr.io/v2/
% docker logout
# How to show all users in dockers group. Docker creates the docker group, but also any sudoers can use Docker. to check two group membership
grep /etc/group -e "docker"     # docker:x:1001:zhaohuiwang
grep /etc/group -e "sudo"       # sudo:x:27:zhaohuiwang
# or these two with the same result 
getent group sudo
getent group docker
# to list all the services
% sudo systemctl list-units --type=service | grep "docker" -all

# to build a container, if in the project directory
% docker build ./dockerdir -t ghcr.io/zhaohuiwang/github-workflows-containers:latest
# to publish into the GitHub container registry
% docker push ghcr.io/zhaohuiwang/github-workflows-containers:latest
# to list docker images at your local computer  
% docker image ls | grep zhaohuiwang
% docker image ls
# to remove the image from local computer
% docker image rm <IMAGE ID>
# run the image
docker run ghcr.io/zhaohuiwang/github-workflows-containers:latest
# docker looks for the image locally first, if not found then download it and run 
# go to Github > Packages > your docker image is here !


 % git init --initial-branch learning
# Initialized and set current branch name as learning
# or git init \ git checkout -b learning
% git checkout -b learning      # create and checkout learning branch
# git config init.defaultBranch <name> --global or --local # to change the default branch
% git branch --show     # or  git branch --show-current
% git checkout learning     # git switch learning  
# return: learning
# if you havenot setup use HTTPS, if you have SSH use SSH instead
% git remote add origin https://github.com/zhaohuiwang/github-workflows-containers.git
# you may reset the url to SSH once you set it up both on lcoal machine and remote GitHub account
% git remote set-url origin git@github.com:zhaohuiwang/github-workflows-containers.git
% git diff --name-only  # see what file has update
% git remote -v   # to verify the remote 
# origin  https://github.com/zhaohuiwang/github-workflows-containers.git (fetch)
# origin  https://github.com/zhaohuiwang/github-workflows-containers.git (push)
% git remote show origin                # details remote origin
% git config --get remote.origin.url    # remote origin url only
% git config --global user.email "ezhwang@gmail.com"
% git config --global user.name "zhaohuiwang"
% git config -l
% add add .
% git commit -m "initial push"
% git push --set-upstream origin learning
# username: zhaohuiwang Password: GitHub Personal access tokens 

% git fsck       # file system check, return the numbers for objects and directories
# create a directory and add content into docker-image.yml
% mkdir -p .github/workflow     # -p, --parents no error if existing, make parent directories as needed
% touch docker-image.yml
% vim docker-image.yml
