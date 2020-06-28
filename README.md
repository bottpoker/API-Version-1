# BottPoker Documentation REST API (Version 1)
![BottPoker Version 1](https://i.imgur.com/iHC63YY.png)

**Table of Contents**

- [General Information](#general-information)
    - PHP Development Kit
- [Where can I play?](#where-can-i-play)
- [HTTP Return Codes](#http-return-codes)
- [Error Codes](#error-codes)
- [Endpoint Information](#general-information-on-endpoints)
- System
	- [Endpoints](#endpoints) (system/endpoints)
	- [List Announcements](#list-announcements) (system/list-announcements)
	- [Ping](#ping) (system/ping)
	- [Status](#status) (system/status)
	- [Timestamp](#timestamp) (system/timestamp)
	- [System Version](#system-version) (system/version)
- Tests
	- [Deal Community Cards](#deal-community-cards) (tests/deal-community-cards)
	- [Deal Pockets](#deal-pockets) (tests/deal-pockets)
	- [Tests Deal Full Details](#tests-deal-full-details) (tests/deal-full-details)
- Bot
	- [Bot Debug Log](#bot-debug-log) (bot/debug-log)
	- [Delete Bot](#delete-bot) (bot/delete-bot)
	- [List Bot Profit and Loss (PNL)](#list-bot-profit-and-loss-(pnl)) (bot/list-bot-profitloss)
	- [List My Bots](#list-my-bots) (bot/list-my-bots)
	- [Register Bot](#register-bot) (bot/register-bot)
- Deposit
	- [Deposit List](#deposit-list) (deposit/list)
	- [Request Deposit Address](#request-deposit-address) (deposit/request-deposit-address)
- Game
	- [Game Create Ring Game](#game-create-ring-game) (game/create-ring-game)
	- [Game Create Tournament](#game-create-tournament) (game/create-tournament)
	- [Join Game](#join-game) (game/join)
	- [Leave Game](#leave-game) (game/leave)
	- [List Game Player Actions](#list-game-player-actions) (game/list-game-player-actions)
	- [List Previous Hands](#list-previous-hands) (game/list-previous-hands)
	- [List Table Players](#list-table-players) (game/list-table-players)
	- [Payout Table](#payout-table) (game/payout-table)
	- [Real-time Game Data](#real-time-game-data) (game/realtime)
	- [Sit In](#sit-in) (game/actions/sit-in)
	- [Sit Out](#sit-out) (game/actions/sit-out)
	- [Bet](#bet) (game/actions/bet)
	- [Call](#call) (game/actions/call)
	- [Fold](#fold) (game/actions/fold)
	- [Post Blind](#post-blind) (game/actions/post-blind)
	- [Raise](#raise) (game/actions/raise)
	- [Game Actions](#game-actions) (game/actions/top-up)
	- [All-in](#all-in) (game/actions/allin)
- Public
	- [List Collusions](#list-collusions) (public/collusion-list)
	- [List Collusion Refunds](#list-collusion-refunds) (public/collusion-refunds)
	- [Leaderboards](#leaderboards) (public/leaderboards)
	- [List Ring Games](#list-ring-games) (public/poker/list-ring-games)
	- [List Sit and Go Games](#list-sit-and-go-games) (public/poker/list-sitandgo-games)
	- [List Tournament Games](#list-tournament-games) (public/poker/list-tournament-games)
	- [List Equity Pools](#list-equity-pools) (public/list-equity-pools)
	- [Network Playing Statistics](#network-playing-statistics) (public/network-playing-statistics)
	- [Game Round Speeds](#game-round-speeds) (public/game-round-speeds)
	- [Game Speeds](#game-speeds) (public/game-speeds)
	- [Public Game Types](#public-game-types) (public/game-types)
- User
	- [User Access History](#user-access-history) (user/access-history)
	- [User Active Sessions](#user-active-sessions) (user/active-sessions)
	- [User API Limits](#user-api-limits) (user/api-limits)
	- [Game History](#game-history) (user/game-history)
	- [List Violations](#list-violations) (user/list-violations)
	- [User List Rakebacks](#user-list-rakebacks) (user/list-rakebacks)
	- [User List Rakes Paid](#user-list-rakes-paid) (user/list-rakes-paid)
	- [User Rakeback Level](#user-rakeback-level) (user/rakeback-level)
	- [Active Bots](#active-bots) (user/active-bots)
- Withdraw
	- [Withdraw List](#withdraw-list) (withdraw/list)
	- [Request Withdraw](#request-withdraw) (withdraw/request-withdraw)


# Public REST API Version 1 for BottPoker (private beta)
Bott Poker - Poker for developers and programming enthusiasts, where we embrace programmed and pragmatic bots and pit them against each other.

As part of our dedication to transparency we will consistently add guidelines around how our project manages the important questions such as code of conduct, game engines, collusion and general trust factors. 

Name | Purpose
------------ | ------------
[README.md](./README.md) | Information relating to the project and the REST API (/api/v1)
[ERRORS.md](./ERRORS.md) | All error codes and related meanings
[BOT-RESTRICTIONS.md](./BOT-RESTRICTIONS.md) | A list reminder of prohibited actions
[COLLUSIONS.md](./COLLUSIONS.md) | How we manage users who collude
[CODE-OF-CONDUCT.md](./CODE-OF-CONDUCT.md) | Code of conduct for ourselves, users and bots
[ENGINE-DISCLOSURE.md](./ENGINE-DISCLOSURE.md) | Information about how our core game engine runs for transparency
[PAYOUT-MECHANICS.md](./PAYOUT-MECHANICS.md) | Information on how the payouts for `SNG` and `TRN` game types are calculated
[RAISING-GUIDELINES.md](./RAISING-GUIDELINES.md) | Information on how the engine deals with users raising

## General Information

* There are  **`56 endpoints`**.
* Version 1 is currently in beta mode, which is invite only.
* The base endpoint is: **api.bottpoker.com**
* All endpoints return only a JSON object.
* Data returned is limited by default to 10 rows and page 1 in descending order (newest first).
* Timestamp fields vary and are labeled to their corresponding contents of **milliseconds** or **time**

#### PHP Development Kit
A PHP development kit is available [here](https://github.com/bottpoker/PHP-Poker-Bot). Full examples and endpoints exist to make development easy. In the near future functiong bots will be added to this setup.

## Where can I play?
The BottPoker API is exclusively for usage on [bottpoker.com](https://bottpoker.com/). You cannot create poker bots with this API that will play on other webites such as pokerstars

Website | Bot Works
------------ | ------------
BottPoker.com | :radio_button:
PokerStars Poker Bot | :white_circle:
Ignition Poker Bot | :white_circle:
Intertops Poker Bot | :white_circle:
Bovada Poker Bot | :white_circle:
BetOnline Poker Bot | :white_circle:
888 Poker Bot | :white_circle:
Party Poker Bot | :white_circle:
Unibet Poker Bot | :white_circle:
Pacific Poker Bot | :white_circle:
Odds Poker Bot | :white_circle:
Carbon Poker Bot | :white_circle:

There are **zero** plans for any expansion of the poker bot to work on any of the sites in the table. BottPoker is built for play on BottPoker.com where we embrace and invite talented developers to make winning poker bots that can compete against other developers bots.

## HTTP Return Codes

* HTTP `4XX` return codes are used for malformed requests where the issue exists with the sender.
* HTTP `404` return code indicates the endpoint doesn't exist.
* HTTP `422` return code is applied when a user input is unexpected.
* HTTP `429` return code is used when breaking a request rate limit.
* HTTP `418` return code is used when an IP has been banned for continious requests and violating policy.
* HTTP `5XX` return codes are used for internal errors from BottPoker. The end user is not at fault and cannot influence a fix.

## Error Codes
* Any endpoint has the ability to return an ERROR

Sample Payload below:
```javascript

"data": {
  "code": 'xxx',
  "error": "Missing POST parameter(s) required to proceed, review 'missing_parameters' for more information."
},
   
```

* We provide a run down of [Errors Codes](./ERRORS.md) used within the Bott Poker API.

## General Information on Endpoints
* For `POST` endpoints, the parameters must be sent as a `query string` or in the `request body`.
* For `GET` endpoints, parameters must be sent as a `query string`.
* If a parameter sent in both the `query string` and `request body`, the `query string` parameter will take priority.
* Parameters may be sent in any order.

## Endpoints
All system endpoints which are available to use within Bott Poker.

```
GET /api/v1/system/endpoints
```

**Parameters:**
None

## List Announcements
All announcements made by Bott Poker.

```
POST /api/v1/system/list-announcements
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## Ping
Ping the server for a timestamp.

```
GET /api/v1/system/ping
```

**Parameters:**
None

## Status
The current status of the Bott Poker system.

```
GET /api/v1/system/status
```

**Parameters:**
None

## Timestamp
The timestamp of the server for your synchronization.

```
GET /api/v1/system/timestamp
```

**Parameters:**
None

## System Version
The current version of the BottPoker system.

```
GET /api/v1/system/version
```

**Parameters:**
None

## Deal Community Cards
For testing your robots you can request community cards. This can be useful for testing robots without having to seat at a table.  The `test_id` is a required field for you to be able to request more cards such as pockets. Also consult the endpoint `tests/deal-pockets`. 

```
POST /api/v1/tests/deal-community-cards
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
test_id |  | YES |  | Provide a ID for the test. This can be used with the `tests/deal-pockets` endpoint.
request_amount |  | YES |  | How many cards do you want? Maximum of 5 allowed. 


## Deal Pockets
Related to the endpoint `test/deal-community-cards`. The `test_id` needs to be provided. Indicate with `how_many` you want to draw. A maximum of 10 is allowable.

```
POST /api/v1/tests/deal-pockets
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
test_id |  | YES |  | Provide a ID for the test. This can be used with the `tests/deal-pockets` endpoint.
how_many |  | YES | 1 | Maximum of 10 pockets allowed to be called.


## Tests Deal Full Details
Get the entire array of data of your test deal. Also look up the endpoints  `tests/deal-pockets` and  `tests/deal-community-cards`

```
POST /api/v1/tests/deal-full-details
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
test_id |  | YES |  | Provide a ID for the test. This can be used with the `tests/deal-pockets` and  `tests/deal-community-cards`  endpoints.


## Bot Debug Log
The debug log gives you a run down on your hands played, how your bot reacted and what the results were. This log is provided to give you the means to understand how your bot is behaving when encountering certain scenarios.

```
POST /api/v1/bot/debug-log
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID


## Delete Bot
Delete a bot from your account.

```
POST /api/v1/bot/delete-bot
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
id |  | YES | 10 | Provide the `id` of the bot.


## List Bot Profit and Loss (PNL)
A list is provided by `id` and `name` for you to understand your profit and loss of particular bots.

```
POST /api/v1/bot/list-bot-profitloss
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## List My Bots
List all available bots on your account. Consult this list when you are deleting, or applying a bot to an endpoint such as `game/poker/join`.

```
POST /api/v1/bot/list-my-bots
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## Register Bot
Register a bot for usage. Bots cannot be used together in any other equity pools. Review [Bot estrictions](./BOT-RESTRICTIONS.md) for more information about acceptable practices. In the event you violate the terms and conditions your account will be suspended and any funds you earned during that period will be ceased and returned to the parties impacted.

We automatically block bots from being able to seat together in all equity types but `sandbox`. You can freely seat with other bots you have registered in `sandbox` `equity pools`, but you will be stopped from doing so in any other equity type.

We take every precaution to make sure that you will not accidently seat with another bot. It is `prohibited` and we take actions to prevent it from occuring. If you accidently try to `join a room`  where you already have another bot seated, it will simply reject and will not impact your standing within the system.

```
POST /api/v1/bot/register-bot
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
username |  | YES |  | Unique bot username


## Deposit List
A list of all of your real currency deposits into BottPoker

```
POST /api/v1/deposit/list
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## Request Deposit Address
When depositing to the service you need to deposit to the service. Consult the endpoint `public/list-quity-pools` for the ID of the currency you would like to deposit too.

```
POST /api/v1/deposit/request-deposit-address
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
equity_pool_id |  | YES |  | Provide the `id` of the Equity Pool.


## Game Create Ring Game
This action is limited to users with the correct permissions. You must fill in all related information to the types. 

```
POST /api/v1/game/create-ring-game
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
name |  | YES |  | 


## Game Create Tournament
This action is limited to users with the correct permissions. You must fill in all related information to the types. 

```
POST /api/v1/game/create-tournament
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
name |  | YES |  | 
password |  | NO |  | Optional password
table_size |  | YES | 10 | Options, 2, 6 or 10
min_players |  | YES | 10 | The maximum amount of players until start.
max_players |  | YES | 10 | The maximum amount of players
time_start |  | YES | 0 | Provide a timestamp for when the tournament starts. If the minimum amount of players are not present when the timestamp reaches the tournament will wait until the minimum has been met
paidout_places |  | YES | 1 | How many users are paid out? In the event there are less users than the payout amount it will be divided
speed_id |  | YES |  | Consult `public/game-round-speeds` and `public/game-speeds` for more information.


## Join Game
You must provide the `game_id` and the `bot_id` to seat at a table. Please consult [CODE-OF-CONDUCT](./CODE-OF-CONTACT.md) and [COLLUSION](./COLLUSION.md) when you join a table. It is important to note that we take every measure to protect our players. We spend considerable resource on collusion and actively invite users to submit feedback about collusion attempts. When collusion is discovered we 

Also note you may encounter the following errors while trying to seat

- You are unable to sit with your own bots on a table in any other equity pool than `sandbox`.
- You will not be able to sit with users who are considered to be `affiliated`.
- All affiliations (`affiliated`) the system detects it will not disclosed to you.

In the event you try to eat with another bot who is `affiliated` to you, your access to join will be denied. This will not harm your standing or be logged as a collusion attempt, we are well aware that accidents like this can happen and we have measure to prevent this anyway.

```
POST /api/v1/game/join
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID


## Leave Game
You can only leave `SNG` and `TRN` if they have not started. With `RNG` you can request to leave at any point but the hand must finish. Please note that if you partake in `sit-down-stand-up-spam` your account is at risk of be blocked or freezed. We do not condone users who perform this type of operation and will actively enforce our [code of conduct](./CODE-OF-CONDUCT.md) rules which exist to protect everyone.

```
POST /api/v1/game/leave
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID


## List Game Player Actions
A complete list of actions available to you. This is an extention of the endpoints which provides more information about each action you can take and the use.

```
GET /api/v1/game/list-game-player-actions
```

**Parameters:**
None

## List Previous Hands
Show all previous hands for a particular game by providing the `game_id`.

```
POST /api/v1/game/list-previous-hands
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
limit |  | NO | 10 | 
page |  | NO | 1 | 


## List Table Players
List all of the players on the provided `game_id` currently. This endpoint does not provide historical data.

```
POST /api/v1/game/list-table-players
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID


## Payout Table
The full payout table for the table. If the table type is an `RNG` then no table will exist.

```
POST /api/v1/game/payout-table
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID


## Real-time Game Data
Real-time game data. Also see `websocket` information. Becareful when using this endpoint not to trigger rate limiting. This data provides all the current information about the games position. If you want to look at previous hands you should look at `game/list-previous-hands`.

```
POST /api/v1/game/realtime
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID


## Sit In
Sit back in on the table. If you are already seated out this request will be ignored. You only need to provide the `game_id` and be present at the game.

```
POST /api/v1/game/actions/sit-in
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID


## Sit Out
Sit out of the table. If you sit out you will forfeit blinds in `TRN` and `SNG`. If you are at a `RNG` you can only sitout for a maximum of 10 minutes before your bot will be kicked from the table.

```
POST /api/v1/game/actions/sit-out
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID


## Bet
Provide an amount to bet.

```
POST /api/v1/game/actions/bet
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID
amount |  | YES |  | Provide Amount


## Call
Call the current amount required. If ZERO then it will `check` for you.

```
POST /api/v1/game/actions/call
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID


## Fold
Fold your current hand. If there is no bet to make it will `check` for you. You cannot fold hands when there is nothing to call.

```
POST /api/v1/game/actions/fold
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID


## Post Blind
Post the blinds before they come to you. Otherwise they will automatically post when it comes to you. This endpoint is usually only used when someone seats at a table for the first time or comes back from having sitted out.

```
POST /api/v1/game/actions/post-blind
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID


## Raise
Please review the [poker raising mechanics document](./RAISING-MECHANICS.md) for more information about how you should raise. In the event you raise more than you have, you will be marked as `allin`,

```
POST /api/v1/game/actions/raise
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID
amount |  | YES |  | 


## Game Actions
If you are below the maximum allowed you and in a `RNG` you can request to top up from your balance.

```
POST /api/v1/game/actions/top-up
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID


## All-in
Place your bot all-in. All-in can occur automatically if you have less than a required blind when it comes to your turn.

```
POST /api/v1/game/actions/allin
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_id |  | YES |  | Provide Game ID
bot_id |  | YES |  | Provide BOT ID


## List Collusions
List all collusions as they are flagged. See [Collusions document](./COLLUSIONS.md) for more information about how we handle this topic.

```
POST /api/v1/public/collusion-list
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## List Collusion Refunds
List all collusion refunds that have been made by BottPoker. You can read more about [collusions here](./COLLUSIONS.md).

```
POST /api/v1/public/collusion-refunds
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## Leaderboards
The leaderboards for each `equity_id`. Provided as a useful resource to know who you are playing.

```
POST /api/v1/public/leaderboards
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
equity_id |  | NO | 10 | Equity Pool ID
limit |  | NO | 10 | 
page |  | NO | 1 | 


## List Ring Games
List all available ring games. This does not provide an historical view.

```
POST /api/v1/public/poker/list-ring-games
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## List Sit and Go Games
List all available sit and go games. This does not provide an historical view.

```
POST /api/v1/public/poker/list-sitandgo-games
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## List Tournament Games
List all available poker tournament games. This does not provide an historical view.

```
POST /api/v1/public/poker/list-tournament-games
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## List Equity Pools
List all equity pools 

```
GET /api/v1/public/list-equity-pools
```

**Parameters:**
None

## Network Playing Statistics
Stats on players online and amount of active bots per user are some of the values available.

```
GET /api/v1/public/network-playing-statistics
```

**Parameters:**
None

## Game Round Speeds
List of the game round speeds. This relates by `object_id` to `public/game-speeds` endpoint.

```
POST /api/v1/public/game-round-speeds
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
object_id |  | NO |  | Filter by object ID


## Game Speeds
The parent `id` for `public/game-round-speeds`

```
GET /api/v1/public/game-speeds
```

**Parameters:**
None

## Public Game Types
Show all game types available.

```
GET /api/v1/public/game-types
```

**Parameters:**
None

## User Access History
All of your user access history related to logging in via bottpoker.com

```
GET /api/v1/user/access-history
```

**Parameters:**
None

## User Active Sessions
A list of all active sessions happening on bottpoker.com

```
POST /api/v1/user/active-sessions
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## User API Limits
User API Limits for your account.

```
GET /api/v1/user/api-limits
```

**Parameters:**
None

## Game History
A full game history, you should cross reference the provided IDs with other endpoints for a richer data experience.

```
POST /api/v1/user/game-history
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 
bot_id |  | NO |  | Filter bots



## List Violations
Any violations you have found to have made will be listed here. Please consult our [code of conduct](./CODE-OF-CONDUCT.md) for more information.

```
POST /api/v1/user/list-violations
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## User List Rakebacks
List all of your rakebacks you have made in your account. You can filter down to `bot_id`

```
POST /api/v1/user/list-rakebacks
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 
bot_id |  | NO |  | Provide BOT ID


## User List Rakes Paid
A daily summary of your paid rake per day

```
POST /api/v1/user/list-rakes-paid
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## User Rakeback Level
Information about your current rakeback percentage. Rakebacks are settled every 24 houts.

```
GET /api/v1/user/rakeback-level
```

**Parameters:**
None

## Active Bots
All active bots which are currently either seated and playing or waiting for a `TRN` or `SNG` to start.

```
POST /api/v1/user/active-bots
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
game_type |  | NO |  | Filter the room type `RNG`, `SNG` or `TRN`.


## Withdraw List
All of your accounts withdraw requests and related `status` and `id` information

```
POST /api/v1/withdraw/list
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
limit |  | NO | 10 | 
page |  | NO | 1 | 


## Request Withdraw
Withdraw your earnings to your desired location. The parameters may alter based on your requested withdraw method. All withdraw methods must have a whitelisted IP attached.

```
POST /api/v1/withdraw/request-withdraw
```

**Parameters:**
Name | MinLength | Required | Default | Description
------------ | ------------ | ------------ | ------------ | ------------
equity_pool_id |  | YES |  | Provide the `id` of the Equity Pool.
address |  | YES |  | Provide the address
amount |  | YES |  | Provide the amount

