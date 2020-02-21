# discord-tts
Node.js module to make your discord bot talk



# Quick Example
```js
const secret = require("./secret.json"); //file with your bot credentials/token/etc
const discord = require("discord.js");
const discordTTS=require("discord-tts");
const client = new discord.Client();
client.login(secret.token);

client.on("ready",()=>{
    console.log("Online");
});

client.on("message",msg=>{
    if(msg.content==="say test 123"){
        const broadcast = client.createVoiceBroadcast();
        var channelId=msg.member.voiceChannelID;
        var channel=client.channels.get(channelId);
        channel.join().then(connection => {
            broadcast.playStream(discordTTS.getVoiceStream("test 123"));
            const dispatcher=connection.playBroadcast(broadcast);
        });
    }
});
```

# Tested working with:
    OS Windows 10
    Node.js v8.3.0
    discord.js v11.4.0
    ffmpeg v0.0.4
    ffmpeg-binaries v3.2.2-3
    opusscript v0.0.7


## Contributing
* Have [Git](https://git-scm.com/) Installed
* Have [Node.js](https://nodejs.org/en/) Installed

```bash
$ git clone https://github.com/mundoex/discord-bot-express
$ npm install
```
Make a pull request with your changes <br>
Contributions, features request or any other kind of help are very welcome :)

## License
[MIT](LICENSE)