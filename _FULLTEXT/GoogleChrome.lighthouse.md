Lighthouse Lighthouse analyzes web apps and web pages, collecting modern performance metrics and insights on developer best practices. Using Lighthouse in Chrome DevTools Lighthouse is integrated directly into the Chrome Developer Tools, under the "Audits" panel. Installation: install Chrome. Run it: open Chrome DevTools, select the Audits panel, and hit "Run audits". Using the Chrome extension Installation: install the extension from the Chrome Web Store. Run it: follow the extension quick-start guide. Using the Node CLI Lighthouse requires Node 8 LTS (8.9) or later. Installation: ```sh npm install -g lighthouse or use yarn: yarn global add lighthouse ``` Run it: lighthouse https://airhorner.com/ By default, Lighthouse writes the report to an HTML file. You can control the output format by passing flags. CLI options ```sh $ lighthouse --help lighthouse Logging: --verbose Displays verbose logging [boolean] --quiet Displays no progress, debug logs or errors [boolean] Configuration: --save-assets Save the trace contents & screenshots to disk [boolean] --list-all-audits Prints a list of all available audits and exits [boolean] --list-trace-categories Prints a list of all required trace categories and exits [boolean] --additional-trace-categories Additional categories to capture with the trace (comma-delimited). --config-path The path to the config JSON. --chrome-flags Custom flags to pass to Chrome (space-delimited). For a full list of flags, see http://peter.sh/experiments/chromium-command-line-switches/. Environment variables: CHROME_PATH: Explicit path of intended Chrome binary. If set must point to an executable of a build of Chromium version 66.0 or later. By default, any detected Chrome Canary or Chrome (stable) will be launched. [default: ""] --port The port to use for the debugging protocol. Use 0 for a random port [default: 0] --preset Use a built-in configuration. [choices: "full", "perf", "mixed-content"] --hostname The hostname to use for the debugging protocol. [default: "localhost"] --max-wait-for-load The timeout (in milliseconds) to wait before the page is considered done loading and the run should continue. WARNING: Very high values can lead to large traces and instability [default: 45000] --enable-error-reporting Enables error reporting, overriding any saved preference. --no-enable-error-reporting will do the opposite. More: https://git.io/vFFTO --gather-mode, -G Collect artifacts from a connected browser and save to disk. If audit-mode is not also enabled, the run will quit early. [boolean] --audit-mode, -A Process saved artifacts from disk [boolean] Output: --output Reporter for the results, supports multiple values [choices: "csv", "json", "html"] [default: "html"] --output-path The file path to output the results. Use stdout to write to stdout. If using JSON or CSV output, default is stdout. If using HTML output, default is a file in the working directory with a name based on the test URL and date. If using multiple outputs, --output-path is ignored. Example: --output-path=./lighthouse-results.html --view Open HTML report in your browser [boolean] Options: --help Show help [boolean] --version Show version number [boolean] --blocked-url-patterns Block any network requests to the specified URL patterns [array] --disable-storage-reset Disable clearing the browser cache and other storage APIs before a run [boolean] --disable-device-emulation Disable Nexus 5X emulation [boolean] --throttling-method Controls throttling method [choices: "devtools", "provided", "simulate"] --throttling.rttMs Controls simulated network RTT (TCP layer) --throttling.throughputKbps Controls simulated network download throughput --throttling.requestLatencyMs Controls emulated network RTT (HTTP layer) --throttling.downloadThroughputKbps Controls emulated network download throughput --throttling.uploadThroughputKbps Controls emulated network upload throughput --throttling.cpuSlowdownMultiplier Controls simulated + emulated CPU throttling --extra-headers Set extra HTTP Headers to pass with request [string] Examples: lighthouse --view Opens the HTML report in a browser after the run completes lighthouse --config-path=./myconfig.js Runs Lighthouse with your own configuration: custom audits, report generation, etc. lighthouse --output=json --output-path=./report.json --save-assets Save trace, screenshots, and named JSON report. lighthouse --disable-device-emulation Disable device emulation and all throttling. --throttling-method=provided lighthouse --chrome-flags="--window-size=412,732" Launch Chrome with a specific window size lighthouse --quiet --chrome-flags="--headless" Launch Headless Chrome, turn off logging lighthouse --extra-headers "{\"Cookie\":\"monster=blue\"}" Stringify\d JSON HTTP Header key/value pairs to send in requests lighthouse --extra-headers=./path/to/file.json Path to JSON file of HTTP Header key/value pairs to send in requests For more information on Lighthouse, see https://developers.google.com/web/tools/lighthouse/. ``` Output Examples ```sh lighthouse saves ./<HOST>_<DATE>.report.html lighthouse --output json json output sent to stdout lighthouse --output html --output-path ./report.html saves ./report.html NOTE: specifying an output path with multiple formats ignores your specified extension for ALL formats lighthouse --output json --output html --output-path ./myfile.json saves ./myfile.report.json and ./myfile.report.html lighthouse --output json --output html saves ./<HOST>_<DATE>.report.json and ./<HOST>_<DATE>.report.html lighthouse --output-path=~/mydir/foo.out --save-assets saves ~/mydir/foo.report.html saves ~/mydir/foo-0.trace.json and ~/mydir/foo-0.screenshots.html lighthouse --output-path=./report.json --output json saves ./report.json ``` Lifecycle Examples You can run a subset of Lighthouses lifecycle if desired via the --gather-mode (-G) and --audit-mode (-A) CLI flags. ```sh lighthouse http://example.com -G launches browser, collects artifacts, saves them to disk (in ./latest-run/) and quits lighthouse http://example.com -A skips browser interaction, loads artifacts from disk (in ./latest-run/), runs audits on them, generates report lighthouse http://example.com -GA Normal gather + audit run, but also saves collected artifacts to disk for subsequent -A runs. You can optionally provide a custom folder destination to -G/-A/-GA. Without a value, the default will be $PWD/latest-run. lighthouse -GA=./gmailartifacts https://gmail.com ``` Notes on Error Reporting The first time you run the CLI you will be prompted with a message asking you if Lighthouse can anonymously report runtime exceptions. The Lighthouse team uses this information to detect new bugs and avoid regressions. Opting out will not affect your ability to use Lighthouse in any way. Learn more. Viewing a report Lighthouse can produce a report as JSON or HTML. HTML report: Online Viewer Running Lighthouse with the --output=json flag generates a json dump of the run. You can view this report online by visiting https://googlechrome.github.io/lighthouse/viewer/ and dragging the file onto the app. You can also use the "Export" button from the top of any Lighthouse HTML report and open the report in the Lighthouse Viewer. In the Viewer, reports can be shared by clicking the share icon in the top right corner and signing in to GitHub. Note: shared reports are stashed as a secret Gist in GitHub, under your account. Docs & Recipes Useful documentation, examples, and recipes to get you started. Docs Using Lighthouse programmatically Testing a site with authentication Testing on a mobile device Lighthouse Architecture Recipes gulp - helpful for CI integration Custom Audit example - extend Lighthouse, run your own audits Videos The session from Google I/O 2018 covers the new performance engine, upcoming Lighthouse REST API, and using the Chrome UX report to evaluate real-user data. The session from Google I/O 2017 covers architecture, writing custom audits, GitHub/Travis/CI integration, headless Chrome, and more: click to watch the video Develop Read on for the basics of hacking on Lighthouse. Also see Contributing for detailed information. Setup ```sh yarn should be installed first git clone https://github.com/GoogleChrome/lighthouse cd lighthouse yarn yarn install-all yarn build-all ``` Run sh node lighthouse-cli http://example.com Getting started tip: node --inspect --debug-brk lighthouse-cli http://example.com to open up Chrome DevTools and step through the entire app. See Debugging Node.js with Chrome DevTools for more info. Tests ```sh lint and test all files yarn test watch for file changes and run tests Requires http://entrproject.org : brew install entr yarn watch run linting, unit, and smoke tests separately yarn lint yarn unit yarn smoke run tsc compiler yarn type-check ``` Lighthouse Integrations This section details services that have integrated Lighthouse data. If youre working on a cool project integrating Lighthouse and would like to be featured here, file an issue to this repo or tweet at us @_lighthouse! Calibre - Calibre is a web performance monitoring tool running Lighthouse continuously or on-demand via an API. Test using emulated devices and connection speeds from a number of geographical locations. Set budgets and improve performance with actionable guidelines. Calibre comes with a free 14-day trial. HTTPArchive - HTTPArchive tracks how the web is built by crawling 500k pages with Web Page Test, including Lighthouse results, and stores the information in BigQuery where it is publicly available. Treo - Treo is Lighthouse as a Service. It provides regression testing, geographical regions, custom networks, and integrations with GitHub & Slack. Treo is a paid product with plans for solo-developers and teams. Web Page Test — An open source tool for measuring and analyzing the performance of web pages on real devices. Users can choose to produce a Lighthouse report alongside the analysis of WebPageTest results. Related Projects Other awesome open source projects that use Lighthouse. webpack-lighthouse-plugin - run Lighthouse from a Webpack build. lighthouse-mocha-example - gather performance metrics via Lighthouse and tests them in Mocha pwmetrics - gather performance metrics lighthouse-hue - set the color of Philips Hue lights based on a Lighthouse score lighthouse-magic-light set the color of the MagicLight Bluetooth Smart Light Bulb based on Lighthouse score lighthouse-batch - run Lighthouse over a number of sites and generate a summary of their metrics/scores. lighthouse-cron - Cron multiple batch Lighthouse audits and emit results for sending to remote server. lightcrawler - Crawl a website and run each page found through Lighthouse. lighthouse-lambda - Run Lighthouse on AWS Lambda with prebuilt stable desktop Headless Chrome. lighthouse-security - Run a set of security audits along with Lighthouse. Garie — An open source tool for monitoring performance using Lighthouse, PageSpeed Insights, Prometheus, Grafana and Docker. lighthouse-ci - Run Lighthouse and assert scores satisfy your custom thresholds. FAQ How does Lighthouse work? See Lighthouse Architecture. Can I configure the lighthouse run? Yes! Details in Lighthouse configuration. How does Lighthouse use network throttling, and how can I make it better? Good question. Network and CPU throttling are applied by default in a Lighthouse run. The network attempts to emulate 3G and the CPU is slowed down 4x from your machines default speed. If you prefer to run Lighthouse without throttling, youll have to use the CLI and disable it with the --throttling.* flags mentioned above. Read more in our guide to network throttling. Are results sent to a remote server? Nope. Lighthouse runs locally, auditing a page using a local version of the Chrome browser installed the machine. Report results are never processed or beaconed to a remote server. How do I author custom audits to extend Lighthouse? Tip: see Lighthouse Architecture for more information on terminology and architecture. Lighthouse can be extended to run custom audits and gatherers that you author. This is great if youre already tracking performance metrics in your site and want to surface those metrics within a Lighthouse report. If youre interested in running your own custom audits, check out our Custom Audit Example over in recipes. How do I contribute? Wed love help writing audits, fixing bugs, and making the tool more useful! See Contributing to get started. Lighthouse, ˈlītˌhous (n): a tower or other structure tool containing a beacon light to warn or guide ships at sea developers.