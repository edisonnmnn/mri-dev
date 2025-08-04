# Mac UI Installation Guide 

This is a detailed guide for installing the [MRI4ALL Console](https://github.com/mri4all/console/wiki) Devlopment Environment for personal M1 and M2 Macs. 

The original setup instructions were written for Intel/AMD CPUs using a virtual machine, so users with M1 and M2 Macs need to manually install all dependencies.

## Note

At the current stage, the acq/recon are meant to be run in parallel with the UI, so this document will only cover installing and running the UI, as those features will be added later.

## Installation

Note: The original installation to install dependencies on Linux devices can be found here: 
(https://github.com/mri4all/console/wiki/Setting-up-the-dev-environment)


### Folder structure
- Create a folder for the MRI4ALL console on your system (e.g. mri4all)
```
/mri4all
```
- In the newly created folder, make the following directories:
```
/mri4all/console
/mri4all/config
/mri4all/data
/mri4all/logs
```
- Check out the console software from the repo into the console folder: (https://github.com/edisonnmnn/mri-console)
```
git clone https://github.com/edisonnmnn/mri-console ~/mri4all/console
```

Note: The main console software is a modularized copy the `console/` component of the MRI4ALL system adapted for development on M1 and M2 machines.  The original repository is here: (https://github.com/mri4all/console)


### Install Required Packages

- Install the macOS equivalents of the Linux packages found in `install.sh`
```
brew install git git-lfs ffmpeg dcmtk python qt wget curl gdcm
```
- Optionally, you can also install the Docker (Check with the original `install.sh` file to see how you can do this)


### Setup Python Environment

- To be consistent with the Python version of when MRI4ALL was made, make sure to install Python 3.11 on your system e.g. (if not already installed) 
```
brew install python@3.11
```
- Create a new virtual environment using Python 3.11 in the mri4all directory
```
/opt/homebrew/bin/python3.11 -m venv env
source env/bin/activate
```
- Confirm you are using Python 3.11
```python
python --version
# Should output: Python 3.11.x
```

###
- Upgrade pip and install dependecies from `requirements.txt` in `console` directory
```
pip install --upgrade pip
pip install -r requirements.txt
```

### Starting the console

To start the console, activate your Python virtual environment with source /opt/mri4all/env/bin/activate
```
source /env/bin/activate
```
To start the UI service, run:
```
python run_ui.py
```

## Fixes/Issues:

- Remove the need for password authentication

 - The run_ui file uses `systemctl` which is a linux specific system call, however this is kept in for debugging purposes because it allows for running the acquisition and recon services maually in parallel.

 # TODO:

- Include marcos installation guide 
- *Red Pitaya ip should be changed in config file*
 