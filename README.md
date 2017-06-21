# Scripts for bots #
Collection of scripts to make the running of certain bots much easier.

The bots these scripts are targeted at are:
  - [FredBoat](https://github.com/Frederikam/FredBoat)
  - [RRogueBot](https://github.com/yrmvgh/rroguebot)
  - [Discord-IRC](https://github.com/reactiflux/discord-irc)

# Requirements # 
  - Linux - due to how PID information is obtained.
  - Bash? - not tested in other shells, may require minimal porting.

# How to run #
After you set up and verified individually each of the above bots, that they run properly, modify the paths present in the script with the corresponding paths present on your system(try sed).

I recommend creating a cronjob ( `crontab -e` ) that starts the `bootbots` script every minute, every hour, etc:

```
* * * * * sh /path/to/bootbots
```

Also, due to how *rroguebot* works, a reset once every 12 hours would be necessary, although I'd do a reboot every 6 hours ( `crontab -e` and keep adding the following ):

```
*  * * * * sh /path/to/bootbots
*  3 * * * sh /path/to/guardbots
*  9 * * * sh /path/to/guardbots
* 15 * * * sh /path/to/guardbots
* 21 * * * sh /path/to/guardbots
```

And all your bots should always be checked if they're running, if not, be started, and your *rroguebot* should be restarted every 6 hours.
