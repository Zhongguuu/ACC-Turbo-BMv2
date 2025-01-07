# ACC-Turbo-BMv2

### Ensure Required Environments Are Installed:

Make sure the P4 environment and Python environment are installed. Refer to the [p4lang/tutorials: P4 language tutorials](https://github.com/p4lang/tutorials) for guidance.

### Prepare the Workspace:

Navigate to the `/ACC-Turbo-BMv2` directory. Copy the `v1model.p4` file into the environment, replacing the existing `v1model.p4`. Ensure that the versions match.

### Start  Simulation:

Execute the following command:

```
sudo p4run
```

#### Open Mininet Terminals:

After compilation, execute the following in Mininet:

```
xterm h1 h2 h3 s1
```

#### Run the Control Plane Program:

In terminal s1, run the control plane program:

```
python3 controller.py
```

#### Start Packet Capture on Host h2:

In terminal h2, start tshark to listen for packets:

```
tshark -i h2-eth0 -w save.pcap
```

#### Replay Traffic on Host h1:

In terminal h1, replay the packet capture file at a high rate:

```
tcpreplay -i h1-eth0 -x 100.0 output.pcap
```

#### Replay DDoS Traffic on Host h3:

In terminal h3, replay the DDoS packet capture file at a lower rate:

```
tcpreplay -i h3-eth0 -x 1.0 dos.pcap
```



