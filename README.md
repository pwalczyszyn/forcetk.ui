## Description
**forcetk.ui** is an extension for [forcetk.js](https://github.com/developerforce/Force.com-JavaScript-REST-Toolkit) library (from Salesforce team). In a nutshell *forcetk.js* implements client side OAuth mechanizm to connect to force.com REST services. Where **forcetk.ui** provides a simple UI layer when building mobile apps with [PhoneGap](http://phonegap.com)/[Cordova](http://incubator.apache.org/cordova/) and ChildBrowser plugin (available from [here](https://github.com/phonegap/phonegap-plugins) for different platforms). 

For testing and debugging purposes forcetk.ui will also work in a desktop Safari browser, instead of ChildBrowser plugin it will use popup window.

## Usage

To use this library you will need a Salesforce.com account. For development purposes you can signup for a free developer account [here](http://developer.force.com).

Another thing you will need is to enable remote access, this can be done by navigating to Setup > Develop > Remote Access and adding new Remote Access Application configuration.

```html
<!DOCTYPE html>
<html>
<head>
    <title>forcetk.ui demo</title>

    <script type="text/javascript" src="scripts/libs/jquery-1.8.1.js"></script>

    <script type="text/javascript" src="scripts/libs/forcetk.js"></script>
    <script type="text/javascript" src="scripts/libs/forcetk.ui.js"></script>

    <script type="text/javascript">

        function login() {
            // Salesforce login URL
            var loginURL = 'https://login.salesforce.com/',

            // Consumer Key from Setup | Develop | Remote Access
                    consumerKey = 'CONSUMER_KEY',

            // Callback URL from Setup | Develop | Remote Access
                    callbackURL = 'https://login.salesforce.com/services/oauth2/success',

            // Instantiating forcetk ClientUI
                    ftkClientUI = new forcetk.ClientUI(loginURL, consumerKey, callbackURL,
                            function forceOAuthUI_successHandler(forcetkClient) { // successCallback
                                alert('OAuth success!');
                            },

                            function forceOAuthUI_errorHandler(error) { // errorCallback
                                alert('OAuth error!');
                            });

            // Initiating login process
            ftkClientUI.login();
        }

    </script>

</head>
<body>

<button id="btnLogin" onclick="login()">Login</button>

</body>
</html>
```