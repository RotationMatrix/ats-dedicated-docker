# American Truck Simulator Dedicated Docker

This repository contains a docker compose setup for American Truck Simulator's
dedicated server. It should also run well with podman.

## Usage

First install the dedicated server.

```bash
$ sudo docker-compose run install
```

Then start it once to generate the default configuration files.

```bash
$ sudo docker-compose up
```

After this, create your `server_packages.dat` and `server_packages.sii` files
and move them to `data/American Truck Simulator`. See the [Create Server Packages](#create-server-packages) section for how to create these. Once those files are
in place, run the above command again to start the server. If you have
configured a `steam_login_token` and port forwarding to the container, you
should see your server in the Convoy server list. Otherwise a temporary Session
search ID should be printed in the `server.log.txt` which you can type into the
search bar to find your dedicated server.

```
00:00:00.391 : [MP] -------------------------------------------------------------------------
00:00:00.391 : [MP] Server init
00:00:00.429 : [MP] LogOn Anonymous
00:00:01.564 : [MP] Steam connected
00:00:01.564 : [MP] Settings init
00:00:01.564 : [MP] Init steam game server params
00:00:01.565 : [MP] Initiate server-client.
00:00:01.565 : [MP] Session started.
00:00:01.565 : [MP] Server created.
00:00:01.565 : [MP] =========================================================================
00:00:01.565 : [MP]
00:00:01.565 : [MP] Session search id: 00000000000000000/101
```

Example log output with a Session search id.

## Create Server Packages

The server packages `.sii` and `.dat` files contain information about your current map, DLC and mod configurations and are required to run the dedicated server. These files can be exported from the main game using the following process.

1. Open your game configuration file. It should be located in one of the following locations depending on your platform.

Windows:

```
C:\Users\USER\Documents\American Truck Simulator\config.cfg
```

or

```
C:\Users\USER\OneDrive\Documents\American Truck Simulator\config.cfg
```

macOS:

```
~/Library/Application Support/American Truck Simulator/config.cfg
```

Linux:

```
~/.local/share/American Truck Simulator/config.cfg
```

2. In your `config.cfg` find `g_console` and set it to one.

```
uset g_console "1"
```

3. Save your configuration file and launch the game.
4. Load your profile in game and open the console (press "~").
5. In the console, type `export_server_packages` and press enter.
6. The server packages should be exported to the same directory as your configuration file above. Copy these to `data/American Truck Simulator` in your dedicated server directory.
7. Optionally, you can edit your configuration file to restore the `g_console` setting to `"0"`.

## References

- [SCS Dedicated Server Documentation](https://modding.scssoft.com/wiki/Documentation/Tools/Dedicated_Server)

## License

[![CC0](https://i.creativecommons.org/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors to this project have waived
all copyright and related or neighboring rights to the files contained in this
repository. See [LICENSE](LICENSE.md) for details.

## Disclaimer

This project is not affiliated with or endorsed by SCS Software s.r.o.
