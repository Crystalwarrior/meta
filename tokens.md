# Dangerous code tokens

The following is a list of "tokens" (bits of code) that are to be scrutinised more heavily by the automated parsing system.
Please add to this list if you think of any.

## Suspicious tokens

 * Creating `TCPObject` instances
 * References to `servAuthTCPObj`
 * BLID or name specific if statements (`if(%client.bl_id == 16807)`)
 * Usage of `FreeMemoryDump()`
 * Usage of `videoSetGammaCorrection()`
 * Usage of `setVerticalSync()`
 * Usage of `setProcessorAffinityMask()`
 * Usage of `getClipboard()`
 * Usage of `quit()`
 * Usage of `call()`
 * Usage of `eval()`
 * Usage of `deleteVariables()`
 * Usage of `createPath()`
 * Usage of `fileDelete()`
 * Usage of `fileCopy()`
 * Usage of `upnpAdd()`
 * Usage of `deleteDataBlocks()`
 * Usage of `aiAddPlayer()`
 * Usage of `aiConnect()`
 * Usage of `gotoWebPage()`
 * Usage of `secureCommandToClient()`
 * Usage of `secureCommandToAll()`
 * Usage of `secureCommandToAllExcept()`

## Dangerous tokens

 * Usage of `setKey()`
 * Usage of `crash()`
 * Usage of `SteamOfflineUnlock()`
 * Usage of `SteamUnlock()`
 * Usage of `Unlock()`
 * Usage of `lock()`
 * Usage of `setMyBLID()`
 * Usage of `getPassPhraseResponse()`
 * Usage of `setKeyDat()`
 * Usage of `killAllQuotaObjects()`
 * Usage of `SteamAPI_Init()`
 * Usage of `SteamAPI_Shutdown()`
 * Usage of `steamGetAchievement()`
 * Usage of `steamClearAchievement()`
 * Usage of `SteamGetAuthSessionTicket()`

## Suspicious file paths

Keep in mind that this does *not* auto-fail submissions, it merely warns reviewers with a list of triggered paths.

#### Writing

 * Add-Ons/\*_\*/\*\*/\*
 * base/\*\*/\*
 * config/client/Avatar/\*.cs
 * config/client/MiniGameFavorites/\*.cs
 * config/client/avatarColors.cs
 * config/client/config.cs
 * config/client/Favorites.cs
 * config/client/prefs.cs
 * config/client/prefs-trustList.txt
 * config/server/ADD\_ON\_LIST.cs
 * config/server/BANLIST.txt
 * config/server/colorSet.txt
 * config/server/musicList.cs
 * config/server/prefs.cs
 * saves/\*\*/\*
 * screenshots/\*\*/\*
 * \*

#### Reading

 * \*

## Resources

http://bldocs.nullable.se/html/namespace_server_1_1_global.html#aff8f84aaa111abe1bb06a5cde5558164
