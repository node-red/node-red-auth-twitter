# Node-RED Authentication with Twitter

[Node-RED](https://nodered.org) plugin for authenticating users with Twitter.

This modules lets you restrict access to the Node-RED editor to specific Twitter
users.

**Note:** this requires Node-RED 0.17 or later


## Install

In your Node-RED user directory, typically `~/.node-red`:

    $ npm install node-red/node-red-auth-twitter

## Usage

### Create a new Twitter application

To enable access control with Twitter, you must first [create a new application
on your Twitter account](https://apps.twitter.com/app/new). While creating the 
application, it's important to fill the _Callback URL_ field with a valid URL.
It does not need to be a "real" URL, you can use `http://example.com` or
`https://placeholder.com`.

Once created, you will be provided a _Consumer Key_ and _Consumer Secret_ that
you will need to use to configure the authentication plugin.

### Configure `adminAuth`

Access control for the Node-RED editor is configured in your `settings.js` file
using the `adminAuth` property.

    adminAuth: require('node-red-auth-twitter')({
        consumerKey: TWITTER_CONSUMER_KEY,
        consumerSecret: TWITTER_CONSUMER_SECRET,
        baseURL: "http://localhost:1880/",
        users: [
           { username: "knolleary",permissions: ["*"]}
        ]
    })

The `baseURL` property is the URL used to access the Node-RED editor.

The `users` property is the list of Twitter users who are allowed to access the
editor. It is the same as used by `adminAuth` as described in the [security documentation](http://nodered.org/docs/security), but without the `password` property.

A default user can be specified by adding a `default` property to the options object:

        users: [
           ...
        ],
        default: {
            permissions: "read"
        }

## Copyright and license

Copyright JS Foundation and other contributors, http://js.foundation under [the Apache 2.0 license](LICENSE).
