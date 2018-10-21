# mobile_my_trainer
'use strict';

const express = require('express');

const app = express();

// [START hello_world]
// Say hello!
app.get('/', (req, res) => {
  res.status(200).send('Hello, world!');
});
// [END hello_world]

if (module === require.main) {
  // [START server]
  // Start the server
  const server = app.listen(process.env.PORT || 8080, () => {
    const port = server.address().port;
    console.log(`App listening on port ${port}`);
  });
  // [END server]
}

module.exports = app;

app.get('/account',
  ensureLoggedIn('/login'),
  function(req, res) {
    res.send('<html><body>Ola '+ req.user.username+'.<br/><a href="/logout">Logout</a></body></html> ');
  });
  app.get('/login'),
  /* @callback */ function(req, res) {
    res.send('<html><body><a href="/auth/twitter">Login com Twitter</a></body></html>');
  };
  var TWITTER_CONSUMER_KEY = "INSIRA_SUA_KEY_AQUI";
var TWITTER_CONSUMER_SECRET = "INSIRA_SUA_SECRET_AQUI";
 
passport.use(new TwitterStrategy({
    consumerKey: TWITTER_CONSUMER_KEY,
    consumerSecret: TWITTER_CONSUMER_SECRET,
    callbackURL: "http://127.0.0.1:3000/auth/twitter/callback"
  },
  /* @callback */ function(token, tokenSecret, profile, done) {
    // NOTA: Voce tera, provavelmente, que associar o usuario do Twitter
    //       com um registro do usuario no banco de dados da aplicacao.
    var user = profile;
    return done(null, user);
  }
));
app.get('/auth/twitter', passport.authenticate('twitter'));
app.get('/auth/twitter/callback', passport.authenticate('twitter', { successReturnToOrRedirect: '/account', failureRedirect: '/login' }));
app.use(express.static(__dirname + '/public'));
app.use(express.cookieParser());
app.use(express.session({ secret: 'usado para calcular o hash' }));
app.use(passport.initialize());
app.use(passport.session());
passport.serializeUser(function(user, done) {
  done(null, user);
});

passport.deserializeUser(function(obj, done) {
  done(null, obj);
});
var express = require('express'),
    passport = require('passport'),
    TwitterStrategy = require('passport-twitter').Strategy,
    ensureLoggedIn = require('connect-ensure-login').ensureLoggedIn,
    app = express();
 
app.use(express.static(__dirname + '/public'));
app.use(express.cookieParser());
app.use(express.session({ secret: 'usado para calcular o hash' }));
app.use(passport.initialize());
app.use(passport.session());
 
passport.serializeUser(function(user, done) {
  done(null, user);
});
 
passport.deserializeUser(function(obj, done) {
  done(null, obj);
});
 
 
var TWITTER_CONSUMER_KEY = "INSIRA_SUA_KEY_AQUI";
var TWITTER_CONSUMER_SECRET = "INSIRA_SUA_SECRET_AQUI";
 
passport.use(new TwitterStrategy({
    consumerKey: TWITTER_CONSUMER_KEY,
    consumerSecret: TWITTER_CONSUMER_SECRET,
    callbackURL: "http://127.0.0.1:3000/auth/twitter/callback"
  },
  /* @callback */ function(token, tokenSecret, profile, done) {
    // NOTA: Voce tera, provavelmente, que associar o usuario do Twitter
    //       com um registro do usuario no seu banco de dados.
    var user = profile;
    return done(null, user);
  }
));
 
 
app.get('/', /* @callback */ function(req, res){
    res.send('<html><body>Ola mundo<br/><a href="/login">Login</a></body></html>');
  });
 
app.get('/account',
  ensureLoggedIn('/login'),
  function(req, res) {
    res.send('<html><body>Ola '+ req.user.username+'.<br/><a href="/logout">Logout</a></body></html> ');
  });
 
app.get('/login',
  /* @callback */ function(req, res) {
    res.send('<html><body><a href="/auth/twitter">Login com Twitter</a></body></html>');
  });
  
app.get('/logout',
  function(req, res) {
    req.logout();
    res.redirect('/');
  });
 
app.get('/auth/twitter', passport.authenticate('twitter'));
app.get('/auth/twitter/callback', passport.authenticate('twitter', { successReturnToOrRedirect: '/account', failureRedirect: '/login' }));
 
 
var server = app.listen(3000);
console.log('Seridor express iniciado na porta %s', server.address().port);

echo; "# mobile_my_trainer" >> README.md; 
git; init; 
git; add; README.md; 
git; commit -m; "primeiro commit"; 
git; remoto; add; origem; https://github.com/polinevs/mobile_my_trainer.git
 git; push -u; origem; master;
