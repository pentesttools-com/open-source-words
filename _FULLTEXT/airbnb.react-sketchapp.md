This project is currently in beta and APIs are subject to change. render React components to Sketch; tailor-made for design systems Quickstart 🏃‍ First, make sure you have installed Sketch version 43+, & a recent npm. Open a new Sketch file, then in a terminal: ```bash git clone https://github.com/airbnb/react-sketchapp.git cd react-sketchapp/examples/basic-setup && npm install npm run render ``` Next, check out some more examples! Why?! Managing the assets of design systems in Sketch is complex, error-prone and time consuming. Sketch is scriptable, but the API often changes. React provides the perfect wrapper to build reusable documents in a way already familiar to JavaScript developers. What does the code look like? ```js import * as React from react; import { render, Text, Artboard } from react-sketchapp; const App = props => ( { props.message } ); export default (context) => { render(, context.document.currentPage()); } ``` What can I do with it? Manage design systems— react-sketchapp was built for Airbnbs design system; this is the easiest way to manage Sketch assets in a large design system Use real components for designs— Implement your designs in code as React components and render them into Sketch Design with real data— Designing with data is important but challenging; react-sketchapp makes it simple to fetch and incorporate real data into your Sketch files Build new tools on top of Sketch— the easiest way to use Sketch as a canvas for custom design tooling Found a novel use? Wed love to hear about it! Read more about why we built it Documentation Examples API Reference Styling Universal Rendering Data Fetching FAQ Contributing