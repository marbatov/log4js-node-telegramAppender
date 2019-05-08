# TelegramAppender - for [log4js-node](https://github.com/log4js-node/log4js-node)

Pre-requisites:
* registered a telegram bot
* telegram bot token
* put the bot in a chat group
* chat id of the group
* reference: [Telegram Bot API](https://core.telegram.org/bots/api)


Install peer dependency log4js:
```
npm install --save log4js
```

Install log4js-node-telegramAppender:
```
npm install --save "https://github.com/marbatov/log4js-node-telegramAppender/tarball/master"
```

Sample usage:
```
'use strict';

const log4js = require("log4js");
log4js.configure({
    appenders: {
        colouredConsole: { type: 'stdout' },
        telegramAlert: {
            type: 'log4js-node-telegramAppender',
            silentAlertLevel: 'info',
            audioAlertLevel: 'error',
            bottoken: <token>,
            botchatid: <chatid>,
            proxy: <proxyURL>
        }
    },
    categories: { default: { appenders: ['colouredConsole', 'telegramAlert'], level: 'debug' } }
})

var logger = log4js.getLogger("TEST");

logger.debug(`This logs to console only`);
logger.info(`This logs to console and telegram, without telegram notification sound`);
logger.error(`This logs to console and telegram, with telegram notification sound`);
```