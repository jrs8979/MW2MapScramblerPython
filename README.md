# MW2MapScramblerPython

This was written with the [IW4x](https://xlabs.dev/) project in mind. It is a small tool to randomize the map list found in the server settings file. This was very annoying for me to do by hand as it could take upwards of 10 minutes each time. IW4x does not support automatic map list scrambling so I made it myself.

## Arguments

| Argument         | Required                                                                                                                                                                                                                     | Description                                                                                                                                                                                | Example                                                                                                            |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `MapFile`        | :heavy_check_mark:                                                                                                                                                                                                           | Path to the map file. Can be relative. Goes at the end of the script invocation.                                                                                                           | `python scrambler.py -l -p "mp " /c/MW2Server/maps.txt`, `python scrambler.py -l -p "mp " "C:\MW2Server\maps.txt"` |
| `--ServerFile`   | :cross_mark:                                                                                                                                                                                                                 | Path to server.cfg file. Can be relative.                                                                                                                                                  | `--ServerFile /c/MW2Server/server.cfg`, `--ServerFile "C:\MW2Server\server.cfg"`                                   |
| `--PreArg`       | :cross_mark:                                                                                                                                                                                                                 | Arguments that go before the map list. Note that spaces or new lines at the end will not be added by the script, so they must be present in the string given.                              | `--PreArg "set sv_hostname \"^:ThatGuyinPJ's Bots Server\" set g_gametype \"war\" set sv_maprotation " `           |
| `--PostArg`      | :cross_mark:                                                                                                                                                                                                                 | Arguments that go after the map list. Note that spaces or new lines at the beginning will not be added by the script, so they must be present in the string given.                         | See `--PreArg` example.                                                                                            |
| `--ArgSliceChar` | :cross_mark:                                                                                                                                                                                                                 | An alternative to `--PreArg` and `--PostArg`, place a character in your server.cfg file directly before and after the map list. This **CANNOT** be used with `--PreArg` **OR** `--PostArg` | `"%"`                                                                                                              |
| `-l`, `--list`   | Specifies if you want it output to a list file instead of to your sever.cfg file. Not to be used with `--ServerFile`. Can be used with `--Prefix` and `--PostFix` if desired. Will ignore `--ArgSliceChar` if it is present. | N/A                                                                                                                                                                                        |
| `-p`, `--prefix` | Prefix for map names if the game requires it(e.g. mp [map name]). Spaces will not be added to the end of this string.                                                                                                        | `-p "mp "`                                                                                                                                                                                 |