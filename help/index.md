# AASX Package Explorer - General help

## License

Copyright (c) 2018-2019 Festo AG & Co. KG (https://www.festo.com/net/de_de/Forms/web/contact_international), author: Michael Hoffmeister
This software is licensed under the Eclipse Public License - v 2.0 (EPL-2.0) (see https://www.eclipse.org/org/documents/epl-2.0/EPL-2.0.txt).
The browser functionality is under the cefSharp license (see https://raw.githubusercontent.com/cefsharp/CefSharp/master/LICENSE).
The JSON serialization is under the MIT license (see https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md).

## Commandline options

| Option         | Argument     | Description                                                             |
|----------------|--------------|-------------------------------------------------------------------------|
| -maximized     |              | causes program window to fill entire screen                             |
| -noflyouts     |              | uses modal dialogues insteand of transparent overlays in main window    |
| -left          | \<pixel\>    | left position of the main window                                        |
| -top           | \<pixel\>    | top position of the main window                                         |
| -width         | \<pixel\>    | width of the main window                                                |
| -height        | \<pixel\>    | height of the main window                                               |
| -id-aas        | \<template\> | template string for generation of AAS identifiers.                      |
| -id-sm-template| \<template\> | template string for generation of Submodel (template) identifiers.      |
| -id-sm-instance| \<template\> | template string for generation of Submodel (instance) identifiers.      |
| -id-cd         | \<template\> | template string for generation of ConceptDescription identifiers.       |
| -eclass        | \<path\>     | path to a sub-directory, which contains eCl@ss XML files                |
| -twopass       |              | apply second search operation to join multi-language information        |
| -intbrowse     |              | use always internal browser                                             |
| -logo          | \<file\>     | path to a file containing a logo (height < 40pixel) to be shown         |
| -aasxrepo      | \<file\>     | path to a file containing JSON definitions for assit-id to file maps    |
| -qualifiers    | \<file\>     | Path to JSON file defining qualifier presets.                           |
| -contenthome   | \<URL\>      | URL to show in content browser on startup, on change of AASX            |
| -splash        | \<time ms\>  | If not -1, then time in ms for the splash window to stay on screen      |
| -options       | \<file\>     | read text file, which contains options (in same syntax)                 |
| -backupdir     | \<path\>     | points to writeable folder, creating backups of the AasEnv in XML       |
| -c0..-c3       | \<color\>    | Set brandlabel accent color (see below) in WPF format, e.g. #ff334455   |
| -dll           | \<file\>     | path to plugin-dll to load (might auto-load furter dll's in its directory) |
| -resthost      | \<host\>     | Hostname for the REST server. If not "localhost", use of admin rights might be required. |
| -restport      | \<port\>     | Port for the REST server. Port numbers below 1023 may not work.         |
| -rem           | \<remark\>   | Add a remark. Intended use: disabling next argument.                    |
                                                                                   
\<template\> = Template string may contain an arbitrary number of 'D', 'X', 'A'characters and orthers. The former will be mapped to 1..n digit of an generated unique id in decimal, hexadecimal or alphanumerical form.

Color numbers: 0 = "LightAccentColor", 1 = "DarkAccentColor", 2 = "DarkestAccentColor", 3 = "FocusErrorBrush"

## Syntax of Qualifier-Presets

JSON-File, e.g. named 'qualifier-presets.json'. Structure like this:

    [
      {
        "name": "Value processing | median",
        "qualifier": {
          "semanticId": {
            "keys": [
              {
                "type": "GlobalReference",
                "local": false,
                "idType": "IRDI",
                "value": "0112/2///61360_4#AAF583"
              }
            ]
          },
          "qualifierType": "value proc qual",
          "qualifierValue": "MED",
          "qualifierValueId": {
            "keys": [
              {
                "type": "GlobalReference",
                "local": false,
                "idType": "IRDI",
                "value": "0112/2///61360_4#AAF594"
              }
            ]
          }
        }
      },
      {
         [..]
      }
    ]
    
## Syntax of AASX Repository

This repository will be loaded, when the -aasxrepo commandline argument is set and the "File / Query AASX repository" or F12 is activated. The "filemaps"-array maps assetIds to filenames, which can be immediately loaded. The "tag" property is used for display in the screen, while the "description" property will be used for print out by "File / Print 2D code sheet for repository". Here, the "code" property will control, if a data matrix code ("DMC") or a QR-Code ("QR") will be printed.


    {
      "filemaps": [
        {
          "assetid": "HTTP://PK.FESTO.COM/3S7PLPGNH1T",
          "description": "Festo USB Stick",
          "tag": "F",
          "code": "DMC",
          "fn": "C:\\Users\\miho\\Desktop\\AasxPackageExplorer\\Sample_AAS\\Festo-USB-stick-sample-admin-shell.aasx"
        },
        {
          "assetid": "http://pk.pf.com/40000039198163",
          "description": "P+F Laser Sensor",
          "tag": "PF",
          "code": "QR",
          "fn": "C:\\Users\\miho\\Desktop\\AasxPackageExplorer\\Sample_AAS\\pf_232769_40000039198163.aasx"
        },
        {
          "assetid": "www.phoenixcontact.com/asset/product/2404267",
          "description": "Phoenix Contact Control",
          "tag": "PC",
          "code": "QR",
          "fn": "C:\\Users\\miho\\Desktop\\AasxPackageExplorer\\Sample_AAS\\Phoenix Contact AXC F 2152 - 11.aasx"
        }
      ]
    }
