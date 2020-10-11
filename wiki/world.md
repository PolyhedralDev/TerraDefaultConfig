# World Configuration
World config files define general world-specific values that do not rely on a Config Pack. They are
automatically generated in `Terra/worlds/`, and named for the world they configure.

### config
The ID of the config pack to use in this world.

### image
Options to pull Biome selections from an image. All image-related options are **optional**.
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