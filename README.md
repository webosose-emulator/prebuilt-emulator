# webOS OSE emulator README

webOS OSE emulator is a tool that enables you to test the features of webOS OSE on your PC.

webOS OSE emulator is an x86 (x86_64) virtualization system based on QEMU virtualizer. Currently, the emulator only supports Linux Ubuntu as a host operating system.

## Source codes
Source codes for qemu binary and virglrendere lib are:
* qemu : https://github.com/webosose-emulator/qemu
* virglrenderer : https://github.com/webosose-emulator/virglrenderer

## How to run the emulator

Use the run script (`emulator`) to launch webOS OSE emulator easily.

### Portable environment

* Run script requires a JSON configuration file (`webos-config.json`) to execute the emulator.
* You should create a custom JSON configuration file.
    * Refer to the [JSON configuration file](#json-configuration-file) section for more information.
* To run the emulator using the custom configuration, type the command in the following form.
    * `./emulator <JSON configuration file path>`

#### In Ubuntu 18.04

* You need to launch the script with `sudo` command, because of KVM permission.
    * `sudo ./emulator <JSON configuration file path>`

## JSON configuration file

The JSON configuration file (`webos-config.json`) includes emulator options.

### Sample `webos-config.json`

```json
{
    "description":"qemux86",
    "name":"webos-image-qemux86-master-20180524053534",
    "vmdk_file_path":"~/Downloads/webos-image-qemux86.vmdk",
    "hw.core":"1",
    "hw.ramSize":"1024",
    "hw.accel":"true",
    "hw.gl.accel":"true",
    "debug":"false",
    "portforwarding.SSH":"6622",
    "portforwarding.inspector":"9998"
}
```

### Options

* `description`
    * Emulator description
* `name`
    * The name of the guest
* `vmdk_file_path`
    * The path to the guest image file in the local filesystem
    * It is recommended to use the absolute path.
    * The relative path is converted to an absolute path based on JSON configuration file path.
* `hw.core`
    * Emulator CPU core count
    * Default is (Host CPU count)/2
* `hw.ramSize`
    * Emulator RAM size (default unit is MB)
    * Available size units: M(MB), G(GB).
    * Minimum value is 1024(M/MB).
    * Examples
        * Use number only: 1024
        * Use with unit: 1024M
        * Use with full unit: 2GB
* `hw.accel`
    * Enable host HW acceleration
* `hw.gl.accel`
    * Enable OpenGL ES acceleration
* `debug`
    * Enable console debug
* `portforwarding.SSH`
    * Port for SSH connection
    * Command example to connect from the shell
        * `ssh -p <PortNumber> root@localhost`
* `portforwarding.inspector`
    * Port for Web Inspector
    * Address format to connect from the web browser
        * `localhost:<PortNumber>`

## Documentation

For full documentation of webOS OSE emulator and other developer tools, visit http://webosose.org/develop/sdk-tools/.
