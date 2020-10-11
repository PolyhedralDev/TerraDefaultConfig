# Biome Selection
This page provides an overview of how Terra selects a biome for a location based on a Config Pack's BiomeGrids and
BiomeZone.

## Biome Grids
A Biome Grid defines Biome distribution in a world. They are 2D (hence the name "grid") tables of biomes. Here is a
simple example of a Biome Grid you may use in your world:  
|   | 0 | 1 | 2 | 3 |
|---|--------|--------|------------|------------|
| 0 | PLAINS | PLAINS | OAK_FOREST | OAK_FOREST |
| 1 | PLAINS | PLAINS | BIRCH_FOREST | BIRCH_FOREST |
| 2 | DESERT | DESERT | SAVANNA | SAVANNA |
| 3 | DESERT | DESERT | SAVANNA | SAVANNA |   

2 continuous noise functions determine the biome at a location. This means that biomes adjacent on the grid
will generate next to each other in the world. For example, if, for a pair of coordinates in the world, noise function X
has a value of 3, and noise function Z has a value of 2, the biome at that location would be SAVANNA. Then, if Z shifts
to 1, the biome would change to BIRCH_FOREST.  

Generally, the X and Z axis are "scales." For example, in the above example, the X axis may be the Vegetation
scale, as biomes with higher X values have more vegetation, and Z may be the Temperature scale, as biomes with higher Z
values are warmer. This allows you to group similar biomes together.

## Biome Zones
A Biome Zone defines Biome *Grid* distribution in the world. Essentially, it adds a third dimension to Biome selection
by "stacking" several Biome Grids on top of each other. A third continuous noise function pulls Biome Grids from the
Zone configuration. For example, here is the Biome Zone config from the pack.yml page's example:
```yaml
grids:
  - OCEAN
  - LAND
  - MOUNTAIN
```
In the above configuration, a Biome Zone noise value of 0 causes Terra to pull biomes from the `OCEAN` grid, using the
2 BiomeGrid noise functions. Then, if the noise value shifts to 1, biomes will be pulled from the `LAND` grid.  
Since Biome Zones, like Biome Grids, use a continuous noise function, Grids that are adjacent in the zone config will
generate adjacent in the world.

## Noise
The noise functions used to select biomes are the same functions that are defined in `pack.yml`.

## Use Cases
Generally, Biome Grids define *similar terrain* Biomes, and Biome Zones define different types of terrain.
For example, the example above has `OCEAN`, `LAND`, and `MOUNTAIN` as grids in the Biome Zone config. This is because,
for the most part, all biomes that would fall under the Ocean category have very similar terrain, as do Land and
Mountain biomes.   
Because Biome Zones generally define the largest difference in biomes, they are usually given the highest spread in the
world (The highest frequency in `pack.yml`).  
   
As mentioned above, each of a Biome Grid's axes usually has a scale assigned to it, like Temperature or Vegetation.
Expanding this into the third dimension with Biome Zones opens up many possibilities. Using the *same scales* on all
Grids ensures that similar biomes generate adjacent in the world. For example, if, in the `LAND` grid, there was a
`TUNDRA` biome in slot (0, 0), then, in the `OCEAN` grid, it would be wise to put a `FROZEN_OCEAN` biome in the same
slot, that way, the Tundra biome always borders frozen oceans.