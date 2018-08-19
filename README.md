# passport-line-token
Passport strategy for authenticating with Line access tokens using the OAuth 2.0 API.
Based on [Line Social API v2.1](https://developers.line.me/en/docs/social-api/)
## Installation

    $ npm install passport-line-token

## Usage
### Configure Strategy
```js
var LineTokenStrategy = require('passport-line-token');

passport.use(new LineTokenStrategy({
    clientID: LINE_CHANNEL_ID,
    clientSecret: LINE_CHANNEL_SECRET,
  }, function(accessToken, refreshToken, profile, done) {
    User.findOrCreate({lineId: profile.id}, function (error, user) {
      return done(error, user);
    });
  }
));
```

Use `passport.authenticate()`, specifying the `'line-token'` strategy, to authenticate requests.

```js
app.post('/auth/line/token',
  passport.authenticate('line-token'),
  function (req, res) {
    // do something with req.user
    res.send(req.user? 200 : 401);
  }
);
```


## Reference

- [passport-facebook-token](https://github.com/drudge/passport-facebook-token)
- [passport-line-auth](https://github.com/IvanWei/passport-line-auth) passport line strategy for web server
- [Line Socail Api](https://developers.line.me/en/docs/social-api/)

## License
[The MIT License](https://github.com/Ray0427/passport-line-token/blob/master/LICENSE)
