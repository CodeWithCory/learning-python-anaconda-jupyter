## Developer Notes

### Install Anaconda
- `brew cask install anaconda`
    - Will need to add `export PATH=/usr/local/anaconda3/bin:"$PATH"` to ~/.bash_profile
- Can also download directly: https://www.anaconda.com/

### Utilize virtual environments through Anaconda
- Anaconda virtual environments provide package consistence, like NPM's package-lock
- `conda init bash` - Initializes conda for use with the bash shell
- (Optional) `conda config --set auto_activate_base False` - Removes default `(base)`
- `conda env list` - lists conda python environments
- `conda create --name my_env_name python` - creates a new environment
    - Note: for this actual project, `learn-jupyter` was used instead of `my_env_name`
- `conda activate my_env_name` - activates a different environment from base
- `conda remove --name my_env_name --all` - removes an environment and all its modules
- `pip list` - lists python packages installed (will be different per environment)

### Initialize a version-controlled jupyter notebook
- `jupyter notebook` - This shell is now hosting the jupyter notebook
- Navigate to the git version-controlled directory using the GUI
- Select New > Notebook > Python 3
    - This will initialize the jupyter notebook in your version-controlled directory
- `conda env export > environment.yml` - exports a Conda environment file
    - Commit this, update as necessary as modules (dependencies) change
- `conda env create -f environment.yml` - clones an existing environment using a file
    - Use this when cloning the repo to have an identical Conda environment
- To save results, in the GUI select File > Download As
    - Save HTML to /results
    - Save Python to /python
- Before every commit, in the GUI select Cell > All Output > Clear, then Save
    - This is one method of versioning in git. Using Cell > All Output > Clear will make the commits consistent





## Misc notes
- Markdown syntax: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet