## This repository will be having a guide to run your binary code over Raspberry Pi.

### Requirement
  - A configured Raspberry Pi 
  - Another Sytem (preferably Unix based <3)
  - Patience and preferably some coffee too

### Quick Steps:
  - Compiling Go Code on source machine 
  - Transferring it over the Rpi
  - Running it

`Note: Keep your RPi and host system on the same network.`

## Procedure

**At your Raspberry Pi end:**
Access your Rpi and enter the following command to get it's local IP:
> $ ip addr

**At Host end:**

Write a Go Program with your preferable editor, then open terminal and enter

```sh
$ env GOARCH=arm64 GOOS=linux go build -o <output-name> <file-name>
```

For eg on my sytem: `$ env GOARCH=arm64 GOOS=linux go build -o test main.go`

The **GOOS** and **GOARCH** inform the compiler about the Operating system and the System Architecture. (In accordance with the Rpi configuration).

Next let's transfer this generated binary over to your Rpi and run it there. We will use secure copy protocol for this.

> $ scp *<location-of-binary-file>* *<Rpi's user-name>*@*<Rpi's IP address>*: *<location-of-file-transfer on Rpi>*

For eg on my system: `$ scp ~/Desktop/go-rpi/test ubuntu@192.168.x.x:/home/ubuntu`

So the binary file **test** got transferred to here */home/ubuntu*
You can ssh from your host machine also and run that file like the following:

> $ ssh *<Rpi's user-name>*@*<Rpi's IP address>*

Enter the prompted password (asked for the first time)

Now go to that location and run the 

```sh
$ cd <location-where-you-copied-your-file>
$ ./<file-name>
```

For eg on my system: `$ cd /home/ubuntu` and then run it with `$ ./test `

# AND BAMM !!!


