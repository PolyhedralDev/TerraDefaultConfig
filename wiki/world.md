# World Configuration
World config files define general world-specific values that do not rely on a Config Pack. They are
automatically generated in `Terra/worlds/`, and named for the world they configure.

### config
The ID of the config pack to use in this world.

### image
Options to pull Biome selections from an image.   
All of these are optional. If they are not included, the generator will not use an image for terrain. (equivalent to
`image.enable` = `false`).
* `enable` - Whether to pull Biome selections from an image.
* `align` - The alignment of the image. Valid values are `CENTER` and `NONE`.
    * `CENTER` - Center the image, so world coordinates (0, 0) are at the center of the image.
    * `NONE` - Do not re-align the image, so world coordinates (0, 0) are at image coordinates (0, 0).
* `file` - The image file location on the drive. **Must be a locally stored image, not an online one!**
* `channels` - What color channels will be used for what Biome selection axis. The values `red`, `green`, and `blue`
are all used once, and only once.
    * `biome-x` - What color channel to use for BiomeGrid X selection (image exports as `red`)
    * `biome-z` - What color channel to use for BiomeGrid Z selection (image exports as `green`)
    * `zone` - What color channel to use for Biome Zone selection (image exports as `blue`)  

## Example
<details>
<summary>Example Configuration</summary>

An example world config. This world has been assigned the generator `OVERWORLD_DEMO`, and has an image to pull biome
selections from, located at `/home/user/image/image.png`.
```yaml
config: OVERWORLD_DEMO
image:
  enable: true
  align: center
  file: "/home/user/image/image.png"
  channels:
    biome-x: red
    biome-z: green
    zone: blue
```

</details>