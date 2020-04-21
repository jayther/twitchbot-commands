<!-- omit in toc -->
Nightbot commands
=================

Commands cheatsheet

- [8 Ball](#8-ball)
- [Coin Flip (random)](#coin-flip-random)
- [Random with emote](#random-with-emote)
- [Pick from comma-delimited query](#pick-from-comma-delimited-query)
- [Win Counter with reset](#win-counter-with-reset)
- [Shoutout that allows "@" prefix](#shoutout-that-allows-%22%22-prefix)
- [Current time](#current-time)

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

`!commands add !time It's $(time America/Los_Angeles "h:mm a z") for $(channel)`.

Note: Replace `America/Los_Angeles` with your own timezone ID from [Nightbot's Timezones](https://docs.nightbot.tv/commands/variables/time#timezones).

Example:

> jayther: !time
> 
> Nightbot: It's 6:00 pm PDT for jayther
