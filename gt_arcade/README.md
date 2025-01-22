# Arcade Coop Gametype

Arcade Coop is a single player / cooperative Player versus Environment gametype in
which players must defeat waves of enemies, and reach the "Portals" before
they open. It features a shop in which you can purchase equipment, upgrades,
and special abilites created for this gametype.

The latest versions this was tested with:
- Warfork version 2.12
- Warsow v2.10

Code/Graphics by Xanthus, all sounds by Jihnsius. This project is licensed under MIT License.

## Votes / Difficulty
You can alter the Arcade experience in game by changing a few votable variables.

- arc_difficulty (50-300) : The percentage of damage the enemies do (Default: 100)
- arc_mapsize (0-3) : changes the number of enemies that can be alive at once, use higher numbers for bigger maps
  - 0: Tiny
  - 1: Small/Duel
  - 2: Medium / 2v2
  - 3: Large / 4v4
- arc_portal (0-3) : The frequency and timer of the portal.
  - 0 : No portals
  - 1 : 30 seconds
  - 2 : 12 seconds
  - 3 : 7 seconds
- arc_mission : The name of the mission config file. (Default: normal, which loads the arc_nomral.cfg file)

## Editing Mission Configs
Mission config files define what enemies are in each wave, the number that must be defeated,
and how many can be active at once.

Enemy / enemy pool names (comments in parenthesis):
- pool_easy (random from the below enemies)
  - bat
  - walker
  - sniper
- pool_med
  - pig  (random pig with either GL, RL, or PG)
  - pig_gl
  - pig_rl
  - pig_pg
  - shield
  - wizard

Example config below defines a mission with only two waves (comments in parenthesis):
```
7  (7 enemies active at once)
25 ( defeat 25 to end the wave )
bat 2
walker 2
sniper 1
wave_end  (until the wave ends, the above enemies will keep spawning)
8 (8 enemies active at once)
30
pool_easy 4
pig 1  (spawns a pig with a random weapon from RL, GL, and PG)
mission_end (notes the end of the mission)
```


## Custom Spawn Locations
By default, the gametype will use player spawns for portal placement. If you would
prefer to customize your own for a certain map to improve it, there are commands
you can use to create a config for a map.

- addspawn : This will add a spawn for your current location. Walk around the map
  and call this at each Portal/enemy spawnpoint. The existing/default spawn locations
  are not included when you begin to call addspawn- so make sure you add every location
  you want to save to the new config!
- savespawncfg : Call this to save a custom config using all the locations you
  called "addspawn" for.

WARNING: You MUST create at least two spawns, otherwise the game will crash
after you close the first portal (a portal can't re-appear at the same spot)

