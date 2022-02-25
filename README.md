# [Screenshot bot](https://t.me/WWM_SSGENbot)

> Telegram Bot For Screenshot Generation.

## Description

An attempt to implement the screenshot generation of telegram files without downloading the entire file. Live version can be found here [world wide movies](https://t.me/world_wide_movies "Screenshot Generator Bot").

## Installation Guide

### Prerequisites

* FFmpeg.
* Python3 (3.6 or higher).

### Local setup

> The setup given here is for a linux environment (Debian/Ubuntu).



* Create and activate virtual environment.

```
$ python3 -m venv venv
$ source venv/bin/activate
```

* Install dependencies.

```
$ pip3 install -U -r requirements.txt
```

### Environment Variables

Properly setup the environment variables or populate `config.py` with the values. Setting up environment variables is advised as some of the values are sensitive data, and should be kept secret.

* `API_ID`(required) - Get your telegram API_ID from [https://my.telegram.org/](https://my.telegram.org/).
* `API_HASH`(required) - Get your telegram API_HASH from [https://my.telegram.org/](https://my.telegram.org/).
* `BOT_TOKEN`(required) - Obtain your bot token from [Bot Father](https://t.me/BotFather "Bot Father").
* `LOG_CHANNEL`(required) - Log channel's id.
* `DATABASE_URL`(required) - Mongodb database URI.
* `AUTH_USERS`(required) - Admin(s) of the bot. User's telegram id separated by space. Atleast one id should be specified.
* `HOST`(required) - Public URL of file streaming service ([See Setting up Streaming Service](#setting-up-streaming-service)).
* `SESSION_NAME`(optional) - Name you want to call your bot's session, Eg: bot's username.
* `MAX_PROCESSES_PER_USER`(optional) - Number of parallel processes each user can have, defaults to 2.
* `MAX_TRIM_DURATION`(optional) - Maximum allowed video trim duration in seconds. Defaults to 600s.
* `TRACK_CHANNEL`(optional) - User activity tracking channel's id. Only needed if you want to track and block any user. Disabled by default.
* `SLOW_SPEED_DELAY`(optional) - Delay required between each interaction from users in seconds. Defaults to 5s.
* `TIMEOUT` (optional) - Maximum time alloted to each process in seconds, after which process will be cancelled. Defaults to 1800s(30 mins).
* `DEBUG` (optional) - Set some value to use DEBUG logging level. INFO by default.
* `IAM_HEADER` (optional) - Authentication token for streaming service. Defaults to `''`.
* `WORKER_COUNT` (optional) - Number of process to be handled at a time. Defaults to `20`.

### Run bot

`$ python3 -m bot`

Now go and `/start` the bot. If everything went right, bot will respond with welcome message.


## Supported commands and functions

### Commands

**General commands**

* `/start` - Command to start bot or check whether bot is alive.
* `/settings` - Command to configure bot's behavior'
* `/set_watermark` - Command to add custom watermark text to screenshots. Usage: `/set_watermark watermark_text`.

**Admin commands**

> Any user specified in `AUTH_USERS` can use these commands.

* `/status` - Returns number of total users.
* `/ban_user` - Command to ban any user. Usage: `/ban_user user_id ban_duration ban_reason`. `user_id` - telegram id of the user, `ban_duration` - ban duration in days, `ban_reason` - reason for ban. All 3 parameters are required.
* `/unban_user` - Command to unban any banned user. Usage: `/unban_user user_id`. `user_id` - telegram id of the user. The parameter is required.
* `/banned_users` - Command to view all banned users. Usage: `/banned_users`. This takes no parameters.
* `/broadcast` - Command to broadcast some message to all users. Usage: reply `/broadcast` to the message you want to broadcast.

### Functions
* `Screenshot Generation` - Generates screenshots from telegram video files or streaming links. Number of screenshots range from 2-10.
* `Sample Video Generation` - Generates sample video from telegram video files or streaming links. Video duration range from 30s to 150s. Configurable in `/settings`.
* `Video Trimming` - Trims any telegram video files or streaming links.

### Settings
In bot settings.
* `Upload Mode` - Screenshot upload mode. Either `as image file` or `as document file`. Defaults to `as image file`.
* `Watermark` - Watermark text to be embedded to screenshots. Texts upto 30 characters supported. Disabled by default.
* `Watermark Color` - Font color to be used for watermark. Any of `white`, `black`, `red`, `blue`, `green`, `yellow`, `orange`, `purple`, `brown`, `gold`, `silver`, `pink`. Defaults to `white`.
* `Watermark Font Size` - Font size to be used for watermarks. Any of `small(30)`, `medium(40)`, `large(50)`. Defaults to `medium`.
* `Watermark Position` - Watermark text's position. Defaults to `bottom left`.
* `Sample Video Duration` - Sample video's duration. Any of `30s`, `60s`, `90s`, `120s`, `150s`. Defaults to `30s`.
* `Screenshot Genetation Mode` - Either `random` or `equally spaced`. Defaults to `equally spaced`.


 

## Dependencies
* pyrogram
* tgcrypto
* motor
* dnspython
* async-timeout
* aiohttp


## License
Code released under [The GNU General Public License](LICENSE).
