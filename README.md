`nlug_matterbot` is a bot powered by [matterbridge](https://github.com/42wim/matterbridge). You can find it idling on our Discrod, IRC, and Telegram channels.

## Config

Replace `<IRC_PASSWORD>`, `<DISCORD_TOKEN>` and `<TELEGRAM_TOKEN>` with the appropriate values:

```toml
# nairobilug.toml

[irc.nairobilug]
Server="irc.libera.chat:6697"
UseTLS=true
UseSASL=true
NickServNick="nlug_matterbot"
NickServPassword="<IRC_PASSWORD>"
Nick="nlug_matterbot"
RemoteNickFormat="[{PROTOCOL}] <{NICK}> "

[discord.nairobilug]
Token="<DISCORD_TOKEN>"
Server="535134719092850719"  # the discord server
RemoteNickFormat="[{PROTOCOL}] <{NICK}> "

[telegram.nairobilug]
Token="<TELEGRAM_TOKEN>"
RemoteNickFormat="[{PROTOCOL}] <{NICK}> "

[[gateway]]
name="gateway0"
enable=true

[[gateway.inout]]
account="irc.nairobilug"
channel="#nairobilug"  # the irc channel

[[gateway.inout]]
account="discord.nairobilug"
channel="general"

[[gateway.inout]]
account="telegram.nairobilug"
channel="-1001090406917"  # the telegram group
```

## Usage

```shell
matterbridge -conf ./nairobilug.toml
```

### Docker

```shell
docker run --name matterbridge -v ./nairobilug.toml:/etc/matterbridge/matterbridge.toml:ro docker.io/42wim/matterbridge:latest
```
