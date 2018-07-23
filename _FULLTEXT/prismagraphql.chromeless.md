Chromeless Chrome automation made simple. Runs locally or headless on AWS Lambda. (See Demo) Chromeless can be used to... Run 1000s of browser integration tests in parallel ⚡️ Crawl the web & automate screenshots Write bots that require a real browser Do pretty much everything youve used PhantomJS, NightmareJS or Selenium for before Examples JSON of Google Results: Google for chromeless and get a list of JSON results Screenshot of Google Results: Google for chromeless and take a screenshot of the results prep: Compile-time prerendering for SPA/PWA (like React, Vue...) instead of server-side rendering (SSR) See the full examples list for more ▶️ Try it out You can try out Chromeless and explore the API in the browser-based demo playground (source). Contents How it works Installation Usage API Documentation Configuring Development Environment FAQ Contributors Credits Help & Community How it works With Chromeless you can control Chrome (open website, click elements, fill out forms...) using an elegant API. This is useful for integration tests or any other scenario where youd need to script a real browser. There are 2 ways to use Chromeless Running Chrome on your local computer Running Chrome on AWS Lambda and controlling it remotely 1. Local Setup For local development purposes where a fast feedback loop is necessary, the easiest way to use Chromeless is by controlling your local Chrome browser. Just follow the usage guide to get started. 2. Remote Proxy Setup You can also run Chrome in headless-mode on AWS Lambda. This way you can speed up your tests by running them in parallel. (In Graphcools case this decreased test durations from ~20min to a few seconds.) Chromeless comes out of the box with a remote proxy built-in - the usage stays completely the same. This way you can write and run your tests locally and have them be executed remotely on AWS Lambda. The proxy connects to Lambda through a Websocket connection to forward commands and return the evaluation results. Installation sh npm install chromeless Proxy Setup The project contains a Serverless service for running and driving Chrome remotely on AWS Lambda. Deploy The Proxy service to AWS Lambda. More details here Follow the usage instructions here. Usage Using Chromeless is similar to other browser automation tools. For example: ```js const { Chromeless } = require(chromeless) async function run() { const chromeless = new Chromeless() const screenshot = await chromeless .goto(https://www.google.com) .type(chromeless, input[name="q"]) .press(13) .wait(#resultStats) .screenshot() console.log(screenshot) // prints local file path or S3 url await chromeless.end() } run().catch(console.error.bind(console)) ``` Local Chrome Usage To run Chromeless locally, you need a recent version of Chrome or Chrome Canary installed (version 60 or greater). By default, chromeless will start Chrome automatically and will default to the most recent version found on your system if theres multiple. You can override this behavior by starting Chrome yourself, and passing a flag of launchChrome: false in the Chromeless constructor. To launch Chrome yourself, and open the port for chromeless, follow this example: sh alias canary="/Applications/Google\ Chrome\ Canary.app/Contents/MacOS/Google\ Chrome\ Canary" canary --remote-debugging-port=9222 Or run Chrome Canary headless-ly: sh canary --remote-debugging-port=9222 --disable-gpu --headless Or run Chrome headless-ly on Windows: sh cd "C:\Program Files (x86)\Google\Chrome\Application" chrome --remote-debugging-port=9222 --disable-gpu --headless Proxy Usage Follow the setup instructions here. Then using Chromeless with the Proxy service is the same as running it locally with the exception of the remote option. Alternatively you can configure the Proxy services endpoint with environment variables. Heres how. js const chromeless = new Chromeless({ remote: { endpointUrl: https://XXXXXXXXXX.execute-api.eu-west-1.amazonaws.com/dev, apiKey: your-api-key-here, }, }) API Documentation Chromeless constructor options - new Chromeless(options: ChromelessOptions) Chromeless methods - end() Chrome methods - goto(url: string, timeout?: number) - setUserAgent(useragent: string) - click(selector: string, x?: number, y?: number) - wait(timeout: number) - wait(selector: string) - [wait(fn: (...args: any[]) => boolean, ...args: any[])] - Not implemented yet - clearCache() - clearStorage(origin: string, storageTypes: string) - focus(selector: string) - press(keyCode: number, count?: number, modifiers?: any) - type(input: string, selector?: string) - back() - Not implemented yet - forward() - Not implemented yet - refresh() - Not implemented yet - mousedown(selector: string) - mouseup(selector: string) - scrollTo(x: number, y: number) - scrollToElement(selector: string) - setHtml(html: string) - setExtraHTTPHeaders(headers: Headers) - setViewport(options: DeviceMetrics) - evaluate<U extends any>(fn: (...args: any[]) => void, ...args: any[]) - inputValue(selector: string) - exists(selector: string) - screenshot(selector: string, options: ScreenshotOptions) - pdf(options?: PdfOptions) - html() - cookies() - cookies(name: string) - cookies(query: CookieQuery) - Not implemented yet - allCookies() - setCookies(name: string, value: string) - setCookies(cookie: Cookie) - setCookies(cookies: Cookie[]) - deleteCookies(name: string) - clearCookies() - clearInput(selector: string) - setFileInput(selector: string, files: string | string[]) Configuring Development Environment Requirements: - NodeJS version 8.2 and greater 1) Clone this repository 2) Run npm install 3) To build: npm run build Linking this NPM repository 1) Go to this repository locally 2) Run npm link 3) Go to the folder housing your chromeless scripts 4) Run npm link chromeless Now your local chromeless scripts will use your local development of chromeless. FAQ How is this different from NightmareJS, PhantomJS or Selenium? The Chromeless API is very similar to NightmareJS as their API is pretty awesome. The big difference is that Chromeless is based on Chrome in headless-mode, and runs in a serverless function in AWS Lambda. The advantage of this is that you can run hundreds of browsers in parallel, without having to think about parallelisation. Running integration Tests for example is much faster. Im new to AWS Lambda, is this still for me? You still can use this locally without Lambda, so yes. Besides that, here is a simple guide on how to set the lambda function up for Chromeless. How much does it cost to run Chromeless in production? The compute price is $0.00001667 per GB-s and the free tier provides 400,000 GB-s. The request price is $0.20 per 1 million requests and the free tier provides 1M requests per month. This means you can easily execute > 100.000 tests for free in the free tier. Are there any limitations? If youre running Chromeless on AWS Lambda, the execution cannot take longer than 5 minutes which is the current limit of Lambda. Besides that, every feature thats supported in Chrome is also working with Chromeless. The maximal number of concurrent function executions is 1000. AWS API Limits Are there commercial options? Although Chromeless is the easiest way to get started running Chrome on Lambda, you may not have time to build and manage your own visual testing toolkit. Commercial options include: Chromatic: Visual snapshot regression testing for Storybook. Troubleshooting Error: Unable to get presigned websocket URL and connect to it. In case you get an error like this when running the Chromeless client: { HTTPError: Response code 403 (Forbidden) at stream.catch.then.data (/code/chromeless/node_modules/got/index.js:182:13) at process._tickDomainCallback (internal/process/next_tick.js:129:7) name: HTTPError, ... Error: Unable to get presigned websocket URL and connect to it. Make sure that youre running at least version 1.19.0 of serverless. It is a known issue, that the API Gateway API keys are not setup correctly in older Serverless versions. Best is to run npm run deploy within the project as this will use the local installed version of serverless. Resource ServerlessDeploymentBucket does not exist for stack chromeless-serverless-dev In case the deployment of the serverless function returns an error like this: ``` Serverless Error --------------------------------------- Resource ServerlessDeploymentBucket does not exist for stack chromeless-serverless-dev `` Please check, that there is no stack with the namechromeless-serverless-dev` existing yet, otherwise serverless cant correctly provision the bucket. No command gets executed In order for the commands to be processed, make sure, that you call one of the commands screenshot, evaluate, cookiesGetAll or end at the end of your execution chain. Contributors A big thank you to all contributors and supporters of this repository 💚 Credits chrome-remote-interface: Chromeless uses this package as an interface to Chrome serverless-chrome: Compiled Chrome binary that runs on AWS Lambda (Azure and GCP soon, too.) NightmareJS: We draw a lot of inspiration for the API from this great tool Help & Community Join our Slack community if you run into issues or have questions. We love talking to you!