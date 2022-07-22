# Kernel modules

## Getting info

What kernel modules are currently loaded:

    $ lsmod

About a specific module:

    $ sudo modinfo [module_name]

Configuration of all the modules:

    $ sudo modprobe -c | less

Configuration of a particular module:

    $ sudo modprobe -c | grep [module_name]

Listing dependencies of a module (or alias), including the module itself:

    $ sudo modprobe --show-depends [module_name]

Manual loading and unloading

To load a module:

    # modprobe [modulename]

To unload a module:

    # modprobe -r [modulename]

## Blacklisting

Blacklisting is a mechanism to prevent a kernel module from loading. This could be useful if, for example, the associated hardware is not needed, or if loading that module causes problems: for instance there may be two kernel modules that try to control the same piece of hardware, and loading them together would result in a conflict.
