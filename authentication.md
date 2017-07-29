# Authentication
Authentication with the API is initially handled via Username(Email Address) and Password authentication for the initial Login request. Afterward, all requests are authenticated with a secure session token, which is obtained during the login process, and needs to be included as a header in EVERY request made to the API.

Session tokens are not everlasting, and will eventually expire, at which point you will receive a **401 - Unauthorized** error message. Tokens cannot be renewed, and you will need to authenticate via username and password to obtain a new token.

{% method %}
## POST `/login`

This request is used to initially authenticate a user. It can also be used to verify if a user has entered their password correctly, for example if they are updating their password.

The password needs to be sent as a Base64 encoded string. This allows for complex passwords, that would otherwise break the JSON formatting if not encoded properly.

If the email and password are correct, the response from the server will contain a `JSESSION` header; this is your session token. You will want to save this, possible in a Cookie, Global Variable, etc. You should keep it relatively secure, since it is used to authenticate with the API for all further interactions, but will eventually expire.

{% sample lang="js" %}
Login request using jQuery. You will need to fill the object yourself, this example uses example content selectors. You can also use a `<form>` and some `onsubmit` js to complete this request, which is how the Web Interface completes this request.


```js

var form_data = new FormData();

form_data.append("email", $('#loginEmail').val());
form_data.append("password", bota($('#loginPassword').val()));

$.ajax({
  type: "POST",
  url: API_ROOT + '/login',
  data: form_data,
  success: success,
  dataType: 'application/x-www-form-urlencoded'
});
```

{% common %}
If successful a `SEE_OTHER` redirect (**303**) is returned, directing the user to the index page. , the user object corresponding to the username and password pair that were submitted is returned.

```json
{
  "first_name": "Administrator",
  "last_name": "User",
  "email": "admin@example.com",
  "notify": true
}
```
Also, a `JSESSION` header will be included in the response, this is the session token that you will need to include in all future requests, and will serve to identify the user.

If either the username or password or incorrect a status a `SEE_OTHER` redirect **303** is returned, directing the user to the Login Page.

If the request is incomplete, a status of **400** (Bad Request) is returned, along with a JSON error message.

```json
{
  "status": "error",
  "message": "Email or Password not included in request"
}
```

{% endmethod %}
