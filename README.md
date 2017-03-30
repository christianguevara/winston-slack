# winston-slack

Winston Transport for Slack chat integration

`$ npm install winston-slack`

Also requires install of winston

`$ npm install winston`


Basic transport that works just like all other winston transports. Sends logged messages to a specified slack chat channel

additonal options:

`domain:` sub-domain of the slack instance 

`apiToken:` a Slack incoming webhook token (see. https://api.slack.com/)

`username:` name displayed in the chat channel. default "winston-slack"

## Example

Adding winston-slack to winston main module.

<code>

    var winston = require('winston');
    var slack = require('winston-slack').Slack;

    winston.add(slack, {
        domain: "yourcompany",
        apiToken: "j7w7tjBMdytjXzEZu9HQooni",
        channel: "#test-channel",
        username: "ErrorBot",
        level: 'error',
        handleExceptions : true
    });
</code>

If you have and array of transports or custom Logger.

<code>

    var winston = require('winston');
    var slack = require('winston-slack').Slack;
    var transports = []

    var slackTransport = new slack({
        domain: 'yourcompany',
        apiToken: 'j7w7tjBMdytjXzEZu9HQooni',
        channel: '#test-channel',
        username: 'ErrorBot',
        level: 'error',
        handleExceptions: true
    });

    transports.push(slackTransport);
    
    var logger = new winston.Logger({
        level: 'debug',
        transports: transports
    });
</code>
