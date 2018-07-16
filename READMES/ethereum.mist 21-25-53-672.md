mist browserbeta the mist browser is the tool of choice to browse and use ðapps for the mist api see mistapi md this repository is the electron host for the meteor based wallet dapp release candidate 0 11 0 up for testing feedback thread for 0 11 0 rc https github com ethereum mist issues 3979 reddit post https www reddit com r ethereum comments 8uelv6 mist browser beta and ethereum wallet 0110 preview file checksum sha256 ethereum wallet installer 0 11 0 rc exe f5431a32a419fdd51a379a02806a0d1cf9fa6a80213661aba2e4713731010615 ethereum wallet linux32 0 11 0 rc deb 161f69d2546999363c64b1c85f938469a37afc51719ed48d4f4b02f33fd0206e ethereum wallet linux32 0 11 0 rc zip 9da6da638b3cb851df78fbe5bf65229147e5a43555463da65ef3a31f7cf93034 ethereum wallet linux64 0 11 0 rc deb dd32ee3c36e4dc2ef04a118b4a6a3402097d722947b09fac9f8914672df39642 ethereum wallet linux64 0 11 0 rc zip e515eb3ae7db6c9eee89892ed3fafa221bc8a0caad5c76305e08ffd950b31764 ethereum wallet macosx 0 11 0 rc dmg 408f50aca5049aeace30ca2d6357d8dd11868ab2ab9828d4ee7286b9eeff1081 ethereum wallet win32 0 11 0 rc zip c605ed12070d185d387f6d649e35659d003a029ad2a7c0c5e9903b488ec1e676 ethereum wallet win64 0 11 0 rc zip 199af74e86c627fd0bc09027c01725869c0beb1eb4d85bfc7d9b9a3979a17b07 mist installer 0 11 0 rc exe e11569e77abbc7555cd570d427c007ce6ab35fcdf299d4094fab55de10a6f101 mist linux32 0 11 0 rc deb 29045433ac1020447e1977949deee05ae8eaef7c157ec6d7766d4eefccb48b9c mist linux32 0 11 0 rc zip 9efccc68184eaa250a5dcce8515ffca59c6ce092913ac0ca7c8bb3a9c7db164c mist linux64 0 11 0 rc deb e29bc4de4c3090b07130b3d96b9b5aae7c216fb6d51900330440535ece7681b5 mist linux64 0 11 0 rc zip 9137183d774ba57d071d3d0b9dcd566d878ace10b745c5b689c3fa2a0997f457 mist macosx 0 11 0 rc dmg 7f8ce72b9693f03a47674ea616ae9e22f67582d27c1265fbc4746d9584a7eab8 mist win32 0 11 0 rc zip f208bb6e00fc0f69ad36a028dc4278507fc5810def2415268b1a302e4e433a79 mist win64 0 11 0 rc zip 632a1aaa24cfd92507be05b443ed4c4a2b8f618d4deb6324824d6cf06cdd50d9 help and troubleshooting in order to get help regarding mist or ethereum wallet please check the mist troubleshooting guide go to our gitter channel to connect with the community for instant help search for similar issues and potential help or create a new issue and provide as much information as you can to recreate your problem how to contribute contributions via pull requests are welcome you can see where to help looking for issues with the enhancement or bug labels we can help guide you towards the solution you can also help by responding to issues sign up on codetriage and itll send you gentle notifications with a configurable frequency it is a nice way to help while learning installation if you want to install the app from a pre built version on the release page you can simply run the executable after download for updating simply download the new version and copy it over the old one keep a backup of the old one if you want to be sure linux zip installs in order to install from zip files please install libgconf2 4 first bash apt get install libgconf2 4 config folder the data folder for mist depends on your operating system windows appdata \mist macos library application\ support mist linux config mist development for development a meteor server assists with live reload and css injection once a mist version is released the meteor frontend part is bundled using the meteor build client npm package to create pure static files dependencies to run mist in development you need node js v7 x use the preferred installation method for your os meteor javascript app framework yarn package manager install the latter ones via bash curl https install meteor com sh curl o l https yarnpkg com install sh bash initialization now youre ready to initialize mist for development bash git clone https github com ethereum mist git cd mist yarn to update mist in the future run bash cd mist git pull yarn run mist for development we start the interface with a meteor server for auto reload etc start the interface in a separate terminal window bash yarn dev meteor in the original window you can then start mist with bash cd mist yarn dev electron note client binaries e g geth specified in clientbinaries json will be checked during every startup and downloaded if out of date binaries are stored in the config folder note use help to display available options e g loglevel debug or trace for verbose output run the wallet start the wallet app for development in a separate terminal window bash yarn dev meteor in another terminal bash cd my path meteor dapp wallet app meteor port 3050 in the original window you can then start mist using wallet mode bash cd mist yarn dev electron mode wallet connect your own node this is useful if you are already running your own node or would like to connect with a private or development network bash yarn dev electron rpc path to geth ipc passing options to geth you can pass command line options directly to geth by prefixing them with node in the command line invocation bash yarn dev electron mode mist node rpcport 19343 node networkid 2 the rpc mist option is a special case if you set this to an ipc socket file path then the ipcpath option automatically gets set i e bash yarn dev electron rpc path to geth ipc is the same as doing bash yarn dev electron rpc my geth ipc node ipcpath path to geth ipc creating a local private net if you would like to quickly set up a local private network on your computer run bash geth dev look for the ipc path in the resulting geth output then start mist with bash yarn dev electron rpc path to geth ipc deployment our build system relies on gulp and electron builder dependencies cross platform builds require additional electron builder dependencies macos bash brew install rpm windows bash brew install wine without x11 mono makensis linux bash brew install gnu tar libicns graphicsmagick xz generate packages to generate the binaries for mist run bash gulp to generate the ethereum wallet this will pack the one ðapp from https github com ethereum meteor dapp wallet bash gulp wallet the generated binaries will be under dist mist release or dist wallet release options platform to build binaries for specific platforms default all available use the following flags bash gulp mac mac gulp linux linux gulp win windows walletsource with the walletsource you can specify the wallet branch to use default is master gulp wallet walletsource local options are master any meteor dapp wallet branch local will try to build the wallet from mist meteor dapp wallet app note applicable only when combined with wallet skiptasks when building a binary you can optionally skip some tasks — generally for testing purposes bash gulp mac skiptasks bundling interface release dist checksums spits out the md5 checksums of the distributables it expects installer zip files to be in the generated folders e g dist mist release bash gulp checksums wallet cutting a release install release globally bash yarn global add release create a git tag and a github release bash release major minor patch a generated release draft will open in the default browser edit the information and add assets as necessary testing tests run using spectron a webdriver io runner built for electron first make sure to build mist with bash gulp then run the tests bash gulp test note integration tests are not yet supported on windows