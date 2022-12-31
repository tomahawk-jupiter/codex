# AI Chat App

Using OpenAI. I followed [this tutorial](https://www.youtube.com/watch?v=2FeymQoKvrk) on youtube.

## Quick Overview

The frontend takes a text prompt from the user (using a simple form) and passes it to the backend which uses the openAI API to get a response which is then passed back to the frontend to be displayed.

The frontend boilerplate was created using `vite`.

## Run the code

**NOTE**: change the fetch request url in the `script.js` file to `http://localhost:5000` to run the app locally.

Start the frontend from inside the `client` folder: `$ npm start dev`.

Start the backend from inside the `server` folder: `$ npm start server`.
