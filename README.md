# Carma README

## Team Member Names
```
Judge Madan (tm3004)
Katie Kim (ksk2171)
Amy Kim (nk2816)
Jasmine Valera (jav2182)
```

## Background

The Carma app is split into a frontend written in React.js. User stories/cucumber tests can be found in the features/ folder in the frontend GitHub. In this iteration, the frontend is connected to the backend. The ‘axios’ library is used to make API requests to specified routes.

The cucumber tests are based on cucumber-js, and the ‘got’ and ‘jsdom’ libraries were used to each make a simple HTTP request to the deployed frontend and to access DOM elements along with 'selenium'.

A backend using Ruby on Rails deployed on Heroku. RSpec tests can be found in the backend GitHub. API routes are below. The authentication API is linked to AWS Cognito, which stores the username/password and returns a bearer token.

Please refer to the frontend and backend READMEs for more specific information. The instructions to run the frontend/backend are located in their respective GitHub repository READMEs and also below this README. 


## Deployment Links

>Frontend React App: http://carma-www-dashboard.s3-website.us-east-2.amazonaws.com/ 

>Backend Rails API: https://carma-apis.herokuapp.com/


## Github Links (Shared with TAs privately)

>Frontend Github Repo: https://github.com/JudgeMadan/carma-frontend/

>Backend Github Repo: https://github.com/jvalera174/carma-backend

<br>
<br>

---
---

<br>
<br>

# Carma Frontend


## Installation instructions to run our frontend locally

<br>

To run the frontend locally, you must have node installed on your machine. 

After cloning the project directory, run:

```npm install``` 

### In the project directory, you can run:

<br>

```npm start```

<br>
This runs the app in the development mode.
Open http://localhost:3000 to view it in the browser.



<br>
<br>

## Testing using Cucumber-js
<br>

``` npm test``` with Google Chrome installed as the default test kit.





<br>
<br>

---
---

<br>
<br>







# Carma Backend

The Carma Backend uses Ruby on Rails API deployed to Heroku. It uses AWS Cognito for user authentication, and currently it is using the default Heroku Postgresql as its database. It is an API-only application that produces JSON for the front end. 

For this first iteration, the backend allows users to create an account, sign-in to an existing account, and view profile information, both of all profiles and for an individual profile. This is an MVP because as an organization that wants to join Carma, it needs to create an account, and go to the profiles page where it can see its account information. 

For the second iteration, we added a Coins API and a Market Trading API. The Coins API allows users to create and retire carbon coins and allows admins to verify coins created by COPs. The Market Trading API allows users to buy and sell coins in the market.

For the third iteration, we added more features to the Market Trading API to make allow for custom trading (trading with a specific COP) in addition to market trading. We also added a feature that allows users to buy multiple coins through one request. Also, we allow trade requests to expire after a designated amount of time.

## Installation instructions to run our backend locally

<br>

>Clone the repository: https://github.com/jvalera174/carma-backend.git

\*Note to TAs: Please work off of main branch. 

<br>

>Make sure Ruby is installed by following these instructions:  https://www.ruby-lang.org/en/documentation/installation/

<br>

>Make sure Rails is installed by following these instructions: https://guides.rubyonrails.org/v5.0/getting_started.html

<br>

>Run these commands in your terminal to start the server: 

```
cd carma-backend
bundle install
rails db:migrate
rails server
```

<br>

>Go the link provided by the server. It should look something like this: http://127.0.0.1:3000

<br>


## Routes
```
Profiles:

  GET /profiles
  
  GET /profiles/cop
  
  GET /profiles/businesses
  
  GET /profiles/admin

  GET /profiles/:id

  POST /profiles 

  PUT /profiles/:id

  DELETE /profiles/:id


Auth:

  POST /auth/signup with form-data body {email, password, first_name, last_name}

  POST /auth/signin with form-data body {email, password}
  
  
Coins:

  GET /coins

  POST /coins with form-data body {current_owner_userid, coin_creator_userid, city_created, state_created, country_created, offset_type, coin_created_date, verified_by, verified (default is 0), retired}

  GET /coins/user/:user_id

  PATCH /coins/retire/:id

  PATCH /coins/verify/:id

  DELETE /coins/:id


Market Trading:

  GET /trades
  
  POST /trades/buy with form-data body {profile_id, price, quantity (opt), traded_with (opt)}

  POST /trades/sell with form-data body {profile_id, coin_id, price}
  
  GET /trades/:id
  
  GET /trades/user/:user_id
  
  GET /trades/pending/buy/user/:user_id
  
  GET /trades/pending/sell/user/:user_id

  GET /trades/marketprice
  
  PATCH /trades/:id
  
  PATCH trades/expired_status
  
  DELETE /trades/:id
  
```

<br>

\*Note to TAs: POST, PATCH, DELETE requests must be done through Postman as they will not work through the browser. Many of the POST, PATCH, and DELETE routes are for admin purposes.  

<br>

## Deploying to Heroku
>Go to our deployed heroku app: https://carma-apis.herokuapp.com/

\*Note to TAs: The route GET / will lead to a 404 error as we have not implemented that on the backend. Please try the routes above. 


## Instructions to test our RSpec

```
bundle exec rspec -fd  spec/models
bundle exec rspec -fd spec/requests
```
\*Note to TAs: We are testing auth_controller, profile_controller, coin_controller, and trades_controller through the specs in the requests folder.



---
---

<br>
<br>




## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
