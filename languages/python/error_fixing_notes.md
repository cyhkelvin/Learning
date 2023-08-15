# error fixing notes

## packages
### opencv
 - ERROR: Could not build wheels for opencv-python which use PEP517 and cannot installed directly
    - solution: update pip 
 - ERROR: Could not build wheels for opencv-python which is required to install pyproject.toml-based projects
    - occured since dependencies with visual studio libraries, installed 4.5.5.62 version to avoid