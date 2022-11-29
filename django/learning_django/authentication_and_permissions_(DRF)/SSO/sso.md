# SSO

**Single sign-on (SSO)** is a technology which combines several different application
  login screens into one.  With SSO, a user only has to enter their login credentials
    (username, password, etc.) one time on a single page to access all of their SaaS
      applications.

> Read more: [What is SSO ?](https://www.cloudflare.com/learning/access-management/what-is-sso/),
  [How SSO works?](https://www.onelogin.com/learn/how-single-sign-on-works)

## SSO workflow

![db25bfa9dc1c69836a5af6b17ff08ded.png](../../../../_resources/db25bfa9dc1c69836a5af6b17ff08ded.png)

Service provider --> your app (Django or Nest ... backend)
Identity provider --> services like Google, Github auth providers

## Django and react workflow

![7193da46a15aa887909383f14f6bdf28.png](../../../../_resources/7193da46a15aa887909383f14f6bdf28.png)

> Note: For google login scopes must be explicitly provided when making request from
  client side to the authentication server
