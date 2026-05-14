# Saint's Transient Addictions

A mod for Fallout: New Vegas / Tale of Two Wastelands that introduces a time and chance based natural recovery from addictions. Written in NVSE, ESPLess, safe to add or remove at any time.

## About

In vanilla, addictions are a forever problem and can only be removed by paying for a doctor's services or by taking Addictol, if available.  This mod adds the ability to *naturally recover* from addictions. If the player is in good health and has abstained for a time, there is a chance (based on time, endurance, and luck) to recover from an addiction on its own. Features a fine selection of *back-patting messages* as you manage to leave your fiend life in the ditch.

## Mechanics

Each active addiction has a chance to naturally disappear. The player needs to be healthy and has to abstain from using any items giving the addiction effect for at least a couple of days. Endurance and luck stats increase the chances for a recovery. Active withdrawal effects are checked every tick (every 30 seconds by default, configurable). Once an addiction is recovered, you will be informed via congratulatory message. The message(s) will be queued up and displayed when not in combat, like a level-up. Addictions cannot be healed while being suppressed by an item giving them.

The recovery chance per addiction is calculated from the following factors:

- Player is healthy (HP > 70% by default, configurable)
- Time since last use (pivot-based, 5 days by default, configurable)
- Player endurance (`END / 9 * 0.25` by default, configurable)
- Player luck (`LCK / 9 * 0.25` by default, configurable)
- Final chance is `(fEND + fLCK) * fTime * fHealth`

Every time the player consumes an item, the mod checks whether there’s an associated withdrawal effect. If there is, the item’s activation time is logged (and stored in an auxiliary variable). This time is updated with every future use of the item. When ticking recovery, the mod checks the time difference between now and last use. Note that this tracking is separate from the game's UMON.

## Compatibility

The mod uses the `TTWAddictionWithdrawalList` form list to determine which effects are withdrawals. Every item having an associated withdrawal effect that is in this form list is supported automatically. TTW already populates this with base game effects from Fallout 3 and New Vegas. If another mod adds their own ingestibles with custom withdrawal effects, their effect ids must be added to the form list to be eligible for natural recovery.

## Roadmap

- [CONSIDERED] Scriptrunner patch to add *Hit Drugs* withdrawal effects to form list (they could also do this themselves, really).
- [CONSIDERED] Support for base FNV (non-TTW version) -- if a form list already exists for withdrawals just for FNV, this could be easily done. You can request features in the Posts section of the Nexus mod page.

## Requirements

Requires xNVSE and its typical extensions, JIP NVSE, JohnnyGuitar, and ShowOff.

## License

This mod was created by Saint for free use by the Fallout mod community under the MIT license. It may be shared, modified, or redistributed as part of mod packs with basic attribution.