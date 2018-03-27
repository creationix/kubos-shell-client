How to test on a beaglebone black.

On beaglebone run shell-service:

```sh
debian@beaglebone:~$  kubos-shell-service
```

Also run communication service.  Here I configured the bone to have UART4
enabled and connected it to the host computer via a serial to usb cable.

```sh
debian@beaglebone:~$ kubos-communication-service serial /dev/ttyO4 115200
```

Now on the host, run the other half of the communication service:

```sh
tim@t580:~$ kubos-communication-service serial /dev/ttyUSB1 115200
```

And now the shell client can be built and tested:

```sh
tim@t580:~$ lit make github://kubos/kubos-shell-client
tim@t580:~$ ./kubos-shell-client
```

This will drop you into a bash shell on the beagle bone communicating over the
serial line.
