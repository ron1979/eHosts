# eHosts

eHosts is an enhanced hosts file that supports regex domain name matching (it is actually a dns proxy run on udp 53 port, so the priority is lower than the rules in system's hosts file).

Note: it is at very early stage and is written just for fun in rust-lang.

It is built on rust nightly and tested on GNU/Linux.

## Download binary file

If you are on x86_64 GNU/Linux platform, then you can download binary file from [eHosts for x86_64 Linux](https://raw.githubusercontent.com/archion/eHosts/master/target/x86_64-unknown-linux-gnu/release/eHosts) and run `sudo ./eHosts`

## Building from Source

```
$ git clone https://github.com/archion/eHosts
$ cd eHosts 
$ sudo cargo run --release
```

## Usage
First adding regex rules in hosts file (if you don't have permission to edit system hosts file like `/etc/hosts`, you can create a file named `hosts` in the current directory instead) start with `#$`, for example, if you want to match all domain name that contain `.google.com` to ip `192.168.0.1`, you may add in hosts file like:

```
#$ 192.168.0.1 .*\.google\.com
```
if you want to access google service in China, you may add below lines in your hosts file(note to replace `x.x.x.x` with a valid google ip, if you don't know how to find a valid google ip, see [here](http://archion.github.io/2014/06/18/%E8%87%AA%E5%AF%BB%E8%B0%B7%E6%AD%8C%E6%8C%A8%E5%B1%81/))
```
#$ x.x.x.x .*google.*\.com.*
#$ x.x.x.x .*gstatic\.com
#$ x.x.x.x .*ggpht\.com
#$ x.x.x.x .*youtube.*\.com.*
#$ x.x.x.x .*ytimg\.com
```
and changing dns server setting to `127.0.0.1` (on Linux, eHosts will set the dns for you by adding `nameserver 127.0.0.1` in /etc/resolv.conf).

`eHosts -h` for more options.
