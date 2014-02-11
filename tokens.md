# Dangerous code tokens

The following is a list of "tokens" (bits of code) that are to be scrutinised more heavily by the automated parsing system.
Please add to this list if you think of any.

## Suspicious tokens

 * Usage of `eval()`
 * Usage of `call()`
 * `fileDelete()`
 * Creating `TCPObject` instances
 * `FileObject` instances opening base/* folders for writing or appending
 * BLID or name specific if statements (`if(%client.bl_id == 16807)`)

## Dangerous tokens

 * `crash()`

## Suspicious file paths

#### Writing

 * Add-Ons/\*_\*/\*
 * base/\*\*/\*
 * config/client/avatarColors.cs
 * config/client/config.cs
 * config/client/prefs.cs
 * config/client/prefs-trustList.cs
 * config/server/ADD\_ON\_LIST.cs
 * config/server/musicList.cs
 * config/server/prefs.cs
 * \*

## Resources

http://bldocs.nullable.se/html/namespace_server_1_1_global.html#aff8f84aaa111abe1bb06a5cde5558164
