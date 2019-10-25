# Altek-AIBox
The Qualcomm® QCS603-based AIBOX reference design by Altek, a leading ODM for IP cameras, is available now.
AIBOX4-W&E by the Qualcomm® QCS603 SoC (System on Chip) also known as the Qualcomm® Vision Intelligence Platform, the QCS603 AIBOX produced by Altek Corporation is the perfect reference design for the IoT camera.
Coupling Qualcomm® Artificial Intelligence Engine with Altek Corporation’s industry expertise in camera and imaging, you are guaranteed to have the best in class visual quality for your product. This design will ensure that your product will be both competitive, and compelling for all your edge computing needs.
With Linux running natively and industry design best practices already applied, you will be able to create your own cost effective product while securing your time to market needs.

## Hardware Specification
### CPU/OS
- SOC : Qualcomm® QCS603/PME605/PM8005 
- OS: Yocto Linux

### Camera
- No Camera

### Memory (discrete)
- LPDDR4 2GB(Micron), if supported by SW
- eMMC 8GB

### Sensors
- No Sensors

### Connective
- Wi-Fi WCN3980 – 802.11 n/ac, 1x1
- Bluetooth 5.0
- Ethernet: Integrated IEEE 802.3 POE/RJ45 1000M 

### Interface
- HDMI: 1 x HDMI 1.4 Type-A
- Power Button: Power on/off
- Display mode switch: single press to switch camera displaying 
- Antenna : Wi-Fi/BT

### Power
- DC-Jack, DC-in 5V, 3A 

### Display
- HDMI Type-A output(1080p) 

### Audio
- N/A

### LED Indicators
- Power LED for PWR on/off 
- LAN (Link/Act): 1 x with a RG 2 color LED Link IPC (Orange for no IPC connected, Green 1Hz for connect to IPCS, Green for connect to IPC(s) & internet
- Status LED: 1 x with a RG 2 color LED (Red for FW update, Green for normal, Orange for configure network)

## Software Document
- [Quick Start Guiding for AIBox By Azure](./aibox-linux-for-edge.md)
- [How to have AI model running at AIBox](./AI_Model_to_AIBox.md)
- [Deploy AI by Azure](./Deploy_AI_By_Azure.md)