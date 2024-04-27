Alt-H1 aaaaa

## MapVote
The `MapVote` plugin for squad js based on the original version https://github.com/maskedmonkyman/squad-js-map-vote

### Commands

#### User Commands
- `!vote help` - sends possbile commands to a player in the from of a warning
- `!vote choices` - sends choices to player in the from of a warning
- `!vote results` - sends player the results in a warning

#### Admin Commands
- `!vote start` - Starts a vote with 6 layers, random modes
- `!vote cancel` - Cancels current round of voting
- `!vote cancelauto` - Cancel scheduled automatic start of vote
- `!vote end` - Gently ends the current vote and announces the winner layer
- `!vote restart` - Restarts voting with 6 random maps and modes
- `!vote broadcast` - Broadcasts current voting results - happens every 7m automatically
- `!vote endmatch` - Ends the current match
- `!vote setvotes <layer_number> <new_vote_count>` - Forces a new amount of votes for a specific layer
- `!vote changevotes` - Alias of `!vote setvotes`

##### Vote by modes
- `!vote start *_raas` - Starts a vote with 6 layers, all RAAS
- `!vote start *_aas` - Starts a vote with 6 layers, all AAS
- `!vote start *_inv` - Starts a vote with 6 layers, all INV

##### Vote by faction
- `!vote start f:rus` - Starts a vote with 6 layers, all with RUS faction
- `!vote start f:aus` - Starts a vote with 6 layers, all with AUS faction
- `!vote start f:mea f:caf f:usa` - Starts a vote with 3 layers, 1 with MEA faction, 1 with CAF faction and 1 with USA faction

##### Vote by map
- `!vote start yeh gor lash gor albas` - Starts a vote with X maps, random modes

##### Vote by map + mode, mixed
- `!vote start yeh_raas gor_raas lash_inv gor albas_inv` - Starts a vote with X maps, X modes

### DBLog
Configure the DBLog SquadJS plugin, nothing more is required.
#### Available Tables
- MapVote_PlayerVotes

### Options
#### commandPrefix
###### Description
The command name to use in chat.
###### Default
```
!vote
```
#### entryFormat
###### Description
The format of an entry in the voting list.
###### Default
```json
"{map_name} {gamemode} {map_version} {factions} {main_assets}"
```
#### entriesAmount
###### Description
Amount of entries generated for automatic votes.
###### Default
```json
6
```
#### automaticVoteStart
###### Description
A map vote will automatically start after a new match if set to true.
###### Default
```json
true
```
#### votingDuration
###### Description
How long the voting will be active (in minutes). Set to 0 for unlimited time.
###### Default
```json
0
```
#### minPlayersForVote
###### Description
The number of players needed on the server for a vote to start.
###### Default
```json
40
```
#### voteWaitTimeFromMatchStart
###### Description
The time in mins from the start of a round to the start of a new map vote.
###### Default
```json
15
```
#### voteBroadcastInterval
###### Description
The broadcast interval for vote notification in mins.
###### Default
```json
7
```
#### automaticSeedingMode
###### Description
Instantly change to a seeding layer if server has less than 5 players and set next layer to a seeding layer if server has less than 20 players.
###### Default
```json
true
```
#### numberRecentMapsToExlude
###### Description
The random layer list will not include the X recent maps
###### Default
```json
4
```
#### numberRecentLayersToExclude
###### Description
**REQUIRES DBLOG PLUGIN**. Avoids repeating the same layer of the same map
###### Default
```json
4
```
#### gamemodeWhitelist
###### Description
The random layer list will be generated with only selected gamemodes.
###### Default
```json
[ "AAS", "RAAS", "INVASION" ]
```
#### layerFilteringMode
###### Description
Select Whitelist mode or Blacklist mode.
###### Default
```json
"blacklist"
```
#### layerLevelWhitelist
###### Description
The random layer list will include ONLY the whitelisted layers or levels. (acceptable formats: Gorodok/Gorodok_RAAS/Gorodok_AAS_v1).
###### Default
```
[]
```
#### layerLevelBlacklist
###### Description
The random layer list will NOT include the blacklisted layers or levels. (acceptable formats: Gorodok/Gorodok_RAAS/Gorodok_AAS_v1).
###### Default
```
[]
```
#### applyBlacklistToWhitelist
###### Description
If set to true the blacklisted layers will be filtered out also in whitelist mode.
###### Default
```json
true
```
#### factionsBlacklist
###### Description
factions to exclude in map vote. ( ex: ['CAF'] )
###### Default
```json
[]
```
#### minGamemodeEntries
###### Description
Minimum amount layers in the vote list per gamemode.
###### Default
```json
{
    "raas": 2,
    "aas": 2,
    "invasion": 0
}
```
#### hideVotesCount
###### Description
Hides the number of votes a layer received in broadcast message.
###### Default
```json
false
```
#### hideEntryIndex
###### Description
Hides the index number of an entry in the mapvote broadcast.
###### Default
```json
false
```
#### showRerollOption
###### Description
vote option to restart the vote with random entries.
###### Default
```json
false
```
#### showRerollOptionInCustomVotes
###### Description
Enables/disables the reroll option only in custom votes. showRerollOption must be set to true.
###### Default
```json
false
```
#### voteBroadcastMessage
###### Description
Message that is sent as broadcast to announce a vote.
###### Default
```json
"✯ MAPVOTE ✯\nVote for the next map by writing in chat the corresponding number!"
```
#### voteWinnerBroadcastMessage
###### Description
Message that is sent as broadcast to announce the winning layer.
###### Default
```json
"✯ MAPVOTE ✯\nThe winning layer is\n\n"
```
#### showWinnerBroadcastMessage
###### Description
Enables the broadcast at the end of the voting.
###### Default
```json
true
```
#### allowedSameMapEntries
###### Description
Allowed max NUMBER of times a map could appear in the vote list.
###### Default
```json
1
```
#### logToDiscord
###### Description
Enables/disables vote logging to Discord.
###### Default
```json
false
```
#### channelID
###### Description
The ID of the channel to log votes to.
###### Default
```json
"112233445566778899"
```
#### persistentDataFile
###### Description
Path to file in which to store important data that should be restored after a restart.
###### Important
Make sure the persistent data file is not inside the plugin folder.
###### Default
```json
""
```
#### timezone
###### Description
Timezone relative to UTC time. 0 for UTC, 2 for CEST (UTC+2), -1 (UTC-1) 
###### Default
```json
0
```
#### timeFrames
###### Description
Array of timeframes that allows to override options based on local time. See example configuration
###### Default
```json
[]
```
#### minimumVotesToAcceptResult
###### Description
Minimum votes per map to accept result. 

Can be used to prevent situation when insignificant number of players decide what map should be next, but most still wants to play map according to rotation.
###### Default
```json
1
```
#### seedingGameMode
###### Description
Gamemode used in seeding mode. 
###### Default
```json
"Seed"
```
#### instantSeedingModePlayerCount
###### Description
Required player count to trigger an instant layer change to a seeding layer. 
###### Default
```json
5
```
#### nextLayerSeedingModePlayerCount
###### Description
Required player count to change the next layer to a seeding layer. 
###### Default
```json
20
```
#### developersAreAdmins
###### Description
Developers of this plugin are allowed to run admin commands in anychat. 
###### Default
```json
true
```
#### OWIMapLayerGSheetUrl
###### Description
Map/Layers Google Sheet URL provided by OWI.
###### Default
```json
"https://docs.google.com/spreadsheets/d/139zvTRo6YnocNM0e4Q_JHHy4gOMG6qiIDWSP2YlMlKM/edit?usp=sharing"
```
###### Timeframe format
```javascript
{
    name: "friendly name", // a friendly name visible in the logs
    start: "12:00", // timeframe start time <hour>:<minutes>
    end: "18:00", // timeframe end time <hour>:<minutes>
    overrides: { // options to override
        automaticVoteStart: false,
        layerLevelBlacklist: [ "Anvil", "Chora" ]
    }
}
```
### Quick start configuration
```json
{
    "plugin": "MapVote",
    "enabled": true,
    "discordClient": "discord",
    "entriesAmount": 6,
    "automaticVoteStart": true,
    "minPlayersForVote": 30,
    "voteWaitTimeFromMatchStart": 10,
    "voteBroadcastInterval": 7,
    "numberRecentMapsToExlude": 4,
    "automaticSeedingMode": false,
    "gamemodeWhitelist": [ "AAS", "RAAS", "Invasion" ],
    "layerFilteringMode": "blacklist",
    "layerLevelBlacklist": [ "BlackCoast_Seed" ],
    "layerLevelWhitelist": [ "Yeho", "Gorodok", "Mutaha", "Narva", "Tallil" ],
    "applyBlacklistToWhitelist": true,
    "factionsBlacklist": [ "CAF", "INS" ],
    "logToDiscord": true,
    "channelID": "112233445566778899",
    "persistentDataFile": "",
    "timezone": 2,
    "filterByMod": [],
    "minGamemodeEntries": {
        "raas": 2,
        "aas": 2,
        "invasion": 0
    }
}
```
### Example configuration
```json
{
    "plugin": "MapVote",
    "enabled": true,
    "discordClient": "discord",
    "entriesAmount": 6,
    "entryFormat": "{map_name} {gamemode} {map_version} {factions} {main_assets}",
    "automaticVoteStart": false,
    "votingDuration": 0,
    "minPlayersForVote": 30,
    "voteWaitTimeFromMatchStart": 10,
    "voteBroadcastInterval": 7,
    "numberRecentMapsToExlude": 4,
    "numberRecentLayersToExclude": 4,
    "automaticSeedingMode": true,
    "gamemodeWhitelist": [ "AAS", "RAAS", "Invasion" ],
    "layerFilteringMode": "blacklist",
    "layerLevelBlacklist": [ "BlackCoast_Seed" ],
    "layerLevelWhitelist": [ "Yeho", "Gorodok", "Mutaha", "Narva", "Tallil" ],
    "applyBlacklistToWhitelist": true,
    "factionsBlacklist": [ "CAF", "INS" ],
    "hideVotesCount": false,
    "hideEntryIndex": false,
    "showRerollOption": true,
    "showRerollOptionInCustomVotes": false,
    "voteBroadcastMessage": "✯ MAPVOTE ✯\nVote for the next map by writing in chat the corresponding number!",
    "voteWinnerBroadcastMessage": "✯ MAPVOTE ✯\nThe winning layer is\n\n",
    "showWinnerBroadcastMessage": true,
    "allowedSameMapEntries": 1,
    "logToDiscord": true,
    "channelID": "112233445566778899",
    "persistentDataFile": "",
    "timezone": 2,
    "minimumVotesToAcceptResult": 1,
    "instantSeedingModePlayerCount": 5,
    "nextLayerSeedingModePlayerCount": 20,
    "seedingGameMode": "Seed",
    "developersAreAdmins": true,
    "OWIMapLayerGSheetUrl": "https://docs.google.com/spreadsheets/d/139zvTRo6YnocNM0e4Q_JHHy4gOMG6qiIDWSP2YlMlKM/edit?usp=sharing",
    "filterByMod": [],
    "minGamemodeEntries": {
        "raas": 2,
        "aas": 2,
        "invasion": 0
    },
    "timeFrames": [
        {
            "name": "follow layer rotation list",
            "start": "12:00",
            "end": "18:00",
            "overrides": {
                "automaticVoteStart": false
            }
        },
        {
            "start": "22:00",
            "end": "02:00",
            "overrides": {
                "voteBroadcastMessage": "Late night games? Vote your favourite map!"
            }
        }
    ]
}
```
