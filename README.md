tor_forced_tunnel
=================

A set of scripts used to created a tor transparent proxy on
macOS. MIT Licensed.

This project is created for experimental and educational
purposes only.

- `./build`: Automatically download, configure, and compile tor.
- `./prepare`: Prepare the system for transparent proxy.
- `./start`: Start the transparent proxy.

## Usage

You must complete step 1 if you are running the transparent
proxy on macOS for the first time, after which you can jump to
the second and third step.

### 1. Compiling tor with Transparent Proxy support

Before running the build script, make sure you have the latest
Xcode and all necessary libraries installed. Tor needs libevent,
zlib, and openssl in order to compile. Assuming you use Homebrew:

```sh
$ brew install openssl zlib libevent # Install dependencies
$ ./build # Run the build script
```

Tor needs to be modified in order to be compiled on macOS with
transparent proxy support. All necessary patches will be applied
automatically by the build script. See `/patch` directiory.

### 2. Prepare the systems

In order to make the transparent proxy function correctly, you
will need to load the `pf.conf` ruleset and adjust the system
packet forwarding settings. The script `prepare` is designed to
automatically complete these steps.

```sh
$ ./prepare # Run the prepare script
```

### 3. Start the transparent proxy

The final step of setting up the transparent proxy is to run the
`start` script. This will automatically start and configure tor
in transparent mode.

```sh
$ ./start <target device IP address> # Run tor in transparent mode. Example: ./start 192.168.1.200
```

You may manually configure the gateway of your target device to your
computer's IP address. For iOS, goto `Settings` -> `Wi-Fi` ->
Tap the `(i)` icon -> `Configure IP` -> Change to `Manual` ->
Set `Router` to your computer's IP Address.

If you have the necessary utilities, you may skip the above step.

