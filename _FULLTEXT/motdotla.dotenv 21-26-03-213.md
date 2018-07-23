dotenv dotenv is a zero dependency module that loads environment variables from a env file into process env storing configuration in the environment separate from code is based on the twelve factor app methodology install bash with npm npm install dotenv or with yarn yarn add dotenv usage as early as possible in your application require and configure dotenv javascript require dotenv config create a env file in the root directory of your project add environment specific variables on new lines in the form of name value for example dosini db host localhost db user root db pass s1mpl3 thats it process env now has the keys and values you defined in your env file javascript const db require db db connect host process env db host username process env db user password process env db pass preload you can use the require r command line option to preload dotenv by doing this you do not need to require and load dotenv in your application code this is the preferred approach when using import instead of require bash node r dotenv config your script js the configuration options below are supported as command line arguments in the format dotenv config option value bash node r dotenv config your script js dotenv config path custom path to your env vars config alias load config will read your env file parse the contents assign it to process env and return an object with a parsed key containing the loaded content or an error key if it failed js const result dotenv config if result error throw result error console log result parsed you can additionally pass options to config options path default path resolve process cwd env you can specify a custom path if your file containing environment variables is named or located differently js require dotenv config path full custom path to your env vars encoding default utf8 you may specify the encoding of your file containing environment variables using this option js require dotenv config encoding base64 parse the engine which parses the contents of your file containing environment variables is available to use it accepts a string or buffer and will return an object with the parsed keys and values js const dotenv require dotenv const buf buffer from basic basic const config dotenv parse buf will return an object console log typeof config config object basic basic rules the parsing engine currently supports the following rules basic basic becomes basic basic empty lines are skipped lines beginning with are treated as comments empty values become empty strings empty becomes empty single and double quoted values are escaped single quote quoted becomes single quote quoted new lines are expanded if in double quotes multiline new\nline becomes multiline new line inner quotes are maintained think json json foo bar becomes json \ foo\ \ bar\ whitespace is removed from both ends of the value see more on trim foo some value becomes foo some value faq should i commit my env file no we strongly recommend against committing your env file to version control it should only include environment specific values such as database passwords or api keys your production database should have a different password than your development database should i have multiple env files no we strongly recommend against having a main env file and an environment env file like env test your config should vary between deploys and you should not be sharing values between environments in a twelve factor app env vars are granular controls each fully orthogonal to other env vars they are never grouped together as “environments” but instead are independently managed for each deploy this is a model that scales up smoothly as the app naturally expands into more deploys over its lifetime – the twelve factor app what happens to environment variables that were already set we will never modify any environment variables that have already been set in particular if there is a variable in your env file which collides with one that already exists in your environment then that variable will be skipped this behavior allows you to override all env configurations with a machine specific environment although it is not recommended if you want to override process env you can do something like this javascript const fs require fs const dotenv require dotenv const envconfig dotenv parse fs readfilesync env override for var k in envconfig process env k envconfig k can i customize write plugins for dotenv for dotenv 2 x x yes dotenv config now returns an object representing the parsed env file this gives you everything you need to continue setting values on process env for example js var dotenv require dotenv var variableexpansion require dotenv expand const myenv dotenv config variableexpansion myenv what about variable expansion for dotenv 2 x x use dotenv expand for dotenv 1 x x we havent been presented with a compelling use case for expanding variables and believe it leads to env vars that are not fully orthogonal as the twelve factor app outlines 1 2 please open an issue if you have a compelling use case how do i use dotenv with import es2015 and beyond offers modules that allow you to export any top level function class var let or const when you run a module containing an import declaration the modules it imports are loaded first then each module body is executed in a depth first traversal of the dependency graph avoiding cycles by skipping anything already executed – es6 in depth modules you must run dotenv config before referencing any environment variables heres an example of problematic code errorreporter js js import client from best error reporting service export const client new client process env best api key index js js import dotenv from dotenv import errorreporter from errorreporter dotenv config errorreporter client report new error faq example client will not be configured correctly because it was constructed before dotenv config was executed there are at least 3 ways to make this work preload dotenv node require dotenv config index js note you do not need to import dotenv with this approach import dotenv config instead of dotenv note you do not need to call dotenv config and must pass options via the command line with this approach create a separate file that will execute config first as outlined in this comment on 133 contributing guide see contributing md change log see changelog md license see license whos using dotenv heres just a few of many repositories using dotenv jaws node lambda resume cli phant adafruit io node mockbin and many more go well with dotenv heres some projects that expand on dotenv check them out require environment variables dotenv safe envalid lookenv run env dotenv webpack