# Developer Notes

## Initial Setup

### Install Anaconda
- `brew cask install anaconda`
    - Will need to add `export PATH=/usr/local/anaconda3/bin:"$PATH"` to ~/.bash_profile
- Can also download directly: https://www.anaconda.com/
- `conda init bash` - Initializes conda for use with the bash shell
    - (Optional) `conda config --set auto_activate_base False` - Removes `(base)` prepend


### Utilize virtual environments through Anaconda
- Anaconda virtual environments provide package consistence, like NPM's package-lock
- Initialize the virtual environment
    - `conda env list` - lists conda python environments
    - `conda create --name my_env_name python` - creates a new environment
        - Note: for this actual project, `learn-jupyter` was used instead of `my_env_name`
    - `conda activate my_env_name` - activates a different environment from base
    - `conda remove --name my_env_name --all` - removes an environment and all its modules
- Use the correct virtual environment via ipykernel
    - These commands must be run after creating the new non-base environment. Activate the environment (`conda activate ...`) then:
    - `conda install ipykernel` - ipykernel gives the environment a jupyter kernel to run from
    - `python -m ipykernel install --user --name MYENVNAME --display-name "Python (MYENVNAME)"` - run this to give this environment kernel a name
    - In the Jupyter Notebook GUI use Kernel > Change Kernel to select the correct environment kernel to use
- Manage modules (packages/dependencies) using:
    - `conda list` - lists python packages installed (will be different per environment)
    - `conda install modulename` - installs a module for use in current environment

### Initialize a version-controlled jupyter notebook
- Initialize a Git repo in preferred location on computer
    - Current preferred method is to initialize on github.com then clone
- Run `jupyter notebook` to have the shell host the Jupyter Notebook GUI
- Navigate to the local git repo directory using the GUI
- Select New > Notebook > Python 3
    - This will initialize the jupyter notebook in your version-controlled directory
- Save a .yml conda environment file for documentation
    - Using command line, activate the conda environment, cd to the necessary directory
    - `conda env export > environment.yml` - exports a Conda environment file
    - Commit this and update as necessary as modules (dependencies) change
- To clone a previously created conda environment:
    - `conda env create -f environment.yml` clones an existing environment using a file

## Continuous development after initial setup
- Open the Jupyter Notebook
    - Type `jupyter notebook` into the command line to open the Jupyter Notebook GUI
    - Navigate to the saved location and select the .ipynb file
    - Ensure the correct Kernel is being used (Kernel > Change Kernel)
        - In this case the kernel being used is *Python (Jupyter Test)*
- To create a full/stable savestate:
    - Save results
        - In the GUI select File > Download As, Save HTML to /results, Python to /python
    - Save a python environment file to document dependencies
        - Using command line, activate the conda environment, cd to the necessary directory
        - `conda env export > environment.yml` - exports a Conda environment file
    - Commit a savestate of the working directory
        - In the GUI select Cell > All Output > Clear, then click the Save button
        - Use `git commit` (or VS Code GUI) to commit the directory to a repository



## Misc notes
- Markdown syntax guide: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet