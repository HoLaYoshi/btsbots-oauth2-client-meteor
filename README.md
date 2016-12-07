# Meteor BTSBots OAuth2 client
Used in conjunction with meteor-oauth2-server on the the target server, this
package will allow your site to authenticate users on another meteor application.

## Usage

### Configuration

1. register a new client from https://btsbots.com.
  * import account to https://btsbots.com with your BTS's active private key.
  * login.
  * register a new client. open the develop console of your browser, run command: 
 ```
> addclient("https://btsbots.com:8000/_oauth/BTSBotsOAuth", 'abcdefg')
 ```
  the first parameter is the redirect URL, the second parameter is the secret for your client.
  your client's ID will output after the command, suppose it's 123456. you'll need the ID and secret in the next step.

2. add Meteor BTSBots OAuth2 to your web site.
  * add this package to your meteor project
 ```
$ mkdir packages && cd packages
$ git clone https://github.com/pch957/btsbots-oauth2-client-meteor
$ meteor add accounts-ui prime8consulting:meteor-oauth2-client
 ```
  * configure OAuth2 with the client ID and secret. open mongo client, and use the app database.run command:
```
meteor:PRIMARY> db.meteor_accounts_loginServiceConfiguration.insert({"service" : "BTSBotsOAuth", "clientId" : "123456", "secret" : "abcdefg", "baseUrl" : "https://btsbots.com", "loginUrl" : "https://btsbots.com/oauthlogin", "loginStyle" : "popup"})
```
