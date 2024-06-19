# New users guide

## New to IRC

Internet Relay Chat was created in 1988 and has hardly changed. It can be used to exchange text messages (one message = single line) with other people, either privately (called query, PM, private message, MSG) or in a room (channel). Pictures are shared by uploading them to a temporary host like https://pomf.lain.la/ and then pasting the HTTP links. Code snippets or longer texts are shared by pasting them to a Pastebin like https://paste.opensuse.org/ and then sharing the HTTP link.

IRC does not have message history. You can only receive replies while your computer is turned on and connected to the channel you want to follow. Some people run their IRC programs on remote servers for that reason.

IRC is organised into networks. Each network consists of many servers. It (mostly) does not matter which server you connect to as long as it belongs to the network you want to use. Irssi supports connections to many networks at the same time.

Each network contains many channels, rooms that are often dedicated to discussing a specific topic. You can find many channels on https://netsplit.de/ or using a search engine with the keyword "IRC". Irssi supports joining many channels at the same time.

There is a rather large IRC network catering to free and open-source software and peer directed projects at https://libera.chat/ and a smaller one at https://www.oftc.net/ -- many free software projects still have support channels on these IRC networks (although some have moved to Matrix or proprietary platforms like Discord).

Please note that by default, when you join a channel, everyone in the channel can see your IP address. One way of avoiding this is to use a cloak. Not all networks support cloaks and there are other ways of avoiding exposing your IP address to everyone in the same channel as you. You can look at the guide for [libera](https://libera.chat/guides/cloaks) and [OFTC](https://www.oftc.net/UserCloaks/) to see how to do that on each network respectively.

## First start

After (compiling and) installing Irssi, to start it, open a shell (Terminal) and type:

```
irssi
```

You should be greeted by a blinking cursor behind `[(status)]`. You are now in the status window of Irssi. Window is the Irssi name for what you might nowadays call a "Web browser tab".

If you're confused about what you are seeing on the Irssi screen, you can find an annotated screenshot of it at [](User-interface).

If you want, you can pick a nick name (handle) that will be shown to others reading your messages now, by typing

```
/set nick whatyouwant
```

Each command or message can be sent by pressing Enter. Commands in Irssi start with a `/`. If there is no `/`, then the line that you wrote will be sent as a message to the channel that you have open, for everyone to see.

### Leaving

Type `/quit` to get out of Irssi.

## Connecting to a network

Irssi comes with some predefined networks. You can see the current list of networks by typing

```
/network
```

(the list will be shown in your status window)

To connect to one of the networks in the list, type `/connect networkname`, for example:

```
/connect liberachat
```

You should see several messages scroll by. After a while, you should be connected to the Libera Chat network.

:::{attention}
Irssi version 1.2 or older may be lacking the liberachat network entry. See https://github.com/shabble/irssi-docs/wiki/liberachat for how to add it.
:::

### Nickname registration

Many IRC networks (but not all) offer a way to register a user account. Sometimes (but not on all networks) the account registration also includes reserving a nick for you. *How* to register also differs by network. Some _channels_ only allow users with registered accounts to join them, so it may be very important for you to register a user account.

User accounts are always specific to a network.

For the Libera Chat network, you can find instructions how to register and set up your account with Irssi on https://github.com/shabble/irssi-docs/wiki/liberachat#configure-sasl-automated-log-in

## Joining a channel

Once you are connected to a network, you can join channels by typing `/join #channelname`, for example:

```
/join #irssi
```

Now, a new window will open and you can send messages to the channel.

### Changing windows

You can change between windows using the `Ctrl`+`n` or `Ctrl`+`p` keys, or--if your terminal is configured properly--using `Alt`+`1`, `Alt`+`2`, ... See [](/documentation/help/bind_-list) for a list of all default key bindings.

### Removing clutter

By default, Irssi shows when someone joins or leaves a channel. These messages can waste a lot of lines and obscure the actual chat. To hide them, type

```
/window hidelevel +joins +parts +quits
```

To get them back

```
/window hidelevel -joins -parts -quits
```

If you want to hide them by default, `/set window_default_hidelevel hidden joins parts quits`

## Adding a new network

If you want to join a network that is not there, you first need to find at least one server of that network. Let's say you have found the room [#hackint](https://netsplit.de/channels/details.php?room=%23hackint&net=hackint) on netsplit.de and want to join it. Then you can find that the [server](https://netsplit.de/servers/?net=hackint) is irc.hackint.org, port 6697, SSL (TLS) on. To add it to Irssi, use the commands:

```
/network add hackint
/server add -tls -network hackint irc.hackint.org 6697
```

Then, you can connect to the newly added network with

```
/connect hackint
```

### Multiple networks

If you are connected to multiple networks, you can change which one you are "talking" to (which one to send commands) by using the `Ctrl`+`x` key in the status window.

## On-line help

Most /commands have a help page, you can read it with

```
/help commandname
```

or [on-line](/documentation/help/index).

The settings that can be changed with /SET are described on [](/documentation/settings) -- the settingshelp [script](#about-scripts) can be used to read it from within `/help`

## About Scripts

You can enhance your Irssi by installing scripts. Many Perl scripts written by other Irssi users can be found on https://scripts.irssi.org/

Most of them should be compatible with Irssi 1.4 (but some may not, also see the Full Change log for some incompatible ones)

