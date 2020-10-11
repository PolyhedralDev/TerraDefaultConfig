# Config Packs
Config packs define a Terra world generator. They are YAML-based, and define all the necessary components to create a
complete world generator with Terra. Users may install multiple config packs simultaneously, allowing the use of
multiple Terra-based generators on the same server.  
Config packs occupy the directory `plugins/Terra/packs/`. 

## Installing a Config Pack
Installing a config pack is easy! Simply download your config pack, and drop it in the `plugins/Terra/packs/` directory.
Then, open the world config for whatever world you wish to use the pack in, and set the `config` key to the ID of the
pack. Stop your server, delete the corresponding world folder, and you're done!

## Creating a Custom Config Pack
To use Terra to its full potential, you will probably want to create a custom config pack. While Terra has a very simple
to understand, intuitive config system, this does **not** mean creating a decent config is an easy task! You will need
to put effort towards understanding all of Terra's components in order to be successful. Be sure to **ask for help** if
you need it! We'll be happy to help you in our [Discord server](https://discord.gg/PXUEbbF).