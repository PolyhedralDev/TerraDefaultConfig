# Block Palettes
Block Palettes define a vertical slice of the world. They are lists of blocks, from which Terra picks based on the depth
at a location.  
Palettes define the blocks used to generate the world, and they are configured on a per-Biome basis. Biomes contain a
list of Palettes, based on Y levels, allowing the user to control which blocks generate at *relative* depths, and
*absolute* depths.

## Relative depth
Relative depth describes "distance below the surface." For example, a Palette can specify that 3 blocks below the
surface of the world, Stone should generate.

## Absolute depth
Absolute depth is a Y-level. For example, a Biome can specify that at Y levels 0-96, a palette called GRASSY is to be
used.

## Randomness
