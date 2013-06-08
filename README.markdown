This package enables users of your [Yesod](http://www.yesodweb.com) site to authenticate users using the [XING
API](https://dev.xing.com).

It's currently under development and is **not** considered **stable**.
This library is a private project and isn't associated with XING AG.

# Usage

Assuming that your [foundation datatype](http://www.yesodweb.com/book/basics) is named `YourSite`
your configuration might look like this:

```haskell
instance YesodAuth YourSite where
  type AuthId XINGAuth = Text
  getAuthId creds = return $ lookup "oauth_token" (credsExtra creds)
  loginDest _     = RootR
  logoutDest _    = RootR
  authPlugins _   = [xingAuth (oauthConsumerKey "YOUR_CONSUMER_KEY") (oauthConsumerSecret "YOUR_CONSUMER_SECRET")]
  authHttpManager = httpManager
```

The repository contains [an example](demos/yesod-auth.hs) that demonstrates the whole workflow.
