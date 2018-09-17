# OatyStats
A Javascript wrapper for SmashGG tournament data.

This wrapper utilises SmashGG public API: [SmashGGApi](https://smashgg.zendesk.com/hc/en-us/articles/217471947-API-Access).

Currently the SmashGG developer is fairly primitive, and requires multiple lookups to find certain data, this wrapper intends to make pulling data for given players simpler and more powerful.

## Basic Usage:
getHeadToHead(Player1GamerTag, Player2GamerTag, tournamentSlug, loadingCallbackFn)
 > tournamentSlug is required to figure out the Player Ids from the tags. (ie, "holy-melee-24")
 
The _loadingCallbackFn_ is a function that will be called with a *LoadingEvent* object when an event occurs:
  + getEventType : {EventType.SETS, EventType.MATCHES, EventType.INFO, EventType.DEBUG}
  + getMessage : String
 
This returns a *HeadToHeadDetails* object containing the following attributes:
```
  + getSetCount()       :    Score
  + getMatchCount()     :    Score
  + getMostRecentWins() : [Date, Date] // First item is for player1, second is for player2.
```
Score object:
```
  + getP1Score()       :    int
  + getP2Score()       :    int
```