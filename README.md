# api documentation for  [passport-windowsauth (v2.0.0)](https://github.com/auth0/passport-windowsauth#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-passport-windowsauth.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-passport-windowsauth) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-passport-windowsauth.svg)](https://travis-ci.org/npmdoc/node-npmdoc-passport-windowsauth)
#### Passport strategy for Windows Integrated Authentication (NTLM)

[![NPM](https://nodei.co/npm/passport-windowsauth.png?downloads=true)](https://www.npmjs.com/package/passport-windowsauth)

[![apidoc](https://npmdoc.github.io/node-npmdoc-passport-windowsauth/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-passport-windowsauth_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-passport-windowsauth/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-passport-windowsauth/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-passport-windowsauth/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Auth0"
    },
    "bugs": {
        "url": "https://github.com/auth0/passport-windowsauth/issues"
    },
    "dependencies": {
        "ldapjs": "~1.0.0",
        "passport": "~0.1.15"
    },
    "description": "Passport strategy for Windows Integrated Authentication (NTLM)",
    "devDependencies": {
        "chai": "~1.5.0",
        "mocha": "~1.8.2"
    },
    "directories": {},
    "dist": {
        "shasum": "7998077b0eb4d8eedc99c854ddff0e16b45245e5",
        "tarball": "https://registry.npmjs.org/passport-windowsauth/-/passport-windowsauth-2.0.0.tgz"
    },
    "gitHead": "2d5b0b0fc365ba2664fc8e1e09fd27c5706c5fd5",
    "homepage": "https://github.com/auth0/passport-windowsauth#readme",
    "keywords": [
        "passport",
        "windows",
        "auth",
        "ntlm"
    ],
    "license": "MIT",
    "main": "lib/strategy.js",
    "maintainers": [
        {
            "name": "jfromaniello",
            "email": "jfromaniello@gmail.com"
        },
        {
            "name": "iaco",
            "email": "sebastian.iacomuzzi@gmail.com"
        }
    ],
    "name": "passport-windowsauth",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/auth0/passport-windowsauth.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "2.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module passport-windowsauth](#apidoc.module.passport-windowsauth)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapLookup (options)](#apidoc.element.passport-windowsauth.LdapLookup)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapValidator (options)](#apidoc.element.passport-windowsauth.LdapValidator)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.</span>super_ ()](#apidoc.element.passport-windowsauth.super_)
1.  object <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapLookup.prototype
1.  object <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapValidator.prototype
1.  object <span class="apidocSignatureSpan">passport-windowsauth.</span>super_.prototype

#### [module passport-windowsauth.LdapLookup](#apidoc.module.passport-windowsauth.LdapLookup)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapLookup (options)](#apidoc.element.passport-windowsauth.LdapLookup.LdapLookup)

#### [module passport-windowsauth.LdapLookup.prototype](#apidoc.module.passport-windowsauth.LdapLookup.prototype)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.LdapLookup.prototype.</span>search (username, callback)](#apidoc.element.passport-windowsauth.LdapLookup.prototype.search)

#### [module passport-windowsauth.LdapValidator](#apidoc.module.passport-windowsauth.LdapValidator)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapValidator (options)](#apidoc.element.passport-windowsauth.LdapValidator.LdapValidator)

#### [module passport-windowsauth.LdapValidator.prototype](#apidoc.module.passport-windowsauth.LdapValidator.prototype)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.LdapValidator.prototype.</span>validate (username, password, callback)](#apidoc.element.passport-windowsauth.LdapValidator.prototype.validate)

#### [module passport-windowsauth.super_](#apidoc.module.passport-windowsauth.super_)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.</span>super_ ()](#apidoc.element.passport-windowsauth.super_.super_)

#### [module passport-windowsauth.super_.prototype](#apidoc.module.passport-windowsauth.super_.prototype)
1.  [function <span class="apidocSignatureSpan">passport-windowsauth.super_.prototype.</span>authenticate (req, options)](#apidoc.element.passport-windowsauth.super_.prototype.authenticate)



# <a name="apidoc.module.passport-windowsauth"></a>[module passport-windowsauth](#apidoc.module.passport-windowsauth)

#### <a name="apidoc.element.passport-windowsauth.LdapLookup"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapLookup (options)](#apidoc.element.passport-windowsauth.LdapLookup)
- description and source-code
```javascript
LdapLookup = function (options){
  this._options = options;

  this._search_query = options.search_query ||
    '(&(objectclass=user)(|(sAMAccountName={0})(UserPrincipalName={0})))';

  this._client = options.client ? options.client : ldap.createClient({
    url:             options.url,
    maxConnections:  options.maxConnections || 10,
    bindDN:          options.bindDN,
    bindCredentials: options.bindCredentials,
    tlsOptions:      options.tlsOptions,
    reconnect:       options.reconnect,
    timeout:         options.timeout,
    connectTimeout:  options.connectTimeout,
    idleTimeout:     options.idleTimeout
  });

  this._client.on('error', function(e){
    // Suppress logging of ECONNRESET if ldapjs's Client will automatically reconnect.
    if (e.errno === 'ECONNRESET' && self._client.reconnect) return;

    console.log('LDAP connection error:', e);
  });

  if (options.client) {
    this.clientConnected = true;
    return;
  }

  this._queue = [];
  var self = this;
  this._client.bind(options.bindDN, options.bindCredentials, function(err) {
    if(err){
        return console.log("Error binding to LDAP", 'dn: ' + err.dn + '\n code: ' + err.code + '\n message: ' + err.message);
    }
    self.clientConnected = true;
    self._queue.forEach(function (cb) { cb(); });
  });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.passport-windowsauth.LdapValidator"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapValidator (options)](#apidoc.element.passport-windowsauth.LdapValidator)
- description and source-code
```javascript
LdapValidator = function (options){
  this._options = options;
  this._lookup = new LdapLookup(options);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.passport-windowsauth.super_"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.</span>super_ ()](#apidoc.element.passport-windowsauth.super_)
- description and source-code
```javascript
function Strategy() {
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.passport-windowsauth.LdapLookup"></a>[module passport-windowsauth.LdapLookup](#apidoc.module.passport-windowsauth.LdapLookup)

#### <a name="apidoc.element.passport-windowsauth.LdapLookup.LdapLookup"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapLookup (options)](#apidoc.element.passport-windowsauth.LdapLookup.LdapLookup)
- description and source-code
```javascript
LdapLookup = function (options){
  this._options = options;

  this._search_query = options.search_query ||
    '(&(objectclass=user)(|(sAMAccountName={0})(UserPrincipalName={0})))';

  this._client = options.client ? options.client : ldap.createClient({
    url:             options.url,
    maxConnections:  options.maxConnections || 10,
    bindDN:          options.bindDN,
    bindCredentials: options.bindCredentials,
    tlsOptions:      options.tlsOptions,
    reconnect:       options.reconnect,
    timeout:         options.timeout,
    connectTimeout:  options.connectTimeout,
    idleTimeout:     options.idleTimeout
  });

  this._client.on('error', function(e){
    // Suppress logging of ECONNRESET if ldapjs's Client will automatically reconnect.
    if (e.errno === 'ECONNRESET' && self._client.reconnect) return;

    console.log('LDAP connection error:', e);
  });

  if (options.client) {
    this.clientConnected = true;
    return;
  }

  this._queue = [];
  var self = this;
  this._client.bind(options.bindDN, options.bindCredentials, function(err) {
    if(err){
        return console.log("Error binding to LDAP", 'dn: ' + err.dn + '\n code: ' + err.code + '\n message: ' + err.message);
    }
    self.clientConnected = true;
    self._queue.forEach(function (cb) { cb(); });
  });
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.passport-windowsauth.LdapLookup.prototype"></a>[module passport-windowsauth.LdapLookup.prototype](#apidoc.module.passport-windowsauth.LdapLookup.prototype)

#### <a name="apidoc.element.passport-windowsauth.LdapLookup.prototype.search"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.LdapLookup.prototype.</span>search (username, callback)](#apidoc.element.passport-windowsauth.LdapLookup.prototype.search)
- description and source-code
```javascript
search = function (username, callback) {
  var self = this;
  function exec(){
    var opts = {
      scope: 'sub',
      filter: self._search_query.replace(/\{0\}/ig, username)
    };
    self._client.search(self._options.base, opts, function(err, res){
      var entries = [];
      res.on('searchEntry', function(entry) {
        entries.push(entry);
      });
      res.on('error', function(err) {
        callback(err);
      });
      res.on('end', function() {
        if(entries.length === 0) return callback(null, null);
        callback(null, entries[0].object);
      });
    });
  }

  if(this.clientConnected){
    exec();
  } else {
    this._queue.push(exec);
  }
}
```
- example usage
```shell
...
LdapLookup.prototype.search = function (username, callback) {
var self = this;
function exec(){
  var opts = {
    scope: 'sub',
    filter: self._search_query.replace(/\{0\}/ig, username)
  };
  self._client.search(self._options.base, opts, function(err, res){
    var entries = [];
    res.on('searchEntry', function(entry) {
      entries.push(entry);
    });
    res.on('error', function(err) {
      callback(err);
    });
...
```



# <a name="apidoc.module.passport-windowsauth.LdapValidator"></a>[module passport-windowsauth.LdapValidator](#apidoc.module.passport-windowsauth.LdapValidator)

#### <a name="apidoc.element.passport-windowsauth.LdapValidator.LdapValidator"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.</span>LdapValidator (options)](#apidoc.element.passport-windowsauth.LdapValidator.LdapValidator)
- description and source-code
```javascript
LdapValidator = function (options){
  this._options = options;
  this._lookup = new LdapLookup(options);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.passport-windowsauth.LdapValidator.prototype"></a>[module passport-windowsauth.LdapValidator.prototype](#apidoc.module.passport-windowsauth.LdapValidator.prototype)

#### <a name="apidoc.element.passport-windowsauth.LdapValidator.prototype.validate"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.LdapValidator.prototype.</span>validate (username, password, callback)](#apidoc.element.passport-windowsauth.LdapValidator.prototype.validate)
- description and source-code
```javascript
validate = function (username, password, callback) {
  if (!username) {
    return callback();
  }

  //lookup by username
  this._lookup.search(username, function (err, up) {
    if(err) return callback(err);
    if(!up) return callback();

    // AD will bind and delay an error till later if no password is given
    if(password === '') return callback();

    var client = this._options.binder || ldap.createClient({
      url:             this._options.url,
      maxConnections:  this._options.maxConnections || 10,
      bindDN:          this._options.bindDN,
      bindCredentials: this._options.bindCredentials,
      tlsOptions:      this._options.tlsOptions,
      reconnect:       this._options.reconnect,
      timeout:         this._options.timeout,
      connectTimeout:  this._options.connectTimeout,
      idleTimeout:     this._options.idleTimeout
    });

    client.on('error', function(e){
        console.log("Error in LdapValidator", e);
    })
    //try bind by password
    client.bind(up.dn, password, function(err) {
      if (!this._options.binder) client.destroy();
      if(err) return callback();
      callback(null, up);
    }.bind(this));
  }.bind(this));
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.passport-windowsauth.super_"></a>[module passport-windowsauth.super_](#apidoc.module.passport-windowsauth.super_)

#### <a name="apidoc.element.passport-windowsauth.super_.super_"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.</span>super_ ()](#apidoc.element.passport-windowsauth.super_.super_)
- description and source-code
```javascript
function Strategy() {
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.passport-windowsauth.super_.prototype"></a>[module passport-windowsauth.super_.prototype](#apidoc.module.passport-windowsauth.super_.prototype)

#### <a name="apidoc.element.passport-windowsauth.super_.prototype.authenticate"></a>[function <span class="apidocSignatureSpan">passport-windowsauth.super_.prototype.</span>authenticate (req, options)](#apidoc.element.passport-windowsauth.super_.prototype.authenticate)
- description and source-code
```javascript
authenticate = function (req, options) {
  throw new Error('Strategy#authenticate must be overridden by subclass');
}
```
- example usage
```shell
...

NOTE: in this case profile only has '''displayName''' and '''id''', both containing just the logon name.

Then use the strategy in a route as follows:

~~~javascript
app.get('/express-passport',
  passport.authenticate('WindowsAuthentication'),
  function (req, res){
    res.json(req.user);
  });
~~~

## Integrated Authentication with Apache and mod_auth_kerb
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
