signale 👋 hackable console logger description hackable and configurable to the core signale can be used for logging purposes status reporting as well as for handling the output rendering process of other node modules and applications read this document in 简体中文 visit the contributing guidelines to learn more on how to translate this document into more languages come over to gitter or twitter to share your thoughts on the project highlights 16 out of the box loggers hackable to the core clean and beautiful output integrated timers custom pluggable loggers interactive and regular modes filename date and timestamp support scoped loggers and timers string interpolation support multiple configurable writable streams simple and minimal syntax globally configurable through package json overridable configuration per file and logger contents description highlights install usage configuration api development related team license install bash npm install signale usage default loggers import signale and start using any of the default loggers view all of the available loggers await complete error debug fatal fav info note pause pending star start success warn watch log js const signale require signale signale success operation successful signale debug hello from l59 signale pending write release notes for s 1 2 0 signale fatal new error unable to acquire lock signale watch recursively watching build directory signale complete prefix task message fix issue 59 suffix klauscfhq custom loggers to create a custom logger define an options object yielding a types field with the logger data and pass it as argument to a new signale instance js const signale require signale const options disabled false interactive false stream process stdout scope custom types remind badge color yellow label reminder santa badge 🎅 color red label santa const custom new signale options custom remind improve documentation custom santa hoho you have an unused variable on l45 here is an example where we override the default error and success loggers js const signale require signale const options types error badge label fatal error success badge label huge success const signale new signale signale error default error log signale success default success log const custom new signale options custom error custom error log custom success custom success log the options object can hold any of the following attributes disabled interactive stream scope and types disabled type boolean default false disables the logging functionality of all loggers belonging to the created instance interactive type boolean default false switches all loggers belonging to the created instance into the interactive mode stream type writable stream or array of writable streams default process stdout destination to which the data is written can be a single valid writable stream or an array holding multiple valid writable streams scope type string or array of strings name of the scope the logger is reporting from types type object holds the configuration of the custom and default loggers badge type string the icon corresponding to the logger label type string the label used to identify the type of the logger color type string the color of the label can be any of the foreground colors supported by chalk scoped loggers to create a scoped logger from scratch define the scope field inside the options object and pass it as argument to a new signale instance js const signale require signale const options scope global scope const global new signale options global success successful operation to create a scoped logger based on an already existing one use the scope function which will return a new signale instance inheriting all custom loggers timers streams configuration interactive mode disabled statuses from the initial one js const signale require signale const global signale scope global scope global success hello from the global scope function foo const outer global scope outer scope outer success hello from the outer scope settimeout const inner outer scope inner scope inner success hello from the inner scope 500 foo interactive loggers to initialize an interactive logger create a new signale instance with the interactive attribute set to true while into the interactive mode previously logged messages originating from an interactive logger will be overridden only by new ones originating from the same or a different interactive logger note that regular messages originating from regular loggers are not overridden by the interactive ones js const signale require signale const interactive new signale interactive true scope interactive interactive await d 4 process a 1 settimeout interactive success d 4 process a 2 settimeout interactive await d 4 process b 3 settimeout interactive error d 4 process b 4 settimeout 1000 1000 1000 1000 writable streams by default all signale instances log their messages to the process stdout stream this can be modified to match your own preference through the stream property where you can define a single or multiple valid writable streams which will be used by all logger types to log your data additionally it is possible to define one or more writable streams exclusively for a specific logger type thus write data independently from the rest logger types js const signale require signale const options stream process stderr all loggers will now write to process stderr types error only error will write to both process stdout process stderr stream process stdout process stderr const signale new signale options signale success message will appear on process stderr signale error message will appear on both process stdout process stderr timers timer are managed by the time and timeend functions a unique label can be used to identify a timer on initialization though if none is provided the timer will be assigned one automatically in addition calling the timeend function without a specified label will have as effect the termination of the most recently initialized timer that was created without providing a label js const signale require signale signale time test signale time signale time settimeout signale timeend signale timeend signale timeend test 500 configuration global to enable global configuration define the options under the signale namespace in your package json the following illustrates all the available options with their respective default values json signale coloredinterpolation false displayscope true displaybadge true displaydate false displayfilename false displaylabel true displaytimestamp false underlinelabel true underlinemessage false underlineprefix false underlinesuffix false uppercaselabel false view all of the available options in detail coloredinterpolation type boolean default false display the arguments which replace the placeholder tokens on string interpolation colored displayscope type boolean default true display the scope name of the logger displaybadge type boolean default true display the badge of the logger displaydate type boolean default false display the current local date in yyyy mm dd format displayfilename type boolean default false display the name of the file that the logger is reporting from displaylabel type boolean default true display the label of the logger displaytimestamp type boolean default false display the current local time in hh mm ss format underlinelabel type boolean default true underline the logger label underlinemessage type boolean default false underline the logger message underlineprefix type boolean default false underline the logger prefix underlinesuffix type boolean default false underline the logger suffix uppercaselabel type boolean default false display the label of the logger in uppercase local to enable local configuration call the config function on your signale instance local configurations will always override any pre existing configuration inherited from package json in the following example loggers in the foo js file will run under their own configuration overriding the package json one js foo js const signale require signale overrides any existing package json config signale config displayfilename true displaytimestamp true displaydate false signale success hello from the global scope also scoped loggers can have their own independent configuration overriding the one inherited by the parent instance or package json js foo js const signale require signale signale config displayfilename true displaytimestamp true displaydate false signale success hello from the global scope function foo foologger inherits the config of signale const foologger signale scope foo scope overrides both signale and package json configs foologger config displayfilename true displaytimestamp false displaydate true foologger success hello from the local scope foo api signale logger message message messageobj errorobj logger type function can be any default or custom logger message type string can be one or more comma delimited strings js const signale require signale signale success successful operation ✔ success successful operation signale success successful operation ✔ success successful operation signale success successful s operation ✔ success successful operation errorobj type error object can be any error object js const signale require signale signale error new error unsuccessful operation ✖ error error unsuccessful operation at module compile module js 660 30 at object module extensions js module js 671 10 messageobj type object can be an object holding the prefix message and suffix attributes with prefix and suffix always prepended and appended respectively to the logged message js const signale require signale signale complete prefix task message fix issue 59 suffix klauscfhq task ☒ complete fix issue 59 klauscfhq signale complete prefix task message fix issue d 59 suffix klauscfhq task ☒ complete fix issue 59 klauscfhq signale scope name name defines the scope name of the logger name type string can be one or more comma delimited strings js const signale require signale const foo signale scope foo const foobar signale scope foo bar foo success foo foo › ✔ success foo foobar success foo bar foo bar › ✔ success foo bar signale unscope clears the scope name of the logger js const signale require signale const foo signale scope foo foo success foo foo › ✔ success foo foo unscope foo success foo ✔ success foo signale config settingsobj sets the configuration of an instance overriding any existing global or local configuration settingsobj type object can hold any of the documented options js foo js const signale require signale signale config displayfilename true displaytimestamp true displaydate true signale success successful operations 2018 5 15 11 12 38 foo js › ✔ success successful operations signale time label return type string sets a timers and accepts an optional label if none provided the timer will receive a unique label automatically returns a string corresponding to the timer label label type string label corresponding to the timer each timer must have its own unique label js const signale require signale signale time ▶ timer 0 initialized timer signale time ▶ timer 1 initialized timer signale time label ▶ label initialized timer signale timeend label return type object deactivates the timer to which the given label corresponds if no label is provided the most recent timer that was created without providing a label will be deactivated returns an object label span holding the timer label and the total running time label type string label corresponding to the timer each timer has its own unique label js const signale require signale signale time ▶ timer 0 initialized timer signale time ▶ timer 1 initialized timer signale time label ▶ label initialized timer signale timeend ◼ timer 1 timer run for 2ms signale timeend ◼ timer 0 timer run for 2ms signale timeend label ◼ label timer run for 2ms signale disable disables the logging functionality of all loggers belonging to a specific instance js const signale require signale signale success foo ✔ success foo signale disable signale success foo signale enable enables the logging functionality of all loggers belonging to a specific instance js const signale require signale signale disable signale success foo signale enable signale success foo ✔ success foo development for more info on how to contribute to the project please read the contributing guidelines fork the repository and clone it to your machine navigate to your local fork cd signale install the project dependencies npm install or yarn install lint code for errors npm test or yarn test related chalk terminal string styling done right figures unicode symbols team klaus sinani klauscfhq license mit