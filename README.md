# discord-tts
Node.js module to make your discord bot talk

## Quick Example
```js
const secret = require('./secret.json'); //file with your bot credentials/token/etc
const discord = require('discord.js');
const discordTTS = require('discord-tts');
const client = new discord.Client();
client.login(secret.token);

client.on('ready', () => {
    console.log('Online');
});

client.on('message', msg => {
    if(msg.content === 'say test 123'){
        const broadcast = client.voice.createBroadcast();
        const channelId = msg.member.voice.channelID;
        const channel = client.channels.cache.get(channelId);
        channel.join().then(connection => {
            broadcast.play(discordTTS.getVoiceStream('test 123'));
            const dispatcher = connection.play(broadcast);
        });
    }
});
```

## Tested working with:
    OS Windows 10
    Node.js v12.16.1
    discord.js v^12.2.0
    @discordjs/opus: github:discordjs/opus,
    ffmpeg v0.0.4
    ffmpeg-binaries v3.2.2-3
    opusscript v0.0.7


## Contributing
- Have [Git](https://git-scm.com/) Installed
- Have [Node.js](https://nodejs.org/en/) Installed

```bash
$ git clone https://github.com/mundoex/discord-tts.git
$ npm install
```
Make a pull request with your changes <br>
Contributions, features request or any other kind of help are very welcome :)

## License
[MIT](LICENSE)
