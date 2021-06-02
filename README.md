<h1 align="center">
  <img src="https://imgur.com/uyG2o2l.png" alt="nlug_matterbot">
</h1>

`nlug_matterbot` is powered by **matterbridge** - a simple chat bridge. More information on the [project page](https://github.com/42wim/matterbridge).

## Config

Replace `<DISCORD_TOKEN>` and `<TELEGRAM_TOKEN>` with the appropriate values, per the [matterbridge documentation](https://github.com/42wim/matterbridge/wiki/Gateway-config-%28basic%29).

```toml
# nairobilug.toml

# Documentation: https://github.com/42wim/matterbridge/wiki/Settings
#              : https://github.com/42wim/matterbridge/wiki/Gateway-config-%28basic%29

# Nairobi GNU/Linux Users Group

[irc.nairobilug]
Server="irc.freenode.net:6697"
UseTLS=true
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

### Binary

```
matterbridge -conf nairobilug.toml
```

### Docker

```
docker run --name matterbridge -v ./nairobilug.toml:/etc/matterbridge/matterbridge.toml:ro docker.io/42wim/matterbridge:latest
```
