# Software Engineering Interview Questions Project

So I thought it would be helpful to create an app with example software engineering interview questions so devs could exercise their interview brain muscles as they get ready for interviewing. I am super passionate about the Web Components standard and wanted to take Polymer 2.0 for a spin, so this project was a great opportunity to make that happen.

## Features
* Collection of example interview questions that exercise fundamental dev knowledge to solve (data structures, iterators, conditionals)
* Users can write the solution to a given question in their browser and test the results
* Unit tests go along with each question to test the user's solution and evaluate that it achieved the goal
* Example solutions to the questions provided

#### To Do
Some additional features that I would like to add:
* Static analysis of userland solution to catch bad patterns and Big O of space and time.
* Node based performance evaluation of userland solution vs example solution.

## Setup

### Prerequisites
First, install the [git client](https://git-scm.com/downloads). Next, install [node & npm](https://nodejs.org). 

Then, install the [Polymer CLI](https://github.com/Polymer/polymer-cli) via [npm](https://www.npmjs.com)

    npm install -g polymer-cli

Now, install [Bower](https://bower.io/) using [npm](https://www.npmjs.com)

    npm install -g bower

### Download the repo and restore dependencies

    mkdir iq-app
    cd iq-app      
    git clone https://github.com/aaron-schnieder/software-interview-questions.git
    cd software-interview-questions
    bower install

### Start the development server

This command serves the app at `http://localhost:8081` and provides basic URL
routing for the app:

    polymer serve

#### **** WARNING - USE CHROME FOR NOW ****
Something isn't rendering the CodeMirror correctly in Microsoft Edge. [Added an issue and need to fix it.](https://github.com/aaron-schnieder/software-interview-questions/issues/8)

# iq-question-template.html
This is the place to start if you want to add a new question to the project. I commented this baby up to explain key concepts of how the questions are built and
what needs to be done to create a new one.

`Think of this as the dev docs for this project.`

# Adding a new question

You can extend the app by adding more questions and example solutions. Doing this is pretty straight forward.

1. Create a new iq-question-name.html
2. Copy contents of iq-question-template.html to the new question
3. Edit app.html to import your question html, add an anchor tag to your question and add the view
4. Update polymer.json fragments to include the new question HTML file

# Web Components FTW
So you built your web app using one of the most popular GA web frameworks/libraries (Angular, React, etc.). Then a few months later you start reading about the next version of said framework/library that will require a complete re-architecture / re-write of your app (Angular v2). Or you read about the new hotness in the web dev community and all of the awesomeness it brings with it (preact, vuejs, inferno, etc.). 

How does that feel? Well, it feels a lot like this

![alt-text](https://media.tenor.com/images/ec46e93f5c45eafb689d5753af27d1f8/tenor.gif "Blow brains out.")

## Enter Web Components
The web components spec has actually been around for years. The spec (and the APIs that make up the spec, see below) have been evolving. The big problem has been browser support up until this point. But 2017 has seen some very exciting developments with browser support of the spec in most major browsers.

[Browser support](https://www.webcomponents.org/)

[Getting started with web components](https://www.webcomponents.org/introduction)

Tell the [Microsoft Edge team](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/) to support the full spec! ([here](https://wpdev.uservoice.com/forums/257854-microsoft-edge-developer/suggestions/6263785-shadow-dom-unprefixed), [here](https://wpdev.uservoice.com/forums/257854-microsoft-edge-developer/suggestions/6261318-html-imports) and [here](https://wpdev.uservoice.com/forums/257854-microsoft-edge-developer/suggestions/6261298-custom-elements))

## All the things!
The web components spec includes four key ingredients that enable encapsulated, extensible and loosely coupled standard components:
* Shadow DOM
* Custom Elements
* HTML Templates (along with slots)
* HTML Imports

Any browser that implements these APIs enables web developers to write rich apps built with small, custom components without the need for proprietary frameworks or libraries.

## But wait, there's more!!!
So if web components are standard spec and sooooo awesome, why use Polymer you ask??? Well, because the dream of using the browser platform, and only the browser platform, is closer than ever - but not quite there yet. 

Polymer provides some very helpful glue and tooling that takes care of some of the still painful parts of web components. *But the important bit is that Polymer does it in a non-proprietary way* so the app you write is 99% web components standard with a little Polymer sugar on top. 

### Why Polymer? 
The Polymer's team vision is for us not to need Polymer... that is a vision I can get behind. :) They want web developers to use as much as possible from the web platform standards and only add additional secret sauce where absolutely necessary. With this in mind, Polymer provides some key functionality in addition to the standard Web Components APIs that make developing web components much nicer.
* State management
* Databinding
* Polyfills for browsers that don't support all APIs (I am talking to you Edge!)
* [And a whole lot more](https://www.polymer-project.org/2.0/start/)

### #Usetheplatform
One of the other huge benefits of using Polymer, is **you aren't writing a Polymer app.** You are writing a JavaScript standards web app that uses Web Components and Custom Elements. Polymer provides some sugar on top, but if you ever wanted to completely ditch Polymer and go another route there is very little code you will need to change.

The Polymer promotes, supports and designs their APIs to [#usetheplatform](https://twitter.com/search?q=%23usetheplatform&lang=en)

## ES6
Last but not least, this app uses ES6 (ES2015) APIs such as `classes`, block scoping via the `let` keyword, `modules` and `Map` key/value pairs. ES6 adds some incredibly powerful new APIs to JavaScript. A lot of the APIs are natively supported in modern browsers so no transpiling or polyfills are necessary.

## Janky Browser Support
So you enjoy a considerable amount of self inflicted pain and still prefer IE11 huh? Well, thanks to Polymer it isn't a problem. One of the many benefits Polymer provides is transpiling / polyfilling APIs where necessary for older browsers.

If you need to use the transpiled / polyfilled version, [read more here.](https://www.polymer-project.org/2.0/docs/polyfills)

# Build

This command performs HTML, CSS, and JS minification on the application
dependencies, and generates a service-worker.js file with code to pre-cache the
dependencies based on the entrypoint and fragments specified in `polymer.json`.
The minified files are output to the `build/unbundled` folder, and are suitable
for serving from a HTTP/2+Push compatible server.

    polymer build

### Preview the build

This command serves the minified version of the app at `http://localhost:8081`
in an unbundled state, as it would be served by a push-compatible server:

    polymer serve build/unbundled

This command serves the minified version of the app at `http://localhost:8081`
generated using fragment bundling:

    polymer serve build/bundled