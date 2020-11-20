# PlatformIO installation

It is now possible to use PlatformIO as development platform instead of the Arduino IDE.  PlatformIO simplifies the management of dependencies. You can use either the command line tools of PlotformIO Core, or PlatformIO IDE as plugin to your favourite IDE.

Please refer to https://platformio.org/install for details on PlatformIO installation.

Below is just one way how to install PlatformIO Core command line in a separate Python virtual environment. You can use the IDE flavour of your choice equally well.  It should be easy to find tutorials for installing PlatformIO IDE online.

## Setup
(Linux or MacOS; Windows might require minor changes to commands)

(First command only if virtualenv is not yet installed already; I assume Python is already installed):
```
pip install virtualenv
virtualenv ~/.platformio/penv
```
You might have to set environment variables correctly for Python 3 (for setup and for use below) -- use any locale that is installed:
```
export LC_CTYPE=de_DE.UTF-8
export LANG=de_DE.UTF-8 
```

## Use

Setup environment and compile code (will install all dependencies automatically)
```
. ~/.platformio/penv/bin/activate
pio run -e ttgo-lora32-v1
```

Upload code (will also compile code automatically) and file system data to board:
```
pio run -e ttgo-lora32-v1 --target upload
pio run -e ttgo-lora32-v1 --target uploadfs 
```

Note: The environment ttgo-lora32-v1 will create a binary image that is compatible with all [[Supported Boards]].
