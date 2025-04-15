This fork of OpenWrt 23.05 includes a patch that adds a weighted round-robin (WRR) classless network scheduler to the Linux 5.15 kernel.

The network scheduler contains three queues and uses the priority field in the skb header to assign the packet to a queue. The scheduler then iterates through each queue and dequeues a number of packets propotional to the priority of the queue.

## Testing
- Run `make kernel_menuconfig`
- Enable the WRR scheduler under Networking support/Networking options/QoS and/or fair queueing/Weighted round-robin scheduler (WRR)
- Save the config and compile OpenWrt for your device
- Use `tc` to change the networking scheduler (Requires the tc-full package to be enabled)

> [!NOTE]
> This scheduler was built for learning purposes and is not meant to be used for serious tasks. If you choose to do so, you do it at your own risk.
