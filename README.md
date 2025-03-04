# i308-calib
Calibration tool


## Installation:

Can be installed via pip:
    
    pip install -qq git+https://github.com/udesa-vision/i308-calib.git


## Camera Calibration

### Quick Start

run the monocular calibration tool cli command:

    calib-tool

### Arguments

- **video** str or int. 
Specifies the video device, on linux might be something like `/dev/video<N>`

- **resolution** str (optional)
 the requested resolution in the format "`<width>`x`<height>`" in pixels

- **checkerboard** str (optional) default=10x7
 the checkerboard layout in the format "`<width>`x`<height>`" in number of squares

- **square-size** str (optional) default=24.2
 the checkerboard square size in millimeters 

- **config** str (optional)
a .yaml configuration file


### Examples

calibrate camera 0 with default parameters:

    calib --video 0


calibrate with custom parameters:

    calib --video /dev/video3 --resolution 640x480 --checkerboard 9x6 --square-size 32.0 --data data_dir


calibrate with capture configuration file:

    calib --config cfg/capture.yaml



### Configuration File

Some configuration files are provided.

In order to copy the configuration files to the working directory run the command:

```bash

 copy-configs

```

This should create the folder `cfg/` with some configuration files.

Example of capture configuration file (.yaml):

```yaml

    # video device, on linux might be /dev/video<N>
    video: 0

    # name: str (optional)
    #   a name to identify the device
    name: My Cute Camera

    # resolution: str (optional)
    #   requested resolution in the format "<width>x<height>" in pixels
    resolution: 640x480


```


### Overwriting configuration parameters
Some configuration file parameters can be overwritten with command line arguments.

For example, the following command will use the configuration file but in the video 3.

    calib --video 3 --config cfg/capture.yaml 


## Stereo Calibration

run the stereo calibration tool cli command:

```bash
    calib-stereo
```

You can use the same arguments of the monocular tool for the stereo tool, for example:

```bash

    calib-stereo --video /dev/video3 --resolution 1280x480 --checkerboard 9x6 --square-size 32.0 --data data/stereo

```

### Configuration file
A configuration file for the Stereo camera ELP-USB3D1080P02 is provided.

To get the configuration files, run the command:

```bash

 copy-configs

```

And then edit in `cfg/stereo.yaml` and then ddapt it to your needs.

After that you can run the stereo tool using that configuration file:

```bash

    calib-stereo --config cfg/stereo.yaml

```
