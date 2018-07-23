Parse CSV with JavaScript Papa Parse is the fastest in-browser CSV (or delimited text) parser for JavaScript. It is reliable and correct according to RFC 4180, and it comes with these features: Easy to use Parse CSV files directly (local or over the network) Fast mode (is really fast) Stream large files (even via HTTP) Reverse parsing (converts JSON to CSV) Auto-detect delimiter Worker threads to keep your web page reactive Header row support Pause, resume, abort Can convert numbers and booleans to their types Optional jQuery integration to get files from <input type="file"> elements One of the only parsers that correctly handles line-breaks and quotations Papa Parse has no dependencies - not even jQuery. Install papaparse is available on npm. It can be installed with the following command: npm install papaparse If you dont want to use npm, papaparse.min.js can be downloaded to your project source. Homepage & Demo Homepage Demo To learn how to use Papa Parse: Documentation The website is hosted on on Github Pages. If you want to contribute just clone the gh-branch of this repository and open a pull request. Papa Parse for Node Papa Parse can parse a Readable Stream instead of a File when used in Node.js environments (in addition to plain strings). In this mode, encoding must, if specified, be a Node-supported character encoding. The Papa.LocalChunkSize, Papa.RemoteChunkSize , download, withCredentials and worker config options are unavailable. Papa Parse can also parse in a node streaming style which makes .pipe available. Simply pipe the Readable Stream to the stream returned from Papa.parse(Papa.NODE_STREAM_INPUT, options). The Papa.LocalChunkSize, Papa.RemoteChunkSize , download, withCredentials, worker, step, and complete config options are unavailable. To register a callback with the stream to process data, use the data event like so: stream.on(data, callback) and to signal the end of stream, use the end event like so: stream.on(end, callback). Get Started For usage instructions, see the homepage and, for more detail, the documentation. Tests Papa Parse is under test. Download this repository, run npm install, then npm test to run the tests. Contributing To discuss a new feature or ask a question, open an issue. To fix a bug, submit a pull request to be credited with the contributors! Remember, a pull request, with test, is best. You may also discuss on Twitter with #PapaParse or directly to me, @mholt6. If you contribute a patch, ensure the tests suite is running correctly. We run continuous integration on each pull request and will not accept a patch that breaks the tests.