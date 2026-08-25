                                                     BFD multi-vendor exercise 


NOTE: The CISCO-XRD image only works on Intel chips; my server is a Mac Mini with an MDA chip and it doesn't work there, so I had to do it on a ThinkPad Laptop.

Download the cisco image with the following command:

docker pull sbezverk/xrd-control-plane:25.2.1

<img width="573" height="120" alt="image" src="https://github.com/user-attachments/assets/38ac10f9-4413-456e-a0f9-098ff9493a29" />



After, you can check the down with the following command on you server:

docker images

<img width="673" height="128" alt="image" src="https://github.com/user-attachments/assets/59b33351-5f4f-45d0-b7b6-4dd1bb32629e" />



NOTE: If you get this error on Router Cisco when deploying the lab

└──> docker logs -f clab-BFD-R1
ERROR - Not enough inotify instance resource available for new XRd instance.
Current settings are 512 max_user_instances and 1048576 max_user_watches.
Each XRd instance is expected to need 4000 of each - please consider
setting the limits high (e.g. 64000, or higher).
[ERROR  ] Insufficient inotify resources
[ERROR  ] XRd hit a critical error during initialization and has aborted launch



Fix: run the following commands:

sudo sysctl -w fs.inotify.max_user_instances=64000
clab destroy 
clab deploy














