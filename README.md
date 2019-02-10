# wia-cmd-scanner

This (very) small utility (~30 KB executable) provides an easy to use command-line interface to WIA-compatible scanners for Windows OS. If scanner is accessible using `Windows Fax and Scan` application, it is very likely to be compatible with this tool. Compiled binaries can be downloaded from [Releases](https://github.com/nagimov/wia-cmd-scanner/releases)

The utility is built around WIA (Microsoft Windows Image Acquisition Library). Depending from version of Windows OS, WIA library (included file `Interop.WIA.dll`) can be required to be placed next to `wia-cmd-scanner.exe` executable. No other external dependencies are required (targeted .NET framework 3.5 comes pre-installed starting from Windows 7). The utility is portable and requires no installation. Both 32-bit and 64-bit versions of Windows OS are supported.

## Usage

```
Usage: wia-cmd-scanner [OPTIONS]...                                           
                                                                              
All arguments are mandatory. Arguments must be ordered as follows:            
                                                                              
  /dpi {150,200,300,600}          scan resolution, dots per inch              
  /color {RGB,GRAY,BW}            scan color mode                             
  /format {BMP,PNG,GIF,JPG,TIF}   output image format                         
  /output FILEPATH                path to output image file                   
                                                                              
e.g.:                                                                         
  wia-cmd-scanner /dpi 300 /color RGB /format PNG /output .\scan.png          
```

## Build

The utility is compiled using Microsoft Visual Studio 2012 Express.

No Visual Studio project files are provided, since the code can be imported into Visual Studio project from scratch in few easy steps (shown according to Visual Studio 2012 layout):

* `File` -> `New Project`
* `Installed` -> `Templates` -> `Visual Basic` -> `Windows` -> `Console Application`
* copy-paste code from [`wia-cmd-scanner.vb`](https://github.com/nagimov/wia-cmd-scanner/raw/master/wia-cmd-scanner.vb) to `Module1.vb` (empty file will be opened in editor)
* right-click on `ConsoleApplication` in `Solution Explorer` and choose `Add Reference...`
    + choose `COM` -> `Type Libraries`
    + search for `image` and select `Microsoft Windows Image Acquisition Library v2.0`
* compile via `BUILD` -> `Build Solution`

## Scripting and automation

Build your own automation tools around `wia-cmd-scanner.exe` binary using batch/powershell, or check out the source code.

The project is simple and tiny (~130 lines of VB code) and very easy to modify to fit your own needs.
