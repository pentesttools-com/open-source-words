simple python version management pyenv pyenv lets you easily switch between multiple versions of python its simple unobtrusive and follows the unix tradition of single purpose tools that do one thing well this project was forked from rbenv and ruby build and modified for python pyenv does let you change the global python version on a per user basis provide support for per project python versions allow you to override the python version with an environment variable search commands from multiple versions of python at a time this may be helpful to test across python versions with tox in contrast with pythonbrew and pythonz pyenv does not depend on python itself pyenv was made from pure shell scripts there is no bootstrap problem of python need to be loaded into your shell instead pyenvs shim approach works by adding a directory to your path manage virtualenv of course you can create virtualenv yourself or pyenv virtualenv to automate the process table of contents how it works understanding path understanding shims choosing the python version locating the python installation installation basic github checkout upgrading homebrew on mac os x advanced configuration uninstalling python versions command reference development version history license how it works at a high level pyenv intercepts python commands using shim executables injected into your path determines which python version has been specified by your application and passes your commands along to the correct python installation understanding path when you run a command like python or pip your operating system searches through a list of directories to find an executable file with that name this list of directories lives in an environment variable called path with each directory in the list separated by a colon usr local bin usr bin bin directories in path are searched from left to right so a matching executable in a directory at the beginning of the list takes precedence over another one at the end in this example the usr local bin directory will be searched first then usr bin then bin understanding shims pyenv works by inserting a directory of shims at the front of your path pyenv root shims usr local bin usr bin bin through a process called rehashing pyenv maintains shims in that directory to match every python command across every installed version of python—python pip and so on shims are lightweight executables that simply pass your command along to pyenv so with pyenv installed when you run say pip your operating system will do the following search your path for an executable file named pip find the pyenv shim named pip at the beginning of your path run the shim named pip which in turn passes the command along to pyenv choosing the python version when you execute a shim pyenv determines which python version to use by reading it from the following sources in this order the pyenv version environment variable if specified you can use the pyenv shell command to set this environment variable in your current shell session the application specific python version file in the current directory if present you can modify the current directorys python version file with the pyenv local command the first python version file found if any by searching each parent directory until reaching the root of your filesystem the global pyenv root version file you can modify this file using the pyenv global command if the global version file is not present pyenv assumes you want to use the system python in other words whatever version would run if pyenv werent in your path note you can activate multiple versions at the same time including multiple versions of python2 or python3 simultaneously this allows for parallel usage of python2 and python3 and is required with tools like tox for example to set your path to first use your system python and python3 set to 2 7 9 and 3 4 2 in this example but also have python 3 3 6 3 2 and 2 5 available on your path one would first pyenv install the missing versions then set pyenv global system 3 3 6 3 2 2 5 at this point one should be able to find the full executable path to each of these using pyenv which e g pyenv which python2 5 should display pyenv root versions 2 5 bin python2 5 or pyenv which python3 4 should display path to system python3 you can also specify multiple versions in a python version file separated by newlines or any whitespace locating the python installation once pyenv has determined which version of python your application has specified it passes the command along to the corresponding python installation each python version is installed into its own directory under pyenv root versions for example you might have these versions installed pyenv root versions 2 7 8 pyenv root versions 3 4 2 pyenv root versions pypy 2 4 0 as far as pyenv is concerned version names are simply the directories in pyenv root versions managing virtual environments there is a pyenv plugin named pyenv virtualenv which comes with various features to help pyenv users to manage virtual environments created by virtualenv or anaconda because the activate script of those virtual environments are relying on mutating path variable of users interactive shell it will intercept pyenvs shim style command execution hooks wed recommend to install pyenv virtualenv as well if you have some plan to play with those virtual environments installation if youre on mac os x consider installing with homebrew the automatic installer visit my other project https github com pyenv pyenv installer basic github checkout this will get you going with the latest version of pyenv and make it easy to fork and contribute any changes back upstream check out pyenv where you want it installed a good place to choose is home pyenv but you can install it somewhere else git clone https github com pyenv pyenv git pyenv define environment variable pyenv root to point to the path where pyenv repo is cloned and add pyenv root bin to your path for access to the pyenv command line utility sh echo export pyenv root home pyenv bash profile echo export path pyenv root bin path bash profile zsh note modify your zshenv file instead of bash profile ubuntu and fedora note modify your bashrc file instead of bash profile proxy note if you use a proxy export http proxy and https proxy too add pyenv init to your shell to enable shims and autocompletion please make sure eval pyenv init is placed toward the end of the shell configuration file since it manipulates path during the initialization sh echo e if command v pyenv 1 dev null 2 1 then\n eval pyenv init \nfi bash profile zsh note modify your zshenv file instead of bash profile ubuntu and fedora note modify your bashrc file instead of bash profile general warning there are some systems where the bash env variable is configured to point to bashrc on such systems you should almost certainly put the abovementioned line eval pyenv init into bash profile and not into bashrc otherwise you may observe strange behaviour such as pyenv getting into an infinite loop see 264 for details restart your shell so the path changes take effect you can now begin using pyenv sh exec shell install python versions into pyenv root versions for example to download and install python 2 7 8 run sh pyenv install 2 7 8 note if you need to pass configure option to build please use configure opts environment variable note if you want to use proxy to download please use http proxy and https proxy environment variable note if you are having trouble installing a python version please visit the wiki page about common build problems upgrading if youve installed pyenv using the instructions above you can upgrade your installation at any time using git to upgrade to the latest development version of pyenv use git pull sh cd pyenv root git pull to upgrade to a specific release of pyenv check out the corresponding tag sh cd pyenv root git fetch git tag v0 1 0 git checkout v0 1 0 uninstalling pyenv the simplicity of pyenv makes it easy to temporarily disable it or uninstall from the system to disable pyenv managing your python versions simply remove the pyenv init line from your shell startup configuration this will remove pyenv shims directory from path and future invocations like python will execute the system python version as before pyenv pyenv will still be accessible on the command line but your python apps wont be affected by version switching to completely uninstall pyenv perform step 1 and then remove its root directory this will delete all python versions that were installed under pyenv root versions directory sh rm rf pyenv root if youve installed pyenv using a package manager as a final step perform the pyenv package removal for instance for homebrew brew uninstall pyenv homebrew on mac os x you can also install pyenv using the homebrew package manager for mac os x brew update brew install pyenv to upgrade pyenv in the future use upgrade instead of install then follow the rest of the post installation steps under basic github checkout above starting with 3 add pyenv init to your shell to enable shims and autocompletion advanced configuration skip this section unless you must know what every line in your shell profile is doing pyenv init is the only command that crosses the line of loading extra commands into your shell coming from rvm some of you might be opposed to this idea heres what pyenv init actually does sets up your shims path this is the only requirement for pyenv to function properly you can do this by hand by prepending pyenv root shims to your path installs autocompletion this is entirely optional but pretty useful sourcing pyenv root completions pyenv bash will set that up there is also a pyenv root completions pyenv zsh for zsh users rehashes shims from time to time youll need to rebuild your shim files doing this on init makes sure everything is up to date you can always run pyenv rehash manually installs the sh dispatcher this bit is also optional but allows pyenv and plugins to change variables in your current shell making commands like pyenv shell possible the sh dispatcher doesnt do anything crazy like override cd or hack your shell prompt but if for some reason you need pyenv to be a real script rather than a shell function you can safely skip it to see exactly what happens under the hood for yourself run pyenv init uninstalling python versions as time goes on you will accumulate python versions in your pyenv root versions directory to remove old python versions pyenv uninstall command to automate the removal process alternatively simply rm rf the directory of the version you want to remove you can find the directory of a particular python version with the pyenv prefix command e g pyenv prefix 2 6 8 command reference see commands md environment variables you can affect how pyenv operates with the following settings name default description pyenv version specifies the python version to be used also see pyenv shell pyenv root pyenv defines the directory under which python versions and shims reside also see pyenv root pyenv debug outputs debug information also as pyenv debug subcommand pyenv hook path see wiki colon separated list of paths searched for pyenv hooks pyenv dir pwd directory to start searching for python version files python build aria2 opts used to pass additional parameters to aria2 if aria2c binary is available on path pyenv use aria2c instead of curl or wget to download the python source code if you have an unstable internet connection you can use this variable to instruct aria2 to accelerate the download in most cases you will only need to use x 10 k 1m as value to python build aria2 opts environment variable development the pyenv source code is hosted on github its clean modular and easy to understand even if youre not a shell hacker tests are executed using bats bats test bats test file bats please feel free to submit pull requests and file bugs on the issue tracker version history see changelog md license the mit license