mackup keep your application settings in sync table of content quickstart usage what does it do bullsh t what does it really do to my files supported storages supported applications can you support application x why did you do this what platforms are supported whats up with the weird name where can i find more information quickstart if you have dropbox installed and want to use it to save your config files thats super easy on os x if you want an easy install you can install homebrew and do bash install mackup brew install mackup launch it and back up your files mackup backup if not running os x or you dont like homebrew you can use pip note the below command will check if a previous version of mackup is already installed on your system if this is the case it will be upgraded to the latest version bash install mackup with pip pip install upgrade mackup launch it and back up your files mackup backup youre all set and constantly backed up from now on next on any new workstation do bash install mackup brew install mackup launch it and restore your files mackup restore done you can find more detailed instructions in install md usage mackup backup backup your application settings mackup restore restore your application settings on a newly installed workstation mackup uninstall copy back any synced config file to its original place mackup list display the list of applications supported by mackup mackup h get some help obviously what does it do back ups your application settings in a safe directory e g dropbox syncs your application settings among all your workstations restores your configuration on any fresh install in one command line by only tracking pure configuration files it keeps the crap out of your freshly new installed workstation no cache temporary and locally specific files are transfered mackup makes setting up the environment easy and simple saving time for your family great ideas and all the cool stuff you like bullsh t what does it really do to my files lets take git as an example your settings for git are saved in your home folder in the gitconfig file backup if you have dropbox these things happen when you launch mackup backup cp gitconfig dropbox mackup gitconfig rm gitconfig ln s dropbox mackup gitconfig gitconfig now your git config is always backed up and up to date on all your workstations restore when you launch mackup restore heres what its really doing ln s dropbox mackup gitconfig gitconfig thats it you got your git config setup on your new workstation mackup does the same for any supported application uninstall you can revert all your files to their original state bash just run this mackup uninstall this will remove the symlinks and copy back the files from the mackup folder in dropbox to their original places in your home the mackup folder and the files in it stay put so that any other computer also running mackup is unaffected supported storages dropbox google drive copy icloud box anything able to sync a folder e g git see the readme file in the doc directory for more info supported applications 1password 4 ack adium adobe camera raw adobe illustrator cc adobe photoshop cc adobe photoshop lightroom cc airmail amethyst amphetamine ancient domains of mystery android studio ansible appcleaner appcode apptivate arara aria2c arm artistic style asciinema aspell atlantis atom audacious auskey autokey awareness aws command line interface bartender bash it bash bbedit beatport pro bettersnaptool bettertouchtool bibdesk billings pro server admin bitchx blackfire blender boto boxer brackets bundler byobu caffeine capture one cartographica cerebro charles chef chicken clementine clion clipmenu clipy cloudapp coda 2 colloquy colorschemer studio 2 colorsync composer concentrate conky consular controlplane copyq cord coteditor ctags cyberduck daisydisk dash day o dbvisualizer deal alert default folder x devils pie 2 devils pie dig divvy docker dolphin double commander doxie droplr dropzone 3 drush editorconfig electrum emacs enjoyable environmental station alpha exercism expandrive factorio fantastical fasd fastlane feeds filezilla fish fisherman flexget flux fontconfig fontexplorer x forge forklift 2 franz gas mask gdb gear player geektool ghci ghostwriter git hooks git gitbox gitkraken gitup gmail notifr gmvault gnome ssh tunnel manager gnupg note includes private keys go2shell gogland goshare gradle grandtotal 3 hammerspoon handbrake hands off hazel hero lab heroku hexchat hexels homebridge houdini htop httpie hub hyper app hyperdock hyperswitch i2cssh i3 i3wm ideavim insomnia intellijidea ipython irssi istat menus 5 iterm2 itermocil janus jitouch jrnl jshint julia jumpcut jupyter kaleidoscope karabiner elements karabiner kdenlive keepassx keepingyouawake keka keybase keyboard maestro keymo keyremap4macbook kwm latexit launchbar libreoffice liftoff light table limechat liquid prompt littlesnitch livestreamer lollypop luftrausers macdive macdown macosx macvim magic launch magicprefs maid mailmate mailplane marked 2 matlab maven max menumeters mercurial mercurymover messages micro microsoft azure cli microsoft remote desktop monodevelop moom mou mpd mplayerx mps youtube mpv musicbrainz picard myrepos mysql workbench mysql name mangler nano navicat ncmpcpp neovim nethack newsbeuter ngrok nomacs npm nvalt nvpy oh my fish oh my zsh omnifocus omnigraffle openbox openemu openssh paintbrush pandoc pass pastebot path finder pear pentadactyl perl phoenix phpstorm pidgin pip poedit pokerstars popclip popcorn time postgresql postico pow prezto processing proxychains ng proxychains punto switcher pycharm pypi pyradio querious quicksilver qutebrowser r rails redshift scheduler redshift rhythmbox rime robomongo royal tsx rstudio rtorrent rubocop ruby version ruby rubymine s3cmd sabnzbd sbcl sbt scenario screen screenhero scrivener scroll reverser securecrt seil selfcontrol sequel pro shiftit shimo showyedge shsh blobs shuttle sizeup sketch skim skitch slate slic3r slogger smartgit smooth mouse soulver sourcetree spacemacs spark spectacle spectrwm splice spotify notifications spotify stata stay sublime text subversion superduper surge swinsian t taskpaper taskwarrior teamocil telegram for macos terminal terminator textexpander textmate textual tig tint2 tinyfugue tmux tmuxp tmuxinator todo txt cli totalspaces2 tower transmission transmit tunnelblick tvnamer twitterrific typinator utorrent ventrilo versions vim vimperator viscosity visual studio code insiders visual studio code vlc wakatime webstorm wget whatsapp web wireshark 2 witch wordpress wp cli workrave x11 xamarin studio xbindkeys xchat xcode xemacs xld xtrafinder yummy ftp z zathura zsh übersicht itunes applescripts can you support application x we can with your help personalization configuration have an application that shouldnt be generally supported but that you use or a cool file you want to sync use a mackup cfg to sync a single file e g gitignore create a mackup directory to sync an application or any file or directory why did you do this yesterday i had a talk with zach zaro complaining about the pain it is to reconfigure our macbook each time we get a new one or install from scratch thats a talk we have already had months ago i change my workstation every x months each time i either lose my apps configurations or i just waste a bunch of hours getting setup like i was on my old box i also spend a lot of time reconfiguring the same stuff again on all my workstations home work boring some people tried to solve the problem on the application layer like githubs boxen but it solves a different problem from my point of view i dont spend a lot of time installing or downloading stuff i spend time configuring it for years ive used a personal shell script that was copying known config files into subversion git or dropbox and linked them into my home but i felt a lot of us had the same problem making a more generic tool could help others and i could get help from others to support more apps in the tool so here comes mackup the little tool that will sync all your application configs to dropbox or google drive or anything and its gpl of course what platforms are supported os x gnu linux whats up with the weird name mackup is just a portmanteau of mac and backup it is simple short and easy to remember and it corresponds with the whole idea of mackup the simpler – the better and i suck at naming stuff but who doesnt where can i find more information in the doc directory