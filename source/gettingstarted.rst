Getting Started with Phood Api
===============================

The phood api provides access to users, payment types, payment balance and other phood delivery resources.  

Accessing the Phood API GraphQL endpoint
------------------------------------------
You can access the Phood API GraphQL endpoing using GraphiQL, curl or any HTTP client. 
You SHOULD use the **POST** method for all requests.

The GraphQL endpoint is
:: 

    https://phood-api-prod.herokuapp.com/graphql


Authentication
---------------
The Phood API also requires an **access token**, which can only be obtained with a valid account.

All authorization methods will return an authorization token that shoul be passed to the header.
::

    Authorization: Bearer <token>

**Curl Example with authorization token in the header**
::

    curl \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer EBnKHEB.DvtHpdHTruklmS3g2Lf5tswGqTvG2t9uBBbXeotAQE4" \
    -X POST https://phood-api-prod.herokuapp.com/graphql \
    -d '{ "query": " query{ me {email} }" }'

Phood Account
~~~~~~~~~~~~~~
**GraphQL**
::

    mutation {
        authenticate(email:"email@gmail.com", password:"password")
    }



Google Account
~~~~~~~~~~~~~~
**GraphQL**
::

    mutation {
        authenticateWithGoogle(accessToken: "token")
    }

Facebook Account
~~~~~~~~~~~~~~~~~
**GraphQL**
::

    mutation {
        authenticateWithFacebook(accessToken: "token")
    }

Twitter Account
~~~~~~~~~~~~~~~~
**GraphQL**
::

    mutation {
        authenticateWithTwitter(secret: "secret", token: "token")
    }


Curl Example
~~~~~~~~~~~~~~~~
This is an Example of a Curl request of the authenticate shown above.
::

    curl \
    -H "Content-Type: application/json" \
    -X POST https://phood-api-prod.herokuapp.com/graphql \
    -d '{ "query": " mutation Authenticate($userEmail:String!, $userPassword:String!){ 
    authenticate(email:$userEmail, password:$userPassword) }", 
    "variables": { "userEmail": "youremail@gmail.com", "userPassword": "password1234"} }'