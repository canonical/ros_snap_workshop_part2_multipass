# ros_snap_workshop_part2_multipass
ROS snap workshop part 2 multipass configuration

The cloud-init configuration will setup an Ubuntu 20.04 VM with ROS noetic installed

## Launch the VM
Before launching the VM you will need to [install multipass](https://multipass.run/install)
On Linux run:
```
sudo snap install multipass
```
then run the VM by calling:
```
multipass launch --cpus 2 --disk 20G --cloud-init ./cloud-init.yaml 20.04 --name workshop-part2 --timeout 1000
```
## Attach the VM
To attach a simple shell:
```
multipass shell workshop-part2
```
To attach with X11 forwarding:
```
ssh -X ubuntu@$(multipass list --format csv | awk -F, '$1=="workshop-part2"{print $3}')
```
The password is then: `ubuntu`

To attach the VM on MacOS and Windows, please refer to the [documentation](https://multipass.run/docs/set-up-a-graphical-interface#heading--using-x11-forwarding).

