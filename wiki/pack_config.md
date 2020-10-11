# pack.yml Options
`pack.yml` is a required file located in the root of all Terra config packs. It defines universal pack options like biome
blending, biome selection, and erosion.

### id
The ID of the config pack. This should be unique (not something generic like "overworld,"
since users may wish to install multiple config packs).  
World configs use this ID to identify which config pack is to be used in the world.

### grids
A list of BiomeGrid IDs, which makes up the third dimension "zone" axis of biome selection. Generally, this section is
the lowest-frequency biome axis, and is used to differentiate between very different BiomeGrids, such as ocean, land,
and mountain biomes.

### frequencies
The frequencies to use for each axis of Biome selection. This contains 3 keys, `grid-x`, `grid-z`, and `zone`.  
* `grid-x` - defines the frequency of the X-axis of BiomeGrids.
* `grid-z` - defines the frequency of the Z-axis of BiomeGrids.
* `zone` - defines the frequency of Zone selection, described above.  
Note that the values here are actually the *inverses* of the actual frequencies, meaning, higher values correspond to
more spread-out biomes. (a value of 1000 will become 0.001 internally)

### blend
Biome blending options. These options configure whether to, and how much to blend biomes together at intersections.  
All of these are optional. If they are not included, the generator will not attempt to blend biomes (equivalent to
`blend.enable` = `false`).
* `enable` - Whether to blend biomes at all.
* `frequency` - The frequency of the noise used to blend biomes. Higher values produce "messier" blends, with values 0.5
and above generally producing "random" scattered blending. Unlike the Biome choosing frequencies, this value corresponds
to the actual frequency used internally.
* `amplitude` - The amplitude of blending. This basically defines "how much" biomes should be blended. (for example, a 
value of 16 will create an approximately 16-block wide blended zone between biomes)  

### erode
Options for erosion. Erosion inserts a custom BiomeGrid at locations where the square of the erosion noise
function is greater than the erosion threshold. (It is most commonly used to create rivers).  
All of these are optional. If they are not included, the generator will not attempt to generate erosion (equivalent to
`erode.enable` = `false`).
* `enable` - Whether to enable erosion
* `frequency` - Erosion noise frequency. Higher values "zoom out" the erosion, producing smaller, more tightly-packed
eroded biomes. Unlike the Biome choosing frequencies, this value corresponds to the actual frequency used internally.
* `threshold` - When the erosion noise function produces a value which, when squared, is *less than* this threshold, the
location will be eroded.
* `octaves` - The number of noise octaves to use for erosion. Higher values produce "squigglier" erosion.
* `grid` - The BiomeGrid to pull biomes from when a location is to be eroded.

***

## Example
<details>
<summary>Example Configuration</summary>

An example config with 3 grids, `OCEAN`, `LAND`, and `MOUNTAIN`, and with biome blending and erosion enabled. The generator ID
is `OVERWORLD_DEMO`.
```yaml
id: OVERWORLD_DEMO
grids:
  - OCEAN
  - LAND
  - MOUNTAIN
frequencies:
  grid-x: 3072
  grid-z: 2048
  zone: 4096
blend:
  enable: true
  frequency: 0.125
  amplitude: 10
erode:
  enable: true
  frequency: 0.002
  threshold: 0.001
  octaves: 4
  grid: "BIOME:RIVER"
```

</details>