# backblaze-backup
This is not a BackBlaze official script. This script is published to help the community backup their files inside of BackBlaze service.

This backup script is capable of create, send and remove backups of the following hosting panels:
- VestaCP
- HestiaCP
- Cyberpanel

If you do not want to use any hosting panel schema, we will also provide a way to you give one or more directories and the script will take care.

# Features implemented and TO DO
| Feature | Status |
| - | - |
| hestiacp backup | TO DO |
| vestacp backup | TO DO |
| cyberpanel backup | TO DO |
| multiple extensions | TO DO |
| log to audit the backup | TO DO |
| zabbix notification script | TO DO |
| backblaze-backup script examples | TO DO |
| upgrade blackbaze binary script | TO DO |
| script to remove backblaze setup | TO DO |

# how to install
1. Execute the installer. It will install the latest stable and official backblaze binary for Linux x85_64
```bash
bash install.sh
```
2. Configure the BackBlaze credentials. Change the "applicationKeyId" and "applicationKey" to the respective credentials that you created inside of BackBlaze dashboard.
```bash
backblaze authorize-account applicationKeyId applicationKey
```
# backblaze-backup.sh parameters explained
- The script backblaze-backup need some parameters to understand what you want to do.
- All of them are mandatory, you can not skip anyone.
- After you create and test your backup, you can create a cronjob under root credentials.

Generic use of the script:
```bash
/usr/bin/bash /usr/bin/backblaze-backup.sh parameter1 parameter2 parameter3 parameter4 etc
```

### parameter 1
Provide which kind of environment you have.

The options are:
- hestiacp
- vestacp
- cyberpanel
- "/absolut/path/directory1 /absolut/path/directory2 /absolut/path/directory3 ... /absolut/path/directoryN"

Notes:
- If you provide a list of directories instead of hosting panel, please separate them using spaces and do not remove the double quotes or they will fail. The quotes will make all directories as only one parameter, the parameter 1.
- The directory path must be absolut.

### parameter 2
Do you want to remove the backup after it was successfully sent to BackBlaze?

The options are:
- yesRemoveAfterSent
- notReMoveAfterSent

### parameter 3
By default the script will try to use /backup to create hosting panel backup temp files to send them. Some panels allow to specify a directory to create the temp files. If you want to provide a specific directory, you need to provide the custom directory as the parameter 3. This can help when you does not have enough space in the / (root) to create backups.

Notes:
- If the hosting panel does not provide this possibility, the /backup will be used.
- If you provide a custom directory, this script will not try to create if it not exist. Please guarante that the directory exist or the script will abort.
- You can provide multiple directories. Make sure they are separated by spaces and do not remove the double quotes.
- The directory path must be absolut.

The options are:
- default
- /absolut/path/directory1
- "/absolut/path/directory1 /absolut/path/directory2 /absolut/path/directory3 ... /absolut/path/directoryN"


### parameter 4
Do you want just backup files with specific extension? If yes, then this is the parameter to be configured. The default option will find for every file extension.

The options are:
- default
- .extension

Extensions example:
- .tar.gz
- .bz2
- .tar
- .zip

Notes:
- You can use any extension that you want.
- Make sure it start with the dot (".zip" and not just "zip").
- At the moment this script not provide implementation for multiple extensions.

### parameter 5
This parameter you can control which accounts will be copied to BackBlaze.
If you will just provide directories to send the files, please choose the "none" option. If you provide a hosting panel option in the parameter 1, then please choose if you want create and copy backups of all acounts or just active accounts (suspended accounts will not be copied).

The options are:
- none
- all
- active

### parameter 6
Provide the BackBlaze bucket name. Please garantee that the name is correct. The name is case sensitive, so be sure about the buck name.

The options are:
- bucketname


