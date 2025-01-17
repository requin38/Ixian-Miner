# Ixian-Miner
CPU mining software for the Ixian cryptocurrency with support for pools.

## Development branches

There are two main development branches:
* master: This branch is used to build the binaries for the official IXIAN DLT network. It should change slowly and be quite well-tested. This is also the default branch for anyone who wishes to build their Ixian software from source.
* development: This is the main development branch and the source for testnet binaries. The branch might not always be kept bug-free, if an extensive new feature is being worked on. If you are simply looking to build a current testnet binary yourself, please use one of the release tags which will be associated with the master branch.


## Running
Download the latest binary release or you can compile the code yourself.
### Windows
Right-click the run.bat file in the IxianMiner directory and choose Edit. In the notepad window, modify YOUR_ADDRESS with your Ixian wallet address and WORKER_NAME with a name for your mining rig. Then choose File -> Save and close the window. Double-click on the run.bat file to start mining to your wallet address.

or

Open a terminal in the IxianMiner directory and type
```
IxianMiner.exe -h
```
to find out how to configure and run the IxianMiner.

### Linux
Download and install the latest Mono release for your Linux distribution. 
The default Mono versions shipped with most common distributions are outdated.

Go to the [Mono official website](https://www.mono-project.com/download/stable/#download-lin) and follow the steps for your Linux distribution.
We recommend you install the **mono-complete** package.

Navigate to the IxianMiner Release folder and execute IxianDLT.exe under mono:
```
mono IxianMiner.exe -h
```
to find out how to configure and run the IxianMiner.

## Building
### Windows
Visual Studio 2017 is required (Community Edition is fine), you can get it from here: [Visual Studio](https://visualstudio.microsoft.com/)

Several NuGetPackages are downloaded automatically during the build process.

### Linux
Download and install the latest Mono release for your Linux distribution. The default Mono versions shipped with most common distributions are outdated.

Go to the [Mono official website](https://www.mono-project.com/download/stable/#download-lin) and follow the steps for your Linux distribution.

We recommend you install the **mono-complete** package.

For Debian based distributions such as Ubuntu, type
```
sudo apt install mono-complete nuget msbuild git gcc
```
or if you have a Redhat based distribution, type
```
sudo yum install mono-complete nuget msbuild git gcc
```

Next you'll need to build the IxianMiner solution. You can do this by typing the following commands in the terminal:
```
git clone https://github.com/ProjectIxian/Ixian-Miner.git
cd Ixian-Miner
nuget restore IxianMiner.sln
msbuild IxianMiner.sln /p:Configuration=Release
```
The IxianMiner will be compiled and placed in the IxianMiner/bin/Release/ folder.

For the IxianMiner to work correctly, you'll need to copy the libargon2.so shared library to the IxianMiner/bin/Release/ folder. You can use the library provided in the latest Ixian Binary release.

If you want to build the libargon2 shared library yourself, you can do this by typing the following commands in the terminal:
```
git clone https://github.com/P-H-C/phc-winner-argon2.git
cd phc-winner-argon2
make
```
Copy the resulting libargon2.so file to the IxianMiner/bin/Release/ folder, like so:
```
cp libargon2.so.1 ../IxianMiner/bin/Release/libargon2.so
```
Adjust the directory as neccessary, if you compiled the argon library in a different location. Please note that the library name generated by the argon project is libargon2.so.1, but Ixian requires libargon2.so. The file can be safely renamed, as shown in the command above.

## Get in touch / Contributing

If you feel like you can contribute to the project, or have questions or comments, you can get in touch with the team through Discord: (https://discord.gg/dbg9WtR)

## Pull requests

If you would like to send an improvement or bugfix to this repository, but without permanently joining the team, follow these approximate steps:

1. Fork this repository
2. Create a branch (preferably with a name that describes the change)
3. Create commits (the commit messages should contain some information on what and why was changed)
4. Create a pull request to this repository for review and inclusion.
