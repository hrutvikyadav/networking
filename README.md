# Networking

## Basics

1. Open System

   A system _connected_ to the internet and _ready for communication_

2. Closed System

   A system _connected_ to the internet but _not ready for communication_

3. Network

   __Inteconnection__ of multiple devices or  _hosts_
   connected using multiple paths\
   Enables sending/ receiving data\
   Other __Network devices__ also present in the network to aid connection between _hosts_
   > Network devices can be Router, Switches, Hubs, Bridges etc

4. Network Topology

   Network devices can be arranges in different ways, called _topologies_
   > Topologies can be Point-to-point, Mesh, Star, Ring, Bus etc

   Eg.

   ```mermaid
   flowchart LR
       subgraph T1[Point-to-point]
            direction RL
            Host1 <--> Host2
       end

       subgraph T2[Ring]
           direction LR
           H1 --n/w device--- H2 --n/w device--- H3 --n/w device--- H4 --n/w device--- H1
       end

       subgraph T3[Star]
           direction LR
           H-1[Network Device] --- H-2
           H-1 --- H-3
           H-1 --- H-4
           H-5 --- H-1
           H-6 --- H-1
           H-7 --- H-1
       end
   ```

5. OSI model

   - Network Architechture is a _layered architechture_. OSI model is a _reference model_ that specifies communication __protocols__ and __funtionality__ of each layer
   - Protocols are set of rules that _define how two hosts communicate_ with each other
   > Each OSI layer has different functions and protocols defined like Ethernet ll for Data-Link Layer, IP v4/v6 at Network Layer, TCP at Transport Layer, HTTP at Application Layer

    ```mermaid
    ---
    title: Open System Interconnection(OSI) model
    ---
    flowchart TD
        subgraph S1[Software-Layers]
            L1[1. Application Layer]-->L2[2. Presentation Layer]-->L3[3. Session Layer]
        end
        L3 --TX--> L4[4. Transport Layer] --TX---> L5
        subgraph S2[Hardware Layers]
            L5[5. Network Layer] --> L6[6. Data Link Layer] --> L7[7. Physical Layer]
        end
        L5 --RX--> L4 --RX--> L3
    ```

    > __Unique Indentifiers__ are assigned to each _host_ in the network for identification purpose
    1. Hostname is unique device name for each _host_\
       Type in `hostname` in the terminal to find out yours

    2. IP address
       To identify devices in a network, each device is assigned 32-bit IPv4 address. An IPv6 address length is 128-bits\
       Type `ifconfig` in the terminal for Linux devices and `ipconfig` for Windows devices to find your IP\
       Also called as _logical address_

    3. MAC address
       Unique 48-bit MAC address is assigned to __NIC__ at manufacturing time\
       Also called _physical address_\
       Enter `ipconfig/all` in windows to find MAC address

    4. Port
       _Port_ are like logical channels through which _data is sent/received_ to/from an __application running on _host_ device__\
       If _multiple applications_ are running on a host, each can be _identified by the port number on which they run_\
       Port number is 16-bit integer. All available ports(0-65535) are grouped as-
       | Port Types  | Range         |
       | :----:      | :----:        |
       | Well-known  | 0 - 1023      |
       | Registered  | 1024 - 49151  |
       | Ephemeral   | 49152 - 65535 |

        To list out all in use ports, in windows type in `netstat -a`

    5. Socket
       Combination of IP address and Port number called socket

## Also checkout

- DNS Server

  Domain Name System Server _translates or resolves_ __URLs(domain name)__ to __IP addresses__
  > This way, we don't need to remember IP addresses by refering to hosts by their _URL_\
  Use `nslookup` in terminal to find out IP of any domain\
  Or just enter URL in browser, it will resolve to IP

- ARP

  Address Resolution Protocol _resolves_ __IP address__ to corresponding __MAC Address__\
  Used by Data Link Layer to identify MAC address of receiver's host
  > ~~RARP~~: Reverse Address Resolution Protocol used to resolve __MAC address to IP address__, but it has become obsolete since __DHCP__ is used
