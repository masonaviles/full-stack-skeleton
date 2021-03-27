# Steps to Full Stack

## Make a Front End
- `npx create-react-app my-app`

## Make a Back End
- `npm init`

## Back End Initial Set up
- `'use strict'` at the top of the `server.js` file you made in the last step
- set up your Libraries
```
// libraries
// allows us to access variables from the .env
require('dotenv').config();
// this library builds our server for us
const express = require('express');
// allows our front-end to access our server
const cors = require('cors');
// allows us to talk to APIs
const superagent = require('superagent');
```
- install Libraries via `npm` in your terminal
  - `npm install express`
  - `npm install cors`
  - `npm install dotenv`
  - `npm install superagent`
- initialize your server
  - `const app = express();`
- connect Express with Cors our people loving bodyguard
  - `app.use(cors());`
- make a variable to hold your `PORT`
  - `const PORT=process.env.PORT || 3002;` 
  - `PORT=3001` (this is in your `.env` file which should be at the root of the relavent directory)
- turn server on
  - ``app.listen(PORT, () => console.log(`listening on ${PORT}`))``
- check to see if it's working
  - `nodemon` in your terminal

## In your Front End, Clean up your Create React and take out everything you don't need

## Connect the Back and Front

### In the Front
- import Axios
  - `import axios from 'axios';`
- install Axios
  - `npm install axios`
- Make an `.env` in the Front End w/ the PORT of the backend
  - `REACT_APP_SERVER=http://localhost:3001`
- Connect it
```
  componentDidMount = async () => {
    const results = await axios.get(`${process.env.REACT_APP_SERVER}`);
  }
```

### In the Back
- make a route
  - `app.get('/bananas', banana.handleBanana);`
```
function handleBanana(request, response) {
  response.status(200).send('bananas are great!');
};
```

### In the Front
- check to see if it's working
```
componentDidMount = async () => {
  const results = await axios.get(`${process.env.REACT_APP_SERVER}`);
  console.log(results);
  console.log(results.data);
}
```
- yay, put it in a variavle
  - `const bananaResults = results.data;`
```
componentDidMount = async () => {
  const results = await axios.get(`${process.env.REACT_APP_SERVER}`);
  console.log(results);
  console.log(results.data);
  const bananaResults = results.data;
}
```

## Time to set up the API

### In the Front
- make a form to collect info
```
<form>
  <input onChange={(e)=> this.setState({address: e.target.value})} placeholder='enter your address'></input>
</form>
```
- take out what we did in `componentDidMount` and make a constructor with state
```
constructor(props){
  super(props);
  this.state={
    address:'',
    weather:[],
    location: {}
  }
}
```
- make a onSubmit on form so we can get weather
```
<form onSubmit={this.getLocation}>
  <input onChange={(e)=> this.setState({address: e.target.value})} placeholder='enter your address'></input>
</form>
```
```

```