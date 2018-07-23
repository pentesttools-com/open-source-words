prezto — instantly awesome zsh prezto is the configuration framework for zsh it enriches the command line interface environment with sane defaults aliases functions auto completion and prompt themes installation prezto will work with any recent release of zsh but the minimum required version is 4 3 11 launch zsh console zsh clone the repository console git clone recursive https github com sorin ionescu prezto git zdotdir home zprezto create a new zsh configuration by copying the zsh configuration files provided sh setopt extended glob for rcfile in zdotdir home zprezto runcoms readme md n do ln s rcfile zdotdir home rcfile t done note if you already have any of the given config files ln will error in simple cases you can add source zdotdir home zprezto init zsh to the bottom of your zshrc to load prezto but keep your config intact for more complicated setups it is recommended that you back up your original configs and replace them with the provided prezto runcoms set zsh as your default shell console chsh s bin zsh open a new zsh terminal window or tab troubleshooting if you are not able to find certain commands after switching to prezto modify the path variable in zprofile then open a new zsh terminal window or tab updating run zprezto update to automatically check if there is an update to zprezto if there are no file conflicts zprezto and its submodules will be automatically updated if there are conflicts you will instructed to go into the zpreztodir directory and resolve them yourself to pull the latest changes and update submodules manually console cd zpreztodir git pull git submodule update init recursive usage prezto has many features disabled by default read the source code and accompanying readme files to learn of what is available modules browse modules to see what is available load the modules you need in zpreztorc then open a new zsh terminal window or tab themes for a list of themes type prompt l to preview a theme type prompt p name load the theme you like in zpreztorc then open a new zsh terminal window or tab external modules by default modules will be loaded from modules and contrib additional module directories can be added to the prezto load pmodule dirs setting in zpreztorc note that module names need to be unique or they will cause an error when loading console zstyle prezto load pmodule dirs home zprezto contrib customization the project is managed via git it is highly recommended that you fork this project so that you can commit your changes and push them to github to not lose them if you do not know how to use git follow this tutorial and bookmark this reference resources the zsh reference card and the zsh lovers man page are indispensable license this project is licensed under the mit license