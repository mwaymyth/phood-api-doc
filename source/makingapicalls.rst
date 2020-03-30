Making API Calls
=================

All request (queries and mutations) go to a single HTTP endpoint.
You SHOULD use the **POST** method for all requests.

Request Requirements
--------------------

The Authorization Header
^^^^^^^^^^^^^^^^^^^^^^^^^
All request (queries and mutations) besides the authorization mutation will require an authorization token
that will need to be passed in the header.  Refer to :ref:`Authentication` to see how to get a token.

::

    Authorization: Bearer <token>

**Curl Example with authorization token in the header**
::

    curl \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer EBnKHEB.DvtHpdHTruklmS3g2Lf5tswGqTvG2t9uBBbXeotAQE4" \
    -X POST https://phood-api-prod.herokuapp.com/graphql \
    -d '{ "query": " query{ me {email} }" }'


The Content-Type Header
^^^^^^^^^^^^^^^^^^^^^^^^
The content type of a query MUST be **application/json**

::

    Content-Type: application/json

The Message Body
^^^^^^^^^^^^^^^^^^

The message body MUST be a JSON object.  It MUST contain a **query** key and MAY contain a **variables** key.

The value of **query** MUST be a single JSON string tha contains a valid GraphQL script(query or mutation).

If you reference variables in your GraphQL script, the value of **variables** MUST be a JSON object containg the 
key/vaulue pairs for each variable. 

**Example**

::

    {
      "query": "GraphQL script with reference vars $var1, $var2",
      "variables": {
        "var1" : "Hello",
        "var2" : 10
      }
    }

Making a Request
-----------------

We are going to make a simple request to receive the current users name and email. This Example
will illustrate how to generate well-formed requests.

Here is the GraphQL query:

::

    query {
        me {
            email
            name
        }
    }

To send that to our API, it has to be wrapped in a JSON object with a **query** key:

::

    {"query": "query { me { email name} }" }

And this is how we fit it all together, using **curl**:

::

    curl \
     -H "Content-Type: application/json" \
     -H "Authorization: Bearer EBnKHEB.DvtHpdHTruklmS3g2Lf5tswGqTvG2t9uBBbXeotAQE4" \
     -X POST https://phood-api-prod.herokuapp.com/graphql \
     -d '{ "query": " query{ me {email name} }" }'

You should recieve this response:

::

    {
        "data":{
          "me":{
            "email":"josh@smoothterminal.com",
            "name":"Josh Adams"
          }
        }
    }