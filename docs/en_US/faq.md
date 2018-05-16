# FAQ

### What is the difference between MiFlora and BLEA
> MiFlora only manages plants, BLEA is a plugin for all Bluetooth LE objects, so it is much more complex,
it needs dependencies, has a daemon system, it is suitable to handle a multitude of Bluetooth LE object types
but needs more monitoring and maintenance, mostly demons and dependencies when updating

### Does this plugin rely on third-party APIs?

> The plugin uses Bluetooth to retrieve information from MiFlora.
You need to install Bluetooth and make sure that `gatttool -b macAddMiFlora --char-read -a 0x35` is running on the target device.

### Does this plugin monopolize Bluetooth?

> Not at all, he needs Bluetooth for each statement, see next question for more details on the number of readings per day.


### How many times a day are the measurements retrieved?

> It is defined in the global configuration of the plugin, for all objects: every 15 minutes to every 12 hours.
It is possible to configure a different frequency for each MiFlora, `default` allows to use the global frequency.

> I use the modulo of the current time with the frequency entered in parameter. +
Warning: in debug mode, data is retrieved continuously regardless of the configuration.

> The static information (battery, device name, firmware version) is retrieved every 12 hours: at midnight and noon.


### Which firmware version is this plugin compatible with?

> It is compatible with all versions known to date (2.9.2) since version 1.0 of the plugin.


### I have a RPI3, I had to disable the internal Bluetooth to not have interference with the Zwave (razberry). Should I always keep the internal Bluetooth off to solve this problem? If not, does any BT USB stick fit the MiFlora and RPI3?

> Dans ce cas il faut prendre un dongle BLE. Le problème avec le razberry c'est seulement si on utilise le contrôleur interne.


### I wish to contribute to the improvement of this plugin, is it possible?

> Bien sur, le code est sur GitHub : rjullien/plugin-MiFlora, vous pouvez soumettre des pull requests.

### gatttool is unstable and hangs on RPI

> There is a lot of configuration that can cause this problem. With Pixel you have to be careful to have a single bluetooth manager.
BlueZ is incompatible with blueman (sudo apt-get remove blueman)

### The plugin works well: what can I do with it?

> Les valeurs d'humidité, de fertilité, de luminosité et de températures sont accessible depuis des scénarios.

> Il est possible de lire ces valeurs, de les comparer à un seuil et d'alerter en cas de dépassement du seuil, par exemple pour arroser une plante.

> Les alertes peuvent être données par du 'text to speech' (plugin playTTS par exemple), par notification sur smartphone (plugin pushbullet), par SMS ...

> Les seuils peuvent être trouvés en utilisant la base de plantes de Xiaomi ou celle de Parrot à défaut un seuil entre 14 et 16 semble convenir à une majorité de plantes d'intérieur.

> Il est aussi possible de réguler un arrosage automatique, MiFlora semble bien résister aux intempéries

