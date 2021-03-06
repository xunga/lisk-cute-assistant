# Lisk Cute Assistant


![Lisk-Cute-Assistant](https://github.com/xunga/lisk-cute-assistant/blob/master/imgs/lisk-cute-assistant.png?raw=true)

### Lisk Cute Assistant is a bot to manage your Lisk Node remotely from Telegram.

Lisk Cute Assistant enables the node owners to remotely manage it, via telegram. The code is self hosted on the same instance of the lisk node and it configures the telegram bot to only reply to requests only from a given telegram ID.

Since some operations are sensitive, it uses One Time Passwords (OTP) to authenticate the requests.

Lisk-cute-assistant doesn't perform any kind of automatic operation besides checking the health of the node/server. E.g. if your node forks, it will not automatically fix it, but instead it will give you the possibility of rebuilding the node from telegram, after executing the authentication.

## Features

- Lisk Core 1.0.x support
- Block height check, comparing it to other nodes
- Server stats
- Remote rebuild from snapshot server
- Logs tailing & logs grep
- Minute by minute cronjobs to check the node health
- Authentication of requests via OTP (e.g. 2FA passwords from Google Authenticator) for sensitive tasks such as the rebuild
- SMS notifications
- Slack integration via webhooks
- Genertic Webhooks integration (e.g. IFTTT)
- Check if the node is forging
- Network speedtest

## How to run

[Please follow the](https://github.com/xunga/lisk-cute-assistant/blob/master/INSTALL.md) `INSTALL.md` [file](https://github.com/xunga/lisk-cute-assistant/blob/master/INSTALL.md)

## How to migrate from Lisk-Cute-Assistant 1.0 to Lisk-Cute-Assistant 2.0 (aka Lisk Core 1.0 support)

[Please follow the](https://github.com/xunga/lisk-cute-assistant/blob/master/MIGRATION.md) `MIGRATION.md` [file](https://github.com/xunga/lisk-cute-assistant/blob/master/MIGRATION.md)


## Functionalities

### Block Heights

It tests your blockheight against the other nodes configured in the `config.js` file

### Server status

Returns the CPU/RAM usage, available space, the lisk process status and a speedtest to check the network speed.

### Rebuild from snapshot

It rebuilds the node via the command `bash lisk.sh rebuild -u ${selected_snapshot_server_URL} -f latest.gz`

### Get logs

Opens a new keyboard that enables to: 
- Tail the logs. Yes it opens a stream from your log file with your chat. It batches the logs and sends them every second
- Get recent logs. A single message sent once, with your last logs (tail -n 3000)
- Grep of logs. You can grep the following:
 - Forks cause 1
 - Forks cause 2
 - Forks cause 3
 - Forks cause 5
 - All forks
 - Forged blocks
 - SIGKILL
 - SIGABRT
 - "Consensus"

### SMS integration

You can receive SMSs when something wrong happens. There are two providers available: Textmagic and Twilio. Fill the `textMagicData` and/or `twilioData`  variables in the config.js in order to enable SMS messages.

### Slack webhooks

Fill the `slackWebhook` variable in the config.js in order to enable messages via slack. You can get the needed data for the configuration by adding an `Incoming WebHook` integration in the settings of you Slack's workspace.


### Webhook events

Lisk-cute-assistant can run webhooks to services like IFTTT. It will pass the `eventName` and as payload `value_1` the name of the node from the config.js (`nodeName` variable).

The available events are:
- lca_forging_switched_off
- lca_blockheights_missmatch
- lca_high_cpu_usage
- lca_high_ram_usage
- lca_high_disk_usage
- lca_low_speed_error
- lca_no_local_blockheight


## Security

The bot is programmed in a way that it only replies to your requests. For certain tasks like the rebuild flow, it requests a [One Time Password](https://en.wikipedia.org/wiki/One-time_password) in order to perform the action.

## Screenshots
<img src="https://github.com/xunga/lisk-cute-assistant/blob/master/imgs/screen0.jpg?raw=true" data-canonical-src="https://github.com/xunga/lisk-cute-assistant/blob/master/imgs/screen0.jpg?raw=true" width="400" />   <img src="https://github.com/xunga/lisk-cute-assistant/blob/master/imgs/screen1.jpg?raw=true" data-canonical-src="https://github.com/xunga/lisk-cute-assistant/blob/master/imgs/screen1.jpg?raw=true" width="400" />


### Challenges that would be nice to discusss
- External heartbeat check
- Improve the snapshot rebuild possibilities (add other snapshot servers)
- Feature to check new bot version

### Contributors
- Carbonara
- TonyT908 for the SMS integration
- Alepop for the bugfixes

### Disclaimer

By using this software you accept the terms and conditions. This software is provided "as is", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. in no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the software.

# Built with ❤️ by [Carbonara](lisk://main/voting/vote?votes=carbonara) and [Lisk Elite](http://liskelite.com)
