Power over Ethernet (PoE) allows network cables to carry electrical power, eliminating the need for separate power supplies for devices connected to a network. This is particularly useful for devices like IP cameras, VoIP phones, wireless access points, and single-board computers like the Raspberry Pi.

### PoE with Raspberry Pi 5

1. **PoE HAT**    
The Raspberry Pi Foundation has released PoE HATs (Hardware Attached on Top) for their previous models, such as the Raspberry Pi 3B+ and Raspberry Pi 4. For the Raspberry Pi 5, a new PoE HAT will be designed to fit the updated form factor and power requirements. This HAT connects to the GPIO pins and the Ethernet port to draw power directly from the Ethernet cable.

2. **Power Requirements**   
The Raspberry Pi 5 requires a more robust power supply compared to its predecessors, especially if it’s used with peripherals and high-power accessories. The PoE HAT for Raspberry Pi 5 will ensure that the device receives adequate power through the Ethernet connection.

3. **Installation**   
To use PoE with the Raspberry Pi 5, you’ll need:     
    
    - A PoE HAT compatible with the Raspberry Pi 5.
    - An Ethernet cable connected to a PoE-enabled switch or injector.
    - The Raspberry Pi 5 itself.

4. **Advantages**:
    
    - **Simplified Cabling**: By using PoE, you reduce the number of cables needed, simplifying installation and reducing clutter.
    - **Placement Flexibility**: PoE enables placing the Raspberry Pi 5 in locations without easy access to power outlets.
    - **Centralized Power Management**: With PoE, you can manage the power supply for multiple devices from a central location.

5. **Compatibility**:
    
    - **Power Budget**: Ensure that your PoE switch or injector can provide sufficient power to all connected devices, including the Raspberry Pi 5.
    - **Network Infrastructure**: Your network infrastructure should support PoE, typically adhering to IEEE 802.3af (PoE) or IEEE 802.3at (PoE+).


### Waveshare PoE HAT (F)

We have tested Waveshare PoE HAT (F) with Raspbery Pi 5.   
Link: [https://www.waveshare.com/poe-hat-f.htm](https://www.waveshare.com/poe-hat-f.htm)

#### Connection Diagram
Connect the PoE_HAT(F) to the Raspberry Pi 5 as shown below:
![Waveshare PoE HAT (F)](../img/PoE_HAT_(F)_RPI.jpg)

#### Parameters
 - PoE input voltage: 37V-57V DC input
 - PoE - GPIO header: 5V 4.5A (MAX)
 - PoE - 2P header: 12V 2A (MAX)
 - Network standard: Support IEEE 802.3af/at PoE
 - Dimensions: 56.5 × 70.0mm

#### HAT Instalation
Install the heatsink as shown below:
![Waveshare PoE HAT (F)](../img/PoE_HAT_(F)_RPI2.jpg)

