# ChatGPT AI App video notes

My notes from following along with [this tutorial](https://www.youtube.com/watch?v=2FeymQoKvrk).

## Contents

- [Vite](#vite)
- [Writing our frontend](#writing-our-app-frontend)
- [Backend](#backend)
- [Hosting Our Code](#hosting-our-code)

## [Vite](https://vitejs.dev/guide/)

A frontend javascript tool, its to do with modules and bundling etc. It sets up the boilerplate for your application.

### Create

To create a new project, and specify the template to use:

`$ npm create vite@latest my-app --template vanilla`

**Note**: There are some cli prompts that ask what template to use and to use js or ts.

### Install

Install the packages with `$ npm i`, `cd` into the folder first.

Run dev server:

`$ npm run dev`

## Writing our App Frontend

Download the assets and css from the vid description.

Add a simple form to the html.

Change our main module to be called `script.js`.

**Note**: We using vanilla javascript (ie. not react) and so we will use dom selection to interact with our dom elements.

### Loading dots

We will use setInterval to create the loading dots that will display while waiting for a response from the api (that we'll do later). This is done in the `script.js` file.

### Typing effect

We also want the bot to respond like its typing out the response rather than it all appearing at once. We can achieve this using `setInterval`:

```js
let interval = setInterval(() => {
  // do stuff every interval

  // stop, put this inside a condition:
  clearInterval(interval);
}, 300);
```

### Generate a unique id

In javascript (and many other languages) you can use the current time stamp to generate a unique id. In js use `Date.now();`. We can also combine this with a random number `Math.random()`.

**hexadecimal string:**

```js
const randomNumber = Math.random();
const hexadecimalString = randomNumber.toString(16);
```

### User Interface

We want the bot and the user chat boxes to show as different colored "stripes" and with the proper icon image.

### FormData

`const data = new FormData(form);`

formData.get() is used to retrieve values from the form object:

`data.get('prompt')` **Note**: prompt is the value of the name attribute on the textarea element.

`form.reset()` is used to reset the form object.

## Backend

This is the part that will interact with the chatGPT api.

### Setup

Create and cd into server folder.

Create a package json with: `$ npm init -y`.

`$ npm install cors dotenv express nodemon openai`

- cors - Cross-Origin Resource Sharing, needed for connecting our frontend and backend
- dotenv - for environment variables, ie. sensitive data like api keys
- express - backend framework
- nodemon - reloads changes to our code while developing
- openai

### OpenAI

This is done in `server/server.js`.

We need an api key from openAI. Create an account, click on your account icon and go to api keys to create a new one. Copy it into the .env file.

Open an example in the playground, there are different **models** to choose from (`text-davinci-003` works well).

There are other variables we can change. Eg. **temperature** controls randomness (or risk), from 0 - 1, 0 is no randomness, 1 is lots of randomness. If you don't want it to be random, ie. you want specific answers set it to 0.

**max_tokens**: how long the response can be.

**frequency_penalty** (0-1): how often it will repeat itself.

**NOTE**: hover over each one in the playground for an explanation of what it does.

Click `view code` to see the code for the selected parameter settings.

### Package.json

Add `"type": "module"` and add a script to start the server with nodemon.

Remove the `"main": "index.js"`

## Hosting Our Code

Push the code to github from where it can be hosted using the following services:

The backend can be hosted using [https://render.com/](https://render.com/) and the frontend hosted on [https://vercel.com/](https://vercel.com/).

**NOTE**: Setup the backend first because we need the live url to add to the frontend instead of using localhost. Remember to change this in the fetch request (in `script.js`) and push the changes to github.
