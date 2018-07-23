showdown is a javascript markdown to html converter based on the original works by john gruber showdown can be used client side in the browser or server side with nodejs live demo check a live demo here http demo showdownjs com who uses showdown or a fork googlecloudplatform ghost meteor stackexchange forked as pagedown docular and some others donate as you know showdownjs is a free library and it will remain free forever however maintaining and improving the library costs time and money if you like our work and find our library useful please donate through pledgie or directly through paypal your contribution will be greatly appreciated and help us continue to develop this awesome library installation download tarball you can download the latest release tarball directly from releases bower bower install showdown npm server side npm install showdown nuget package pm install package showdownjs the nuget packages can be found here cdn you can also use one of several cdns available github cdn https cdn rawgit com showdownjs showdown version tag dist showdown min js cdnjs https cdnjs cloudflare com ajax libs showdown version tag showdown min js browser compatibility showdown has been tested successfully with firefox 1 5 and 2 0 chrome 12 0 internet explorer 6 and 7 safari 2 0 4 opera 8 54 and 9 10 netscape 8 1 2 konqueror 3 5 4 in theory showdown will work in any browser that supports ecma 262 3rd edition javascript 1 5 the converter itself might even work in things that arent web browsers like acrobat no promises node compatibility showdown has been tested with node 0 8 and 0 10 however it should work with previous versions such as node 0 6 legacy version if youre looking for showdown v 1 0 0 you can find it in the legacy branch changelog you can check the full changelog extended documentation check our wiki pages for examples and a more in depth documentation quick example node js var showdown require showdown converter new showdown converter text hello markdown html converter makehtml text browser js var converter new showdown converter text hello markdown html converter makehtml text output both examples should output html h1 id hellomarkdown hello markdown h1 options you can change some of showdowns default behavior through options setting options options can be set globally setting a global option affects all instances of showdown js showdown setoption optionkey value locally setting a local option only affects the specified converter object local options can be set through the constructor js var converter new showdown converter optionkey value through the setoption method js var converter new showdown converter converter setoption optionkey value getting an option showdown provides 2 methods both local and global to retrieve previous set options getoption js global var myoption showdown getoption optionkey local var myoption converter getoption optionkey getoptions js global var showdownglobaloptions showdown getoptions local var thisconverterspecificoptions converter getoptions retrieve the default options you can get showdowns default options with js var defaultoptions showdown getdefaultoptions valid options omitextrawlincodeblocks boolean default false omit the trailing newline in a code block ex this html code pre var foo bar pre code becomes this html code pre var foo bar pre code noheaderid boolean default false disable the automatic generation of header ids setting to true overrides prefixheaderid customizedheaderid boolean default false use text in curly braces as header id since v1 7 0 example sample header real id will use real id as id ghcompatibleheaderid boolean default false generate header ids compatible with github style spaces are replaced with dashes and a bunch of non alphanumeric chars are removed since v1 5 5 prefixheaderid string boolean default false add a prefix to the generated header ids passing a string will prefix that string to the header id setting to true will add a generic section prefix rawprefixheaderid boolean default false setting this option to true will prevent showdown from modifying the prefix this might result in malformed ids if for instance the char is used in the prefix has no effect if prefixheaderid is set to false since v 1 7 3 rawheaderid boolean default false remove only spaces and from generated header ids including prefixes replacing them with dashes warning this might result in malformed ids since v1 7 3 parseimgdimensions boolean default false enable support for setting image dimensions from within markdown syntax examples foo foo jpg 100x80 simple assumes units are in px bar bar jpg 100x sets the height to auto baz baz jpg 80 x5em image with width of 80 and height of 5em headerlevelstart integer default 1 set the header starting level for instance setting this to 3 means that md foo will be parsed as html h3 foo h3 simplifiedautolink boolean default false turning this option on will enable automatic linking to urls this means that md some text www google com will be parsed as html p some text a href www google com www google com a excludetrailingpunctuationfromurls boolean default false this option excludes trailing punctuation from autolinking urls punctuation excluded only applies if simplifiedautolink option is set to true md check this link www google com will be parsed as html p check this link a href www google com www google com a p literalmidwordunderscores boolean default false turning this on will stop showdown from interpreting underscores in the middle of words as em and strong and instead treat them as literal underscores example md some text with underscores in middle will be parsed as html p some text with underscores in middle p literalmidwordasterisks boolean default false turning this on will stop showdown from interpreting asterisks in the middle of words as em and strong and instead treat them as literal asterisks example md some text with underscores in middle will be parsed as html p some text with underscores in middle p strikethrough boolean default false enable support for strikethrough syntax strikethrough as del strikethrough del tables boolean default false enable support for tables syntax example md h1 h2 h3 100 a 1 b 2 foo bar baz see the wiki for more info tablesheaderid boolean default false if enabled adds an id property to table headers tags ghcodeblocks boolean default true enable support for gfm code block style tasklists boolean default false enable support for gfm tasklists example md x this task is done this is still pending smoothlivepreview boolean default false prevents weird effects in live previews due to incomplete input smartindentationfix boolean default false tries to smartly fix indentation problems related to es6 template strings in the midst of indented code disableforced4spacesindentedsublists boolean default false disables the requirement of indenting sublists by 4 spaces for them to be nested effectively reverting to the old behavior where 2 or 3 spaces were enough since v1 5 0 simplelinebreaks boolean default false parses line breaks as like github does without needing 2 spaces at the end of the line since v1 5 1 md a line wrapped in two turns into html p a line br wrapped in two p requirespacebeforeheadingtext boolean default false makes adding a space between and the header text mandatory since v1 5 3 ghmentions boolean default false enables github mentions which link to the username mentioned since v1 6 0 ghmentionslink string default https github com u changes the link generated by mentions showdown will replace u with the username only applies if ghmentions option is enabled example tivie with ghmentionsoption set to mysite com u profile will result in a href mysite com tivie profile tivie a encodeemails boolean default true enable e mail addresses encoding through the use of character entities transforming ascii e mail addresses into its equivalent decimal entities since v1 6 1 note prior to version 1 6 1 emails would always be obfuscated through dec and hex encoding openlinksinnewwindow boolean default false open all links in new windows by adding the attribute target blank to a tags since v1 7 0 backslashescapeshtmltags boolean default false support for html tag escaping ex \ div foo\ div since v1 7 2 emoji boolean default false enable emoji support ex this is a smile emoji for more info on available emojis see https github com showdownjs showdown wiki emojis since v 1 8 0 underline boolean default false experimental feature enable support for underline syntax is double or triple underscores ex underlined word with this option enabled underscores are no longer parses into em and strong completehtmldocument boolean default false outputs a complete html document including html head and body tags instead of an html fragment since v 1 8 5 metadata boolean default false enable support for document metadata defined at the top of the document between ««« and »»» or between and since v 1 8 5 js var conv new showdown converter metadata true var html conv makehtml somemd var metadata conv getmetadata returns an object with the document metadata splitadjacentblockquotes boolean default false split adjacent blockquote blocks since v 1 8 6 note please note that until version 1 6 0 all of these options are disabled by default in the cli tool flavors you can also use flavors or presets to set the correct options automatically so that showdown behaves like popular markdown flavors currently the following flavors are available original original markdown flavor as in john grubers spec vanilla showdown base flavor as from v1 3 1 github gfm github flavored markdown global javascript showdown setflavor github instance javascript converter setflavor github cli tool showdown also comes bundled with a command line interface tool you can check the cli wiki page for more info integration with angularjs showdownjs project also provides seamlessly integration with angularjs via a plugin please visit https github com showdownjs ngshowdown for more information integration with typescript if youre using typescript you maybe want to use the types from definitelytyped integration with systemjs jspm integration with systemjs can be obtained via the third party system md plugin xss vulnerability showdown doesnt sanitize the input this is by design since markdown relies on it to allow certain features to be correctly parsed into html this however means xss injection is quite possible please refer to the wiki article markdowns xss vulnerability and how to mitigate it for more information extensions showdown allows additional functionality to be loaded via extensions you can find a list of known showdown extensions here you can also find a boilerplate to create your own extensions in this repository client side extension usage js var converter new showdown converter extensions twitter server side extension usage js var showdown require showdown myextension require myextension converter new showdown converter extensions myextension tests a suite of tests is available which require node js once node is installed run the following command from the project root to install the dependencies npm install once installed the tests can be run from the project root using npm test new test cases can easily be added create a markdown file ending in md which contains the markdown to test create a html file of the exact same name it will automatically be tested when the tests are executed with mocha contributing if you wish to contribute please read the following quick guide want a feature you can request a new feature by submitting an issue if you would like to implement a new feature feel free to issue a pull request pull requests prs prs are awesome however before you submit your pull request consider the following guidelines search github for an open or closed pull request that relates to your submission you dont want to duplicate effort when issuing prs that change code make your changes in a new git branch based on master bash git checkout b my fix branch master documentation i e readme md changes can be made directly against master run the full test suite before submitting and make sure all tests pass obviously p try to follow our coding style rules breaking them prevents the pr to pass the tests refrain from fixing multiple issues in the same pull request its preferable to open multiple small prs instead of one hard to review big one if the pr introduces a new feature or fixes an issue please add the appropriate test case we use commit notes to generate the changelog its extremely helpful if your commit messages adhere to the angularjs git commit guidelines if we suggest changes then make the required updates re run the angular test suite to ensure tests are still passing rebase your branch and force push to your github repository this will update your pull request bash git rebase master i git push origin my fix branch f after your pull request is merged you can safely delete your branch if you have time to contribute to this project we feel obliged that you get credit for it these rules enable us to review your pr faster and will give you appropriate credit in your github profile we thank you in advance for your contribution joining the team were looking for members to help maintaining showdown please see this issue to express interest or comment on this note credits full credit list at https github com showdownjs showdown blob master credits md showdown is powered by