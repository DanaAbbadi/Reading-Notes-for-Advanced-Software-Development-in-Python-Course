# JSON Web Tokens


JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.


JWT or JSON Web Token is a string which is sent in HTTP request (from client to server) to validate authenticity of the client. But now, you don’t have to save JWT in database. Instead, you save it on client side only.

JWT is created with a secret key and that secret key is private to you. When you receive a JWT from the client, you can verify that JWT with this that secret key. Any modification to the JWT will result into verification failure.

A JWT is simply a string but it contains three distinct parts separated with dots (.).

## What is the JSON Web Token structure?

In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:

### Header

Header is simply a JSON string but it contains information about the algorithm of JWT encryption. Important fields in this JSON object are type and alg. type is always JWT. You can choose alg which stands for algorithm from HS256, RS256 and others of your choice.

    var header = '{"typ":"JWT", "alg":"HS256"}';

### Payload

Payload is any data that you want to include into JWT, it is also a JSON string. This data is base64 encoded as you can see from syntax of JWT above, hence you should be absolutely sure that there is no sensitive information as anyone can decode it and read it. Information like password and email should not be passed into payload.

You can add as many fields in payload as you want but you should not add more than 5-6 fields to keep size of JWT small. There are some standard fields that JWT specification recommends to add (but not necessary) like iss for issuer, sub for subject, exp for expiration time of token and there are couple of others which you can read on Wikipedia.

So a typical payload will look like below:

    var payload = '{"userId":"1101001", "name":"John Doe", "exp":"Sun Apr 25 2018 22:42:28 GMT+0530 (India Standard Time)"}';


### Signature

Signature is an encrypted string. Whatever algorithm you choose in header part, you need to encrypt first two parts of JWT which is base64(header) + '.' + base64(payload) with that algorithm. This is the only part of JWT which is not publically readable because it is encrypted with a secret key. Unless someone has the secret key, they can not decrypt this information.


## Are JWT tokens secure?

JWT (JSON Web Token) is an open standard (published in the RFC 7519) which defines a compact and self-contained method to encapsulate and share assertions (claims) about an entity (subject) between peers in a secure manner by using JSON objects. The content inside the token can be trusted and verified because it’s digitally signed (JWS, RFC 7515). The signature can be generated by using both symmetric (HMAC algorithms) or asymmetric keys (RSA or ECDSA). Additionally JWT can carry encrypted data (JWE, RFC 7516) to protect sensitive data.

## How do JSON Web Tokens work?

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

You also should not store sensitive session data in browser storage due to lack of security.

Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

    Authorization: Bearer <token>

This can be, in certain cases, a stateless authorization mechanism. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. If the JWT contains the necessary data, the need to query the database for certain operations may be reduced, though this may not always be the case.

If the token is sent in the Authorization header, Cross-Origin Resource Sharing (CORS) won't be an issue as it doesn't use cookies.

## How to Use JWT Authentication with Django REST Framework

We are going to use the djangorestframework_simplejwt library, recommended by the DRF developers.

    pip install djangorestframework_simplejwt

### settings.py

    REST_FRAMEWORK = {
        'DEFAULT_AUTHENTICATION_CLASSES': [
            'rest_framework_simplejwt.authentication.JWTAuthentication',
        ],
    }

### urls.py

    from django.urls import path
    from rest_framework_simplejwt import views as jwt_views

    urlpatterns = [
        # Your URLs...
        path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
        path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
    ]



### Obtain Token

First step is to authenticate and obtain the token. The endpoint is /api/token/ and it only accepts POST requests.

    http post http://127.0.0.1:8000/api/token/ username=vitor password=123

![img](https://simpleisbetterthancomplex.com/media/2018/12/jwt-obtain-token.png)

So basically your response body is the two tokens:

    {
        "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTQ1MjI0MjU5LCJqdGkiOiIyYmQ1NjI3MmIzYjI0YjNmOGI1MjJlNThjMzdjMTdlMSIsInVzZXJfaWQiOjF9.D92tTuVi_YcNkJtiLGHtcn6tBcxLCBxz9FKD3qzhUg8",
        "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTU0NTMxMDM1OSwianRpIjoiMjk2ZDc1ZDA3Nzc2NDE0ZjkxYjhiOTY4MzI4NGRmOTUiLCJ1c2VyX2lkIjoxfQ.rA-mnGRg71NEW_ga0sJoaMODS5ABjE5HnxJDb0F8xAo"
    }

After that you are going to store both the access token and the refresh token on the client side, usually in the localStorage.

In order to access the protected views on the backend (i.e., the API endpoints that require authentication), you should include the access token in the header of all requests, like this:

    http http://127.0.0.1:8000/hello/ "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eX

You can use this access token for the next five minutes.

After five min, the token will expire, and if you try to access the view again, you are going to get the following error:

    http http://127.0.0.1:8000/hello/ "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjo

![img](https://simpleisbetterthancomplex.com/media/2018/12/jwt-expired.png)