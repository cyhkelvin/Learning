# windows wsl

## path 
  - [reference](https://www.cnblogs.com/lepeCoder/p/wsl_dir.html)
  - `C:\Users\<UserName>\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu18.04onWindows_79rhkp1fndgsc\LocalState\rootfs`
  - `\\wsl$` can manipulate directory


## notes
### steps to install anaconda on Windows Ubuntu Terminal
- If you have already install an old version, Run `$ bash Anaconda[YOUR VERSION].sh -u` to update version from previous one in step 5.
- [reference](https://gist.github.com/kauffmanes/5e74916617f9993bc3479f401dfec7da)
1. Install WSL (Ubuntu for Windows - can be found in Windows Store). I recommend the latest version (I'm using 18.04) because there are some bugs they worked out during 14/16 (https://github.com/Microsoft/WSL/issues/785)
2. Go to https://repo.continuum.io/archive to find the list of Anaconda releases
3. Select the release you want. I have a 64-bit computer, so I chose the latest release ending in `x86_64.sh`. If I had a 32-bit computer, I'd select the `x86.sh` version. If you accidentally try to install the wrong one, you'll get a warning in the terminal. I chose `Anaconda3-5.2.0-Linux-x86_64.sh`.
4. From the terminal run `wget https://repo.continuum.io/archive/[YOUR VERSION]`. Example: `$ wget https://repo.continuum.io/archive/Anaconda3-5.2.0-Linux-x86_64.sh`
5. Run the installation script: `$ bash Anaconda[YOUR VERSION].sh` (`$ bash Anaconda3-5.2.0-Linux-x86_64.sh`)
6. Read the license agreement and follow the prompts to accept. When asks you if you'd like the installer to prepend it to the path, say yes.
7. Optionally install VS Code when prompted (some have reported this installation doesn't work - checkout https://gist.github.com/kauffmanes/5e74916617f9993bc3479f401dfec7da#gistcomment-3665550)
8. Close the terminal and reopen it to reload .bash configs.
9. To test that it worked, run `$ which python`. It should print a path that has anaconda in it. Mine is `/home/kauff/anaconda3/bin/python`. If it doesn't have anaconda in the path, do the next step. Otherwise, move to step 11.
10. Manually add the Anaconda bin folder to your PATH. To do this, I added "export PATH=/home/kauff/anaconda3/bin:$PATH" to the bottom of my ~/.bashrc file. 
11. To open jupyter, type `$ jupyter notebook --no-browser`. The no browser flag will still run Jupyter on port 8888, but it won't pop it open automatically. it's necessary since you don't have a browser (probably) in your subsystem. In the terminal, it will give you a link to paste into your browser. If it worked, you should see your notebooks!


### release removed space in subsystem
- [reference](https://zhuanlan.zhihu.com/p/358528257)
- find vhd file of wsl, usually storage in `%PROFILE%\AppData\Local\Packages\CanonicalGroupLimited.UbuntuonWindows_79rhkp1fndgsc\LocalState\`
- open powershell and command
  ``` bat
    wsl --shutdown
    diskpart
    # open window Diskpart
    select vdisk file="C:\WSL-Distros\…\ext4.vhdx"
    attach vdisk readonly
    compact vdisk
    detach vdisk
    exit
  ```
