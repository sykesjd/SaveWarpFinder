# SaveWarpFinder

A Python script for finding warp sequences in GoldSrc and Old Source Engine games.

## Command line argument specification
`python builder.py -g <gameAbbr> -d "<destinationStr>" [-m <maxPathLength>]`

- `gameAbbr`: the abbreviation for the game in which to find warps
  - Available options: `hl1`, `op4`, `bs`, `hl2`
- `destinationStr`: desired destination for which to find warps, formatted as `<map> at: <x> x, <y> y, <z> z` where `map` is the map name and the xyz coordinates are provided
- `maxPathLength` (optional): desired maximum chain length of warps to find (default is 35)

## How to use
1. Dump all your potential starting positions for warps (*waypoints*) into a `waypoints_<gameAbbr>.txt` file, where `gameAbbr` corresponds to the abbreviation for the game in which to find warps (see above). Waypoints shall be described in the following format: `<map> | <x> <y> <z>`. For making waypoints, use `swarp_wp_` commands from SWT:
    - `swarp_wp_add` creates a new waypoint in the player's current position on current map and adds it to the list.
    - `swarp_wp_dump` dumps all waypoints in the list into console in the above format.
    - `swarp_wp_clear` clears the list.
2. Save the waypoints file in the directory in which `builder.py` resides.
3. Run `builder.py` using the command line arguments specified above. As a new warp chain is found, it will be dumped into `stdout`.
    - If desired, the output can instead be piped into a file by appending ` > outfile.txt` to the command.
