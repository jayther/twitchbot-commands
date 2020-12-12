<!-- omit in toc -->
Twitch Bot Custom Commands
==========================

Commands cheatsheet

- [Nightbot](#nightbot)
  - [8 Ball](#8-ball)
  - [Coin Flip (random)](#coin-flip-random)
  - [Random with emote](#random-with-emote)
  - [Pick from comma-delimited query](#pick-from-comma-delimited-query)
  - [Win Counter with reset](#win-counter-with-reset)
  - [Shoutout that allows "@" prefix](#shoutout-that-allows--prefix)
  - [Current time](#current-time)
  - [Slap random person](#slap-random-person)
  - [Repeat word a random number of times](#repeat-word-a-random-number-of-times)
  - [User levels](#user-levels)
- [Stream Elements (chat bot)](#stream-elements-chat-bot)
  - [8-ball (custom, with default 8-ball disabled)](#8-ball-custom-with-default-8-ball-disabled)
  - [Coinflip](#coinflip)
  - [Random with emote](#random-with-emote-1)
  - [Win Counter](#win-counter)
  - [Shoutout](#shoutout)
  - [Current time](#current-time-1)
  - [Slap random person](#slap-random-person-1)
  - [Repeat word random number of times](#repeat-word-random-number-of-times)
  - [User levels](#user-levels-1)
- [Streamlabs Cloudbot](#streamlabs-cloudbot)
  - [](#)
  
# Nightbot

Important commands:

* `!commands add [command]`
* `!commands edit [command]`
  * `!commands edit -cd=5`: Change cooldown to 5 seconds (minimum is 5 seconds)
* `!commands remove [command]`

## 8 Ball

`!commands add !8ball @$(user) , 🎱 $(eval const responses = ['All signs point to yes...', 'Yes!', 'My sources say nope.', 'You may rely on it.', 'Concentrate and ask again...', 'Outlook not so good...', 'It is decidedly so!', 'Better not tell you.', 'Very doubtful.', 'Yes - Definitely!', 'It is certain!', 'Most likely.', 'Ask again later.', 'No!', 'Outlook good.', 'Don\'t count on it.']; responses[Math.floor(Math.random() * responses.length)];)`

Example:

> jayther: !8ball Will I finish this readme?
> 
> Nightbot: @jayther , 🎱 All signs point to yes...

## Coin Flip (random)

`!commands add !coinflip @$(user), you got $(eval ['Kappa Heads','Squid4 Tails'][Math.floor(Math.random()*2)]).`

Example:

> jayther: !coinflip Heads I will finish this readme today.
> 
> Nightbot: @jayther , you got Kappa Heads.

## Random with emote

`!commands add !fix $(eval ['Unable to comply, building in progress.','Cannot build here.','Insufficient Funds','Cannot deploy here','Unit lost'][Math.floor(Math.random()*5)] + ' ' + ['MrDestructoid','Kappa','SSSsss','BloodTrail','SMOrc'][Math.floor(Math.random()*5)])`

Example:

> jayther: !fix
> 
> Nightbot: Unable to comply, building in progress. MrDestructoid

## Pick from comma-delimited query

`!commands add !pick @$(user) , I pick $(eval const a='$(query)'.split(','); a[Math.floor(Math.random()*a.length)]).`

Example:

> jayther: !pick me, myself, I
> 
> Nightbot: I pick me.

## Win Counter with reset

* `!commands add !wins 0 wins.`
* `!commands add !addwin -a=!commands edit !wins $(count) wins.`
* `!commands add !resetwins -a=!commands edit !addwin \-c=-1`

Example:

> jayther: !wins
> 
> Nightbot: 2 wins.

> jayther: !addwin
>
> Nightbot: The command "!wins" has been edited successfully.
> 
> jayther: !wins
> 
> Nightbot: 3 wins.

Note: You will need to run `!resetwins` and then `!addwin` to reset the win counter to 0, since `!resetwins` does not update `!wins`.

Example:

> jayther: !resetwins
>
> Nightbot: The command "!addwin" has been edited successfully.
>
> jayther: !addwin
>
> Nightbot: The command "!wins" has been edited successfully.
>
> jayther: !wins
>
> Nightbot: 0 wins.

## Shoutout that allows "@" prefix

`!commands add !so Check out $(twitch $(eval '$(touser)'.replace('@','')) "{{displayName}} at {{url}} ! Last seen playing {{game}}")`

Example:

> jayther: !so jayther
> 
> Nightbot: Check out jayther at https://twitch.tv/jayther ! Last seen playing Science & Technology

## Current time

`!commands add !time It's $(time America/Los_Angeles "h:mm a z") for $(channel)`

Note: Replace `America/Los_Angeles` with your own timezone ID from [Nightbot's Timezones](https://docs.nightbot.tv/commands/variables/time#timezones).

Example:

> jayther: !time
> 
> Nightbot: It's 6:00 pm PDT for jayther

## Slap random person

`!commands add !slap $(user) has slapped $(urlfetch https://2g.be/twitch/randomviewer.php?channel=$(channel))`

Example:

> jayther: !slap
> 
> Nightbot: jayther has slapped uwu_twanswator

## Repeat word a random number of times

`!commands add !boom $(eval 'boom'.repeat(Math.floor(Math.random()*8) + 1))`

Example:

> jayther: !boom
>
> Nightbot: boom boom boom boom

Note: Range is 1-9 (0-8 plus 1).

## User levels

Set minimum user level for a command.

`!commands edit ![name] -ul=[level]`

`name`: Command name

`level`: Minimum level

**Levels**:

* Owner: `owner`
* Mod: `moderator`
* Regular: `regular`
* Sub: `subscriber`
* Everyone: `everyone`

# Stream Elements (chat bot)

## 8-ball (custom, with default 8-ball disabled)

`!command add !8ball @${sender} , 🎱 ${random.pick 'All signs point to yes...' 'Yes!', 'My sources say nope.' 'You may rely on it.' 'Concentrate and ask again...' 'Outlook not so good...' 'It is decidedly so!' 'Better not tell you.' 'Very doubtful.' 'Yes - Definitely!' 'It is certain!' 'Most likely.' 'Ask again later.' 'No!' 'Outlook good.' 'Don\'t count on it.'}`

Example:

> jayther: Will I finish this readme?
> 
> StreamElements: @jayther, 🎱 Better not tell you.

## Coinflip

`!command add !coinflip @${sender} , you got ${random.pick 'Kappa Heads' 'Squid4 Tails'}`

Example:

> jayther: !coinflip
> 
> StreamElements: @jayther , you got Kappa Heads

## Random with emote

`!command add !fix ${random.pick 'Unable to comply, building in progress.' 'Cannot build here.' 'Insufficient Funds' 'Cannot deploy here' 'Unit lost'} ${random.emote}`

Example:

> jayther: !fix
> 
> StreamElements: Unit lost SMOrc

## Win Counter

`!command add !wins ${channel} has won ${getcount wins} times!`

`!command add !addwin ${channel} has won ${count wins +1} times!`

`!command add !resetwins ${channel} has won ${count wins 0} times!`

`!command add !setwins ${channel} has won ${count wins ${1}} times!`

Example:

> jayther: !wins
>
> StreamElements: jayther has won 2 times!
>
> jayther: !addwin
>
> StreamElements: jayther has won 3 times!
>
> jayther: !resetwins
>
> StreamElements: jayther has won 0 times!
>
> jayther: !setwins 20
>
> StreamElements: jayther has won 20 times!

## Shoutout

`!command add !so Check out ${user ${1}} at https://twitch.tv/${channel ${1}} ! Last seen playing ${game ${1}}`

Example:

> jayther: !so jayther
> 
> StreamElements: Checkout jayther at https://twitch.tv/jayther ! Last seen playing Science & Technology

## Current time

`!command add !time It is currently ${time.PST} for ${channel}.`

Example:

> jayther: !time
>
> StreamElements: It is currently 1:52 for jayther.

## Slap random person

`!command add !slap ${user} has slapped ${random.chatter}`

Example:

> jayther: !slap
>
> StreamElements: jayther has slapped uwu_twanswator

## Repeat word random number of times

`!command add !boom ${repeat ${random.1-9} 'boom'}`

Example:

> jayther: !boom
> 
> StreamElements: boom boom boom boom

## User levels

Set minimum user level for commands.

`!command options ![name] -level [amt]`

`name`: Command Name

`amt`: Level

**Levels**:

* Everyone: 100
* Subs: 250
* Regular: 300
* Mod: 500
* Supermod: 1000
* Broadcaster: 1500


# Streamlabs Cloudbot

##  
