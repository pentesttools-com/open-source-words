webpack bundle analyzer visualize size of webpack output files with an interactive zoomable treemap install bash npm install save dev webpack bundle analyzer usage as a plugin js const bundleanalyzerplugin require webpack bundle analyzer bundleanalyzerplugin module exports plugins new bundleanalyzerplugin it will create an interactive treemap visualization of the contents of all your bundles this module will help you realize whats really inside your bundle find out what modules make up the most of its size find modules that got there by mistake optimize it and the best thing is it supports minified bundles it parses them to get real size of bundled modules and it also shows their gzipped sizes options for plugin js new bundleanalyzerplugin options object name type description analyzermode one of server static disabled default server in server mode analyzer will start http server to show bundle report in static mode single html file with bundle report will be generated in disabled mode you can use this plugin to just generate webpack stats json file by setting generatestatsfile to true analyzerhost string default 127 0 0 1 host that will be used in server mode to start http server analyzerport number default 8888 port that will be used in server mode to start http server reportfilename string default report html path to bundle report file that will be generated in static mode relative to bundle output directory which is output path in webpack config defaultsizes one of stat parsed gzip default parsed module sizes to show in report by default size definitions section describes what these values mean openanalyzer boolean default true automatically open report in default browser generatestatsfile boolean default false if true webpack stats json file will be generated in bundle output directory statsfilename string default stats json name of webpack stats json file that will be generated if generatestatsfile is true relative to bundle output directory statsoptions null or object default null options for stats tojson method for example you can exclude sources of your modules from stats file with source false option see more options here excludeassets null\ pattern\ pattern where pattern equals to string\ regexp\ function default null patterns that will be used to match against asset names to exclude them from the report if pattern is a string it will be converted to regexp via new regexp str if pattern is a function it should have the following signature assetname string boolean and should return true to exclude matching asset if multiple patterns are provided asset should match at least one of them to be excluded loglevel one of info warn error silent default info used to control how much details the plugin outputs usage as a cli utility you can analyze an existing bundle if you have a webpack stats json file you can generate it using bundleanalyzerplugin with generatestatsfile option set to true or with this simple command bash webpack profile json stats json if youre on windows and using powershell you can generate the stats file with this command to avoid bom issues webpack profile json out file stats json encoding oem then you can run the cli tool webpack bundle analyzer bundle output path stats json options for cli bash webpack bundle analyzer bundlestatsfile bundledir options arguments are documented below bundlestatsfile path to webpack stats json file bundledir directory containing all generated bundles options v version output the version number m mode mode analyzer mode should be server or static in server mode analyzer will start http server to show bundle report in static mode single html file with bundle report will be generated default server h host host host that will be used in server mode to start http server default 127 0 0 1 p port n port that will be used in server mode to start http server default 8888 r report file path to bundle report file that will be generated in static mode default report html s default sizes type module sizes to show in treemap by default possible values stat parsed gzip default parsed o no open dont open report in default browser automatically e exclude regexp assets that should be excluded from the report can be specified multiple times l log level level log level possible values debug info warn error silent default info h help output usage information size definitions webpack bundle analyzer reports three values for sizes defaultsizes can be used to control which of these is shown by default the different reported sizes are stat this is the input size of your files before any transformations like minification it is called stat size because its obtained from webpacks stats object parsed this is the output size of your files if youre using a webpack plugin such as uglify then this value will reflect the minified size of your code gzip this is the size of running the parsed bundles modules through gzip compression troubleshooting i cant see all the dependencies in a chunk this is a known caveat when webpack optimize moduleconcatenationplugin is used with webpack 3 or webpack bundle analyzer 2 11 0 the way moduleconcatenationplugin works is that it merges multiple modules into a single one and so that resulting module doesnt have edges anymore webpack 3 didnt provide any information about concatenated modules but webpack 4 started including it into a stats files and webpack bundle analyzer 2 11 0 learned to show it if for some reason you cant update to the latest versions try analyzing your bundle without moduleconcatenationplugin see issue 115 for more discussion if you are using angular cli 6 0 0 which is based on webpack 3 and uses moduleconcatenationplugin you can build your project using the following command ng build stats json build optimizer false vendor chunk true the resulting stats json can be found at dist stats json please be aware that this is not a reasonable build for production use as it increases the build output size considerably maintainers yuriy grunin vesa laakso contributing check out contributing md for instructions on contributing tada