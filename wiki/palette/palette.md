# Block Palettes
Block Palettes define a vertical slice of the world. They are lists of blocks, from which Terra picks based on the depth
at a location. They are located in the `palettes` directory within a config pack.  
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
Palettes offer two types of randomness to use for block selection. 
* Random - A pseudorandom number generator. This will produce random scattering of blocks. The seed is configurable.
* Simplex - A simplex generator, redistributed to a continuous distribution. This will produce blob-like patches of
blocks. The frequency and seed are configurable.