# AASX Package Explorer - General help

## License

Copyright (c) 2018-2019 Festo AG & Co. KG (https://www.festo.com/net/de_de/Forms/web/contact_international), author: Michael Hoffmeister
This software is licensed under the Eclipse Public License - v 2.0 (EPL-2.0) (see https://www.eclipse.org/org/documents/epl-2.0/EPL-2.0.txt).
The browser functionality is under the cefSharp license (see https://raw.githubusercontent.com/cefsharp/CefSharp/master/LICENSE).
The JSON serialization is under the MIT license (see https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md).

## Commandline options

| Option     | Argument   | Description                                                             |
|------------|------------|-------------------------------------------------------------------------|
| -maximized |            | causes program window to fill entire screen                             |
| -noflyouts |            | uses modal dialogues insteand of transparent overlays in main window    |
| -left      | <pixel>    | left position of the main window                                        |
| -top       | <pixel>    | top position of the main window                                         |
| -width     | <pixel>    | width of the main window                                                |
| -height    | <pixel>    | height of the main window                                               |
| -id-aas    | <template> | template string for generation of AAS identifiers.                      |
|------------|------------|-------------------------------------------------------------------------|


<template> = Template string may contain an arbitrary number of 'D', 'X', 'A'characters and orthers. The former will be mapped to 1..n digit of an generated unique id in decimal, hexadecimal or alphanumerical form.
