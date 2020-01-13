# synology_iperf3
Instructions to run IPERF3 in Synology Docker Container

I had to troubleshoot a network performance issue and needed a place to run iperf3. A quick search turned up a few examples of people using their Synology NAS units. Those links all led to instructions that required SSH access to the Synology unit. I wanted a solution that didn't require SSH as I typically keep it turned off on my devices.

The solution below allows a user to setup an iperf3 server on a Synology NAS using only the DSM GUI.

(See images in the repo for actual configuration screen captures)

Steps (assumes you have Docker already installed)

1. Open Docker application go to the registry and search for iperf3. 
2. Download the official container which should be on the top of the list labeled as networkstatic/iperf3.
3. Go the the Image tab and confirm the container is downloading.
4. Once downloading is complete, select the iperf3 image and click the launch button.
5. You should now be on the General Settings tab. Click the Enable Resource Limitations check box and enable High CPU Priority and allocate 4096 of memory. Then click Apply
6. Under Advanced Settings, click on Port Mapping tab and add two lines to forward port 5201 UDP + TCP then click Apply
7. Under Advanced Settings, click on Environment tab and add the following Exection Command: networkstatic/iperf3 -s then click Apply

Run your container and you should now be able to reach the iperf3 server from an iperf3 client.

This setup is known to work on DSM 6.1.
