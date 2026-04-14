# Vespa-Velutina-Tracking-Drone
Project for building a drone for tracking purpose

Drone-Assisted RF
Triangulation for Vespa Velutina Control


1. Executive Summary

The project is a sophisticated technological response to the invasive threat
posed by the Vespa Velutina (Asian Yellow-Legged Hornet). By combining aerial robotics,
Software Defined Radio (SDR), and real-time data analysis, this system enables the rapid
localization of hornet nests. The core innovation lies in the use of a drone-mounted directional
antenna system to triangulate signals from micro-transmitters, significantly reducing the search
time compared to traditional ground-based methods.


2. Problem Statement

The Vespa Velutina is a major predator of honeybees, causing ecological and economic
damage across Europe. Locating their nests is the primary challenge for containment, as they
are often hidden in high canopies or dense vegetation. Conventional tracking involves visual
follows or ground-level radio tracking, both of which are hindered by terrain obstacles and the
limited line-of-sight (LOS) available at ground level.


3. System Architecture

The project is divided into two synergistic units connected via high-bandwidth data links.

3.1 The Aerial Unit (The Drone)
The drone acts as an elevated sensing platform, overcoming terrain-induced signal attenuation.
● RF Frontend: A 4-element Yagi-Uda antenna, specifically tuned to the 148 MHz VHF
frequency. This antenna provides high directivity and gain, essential for picking up the
weak pulses of micro-transmitters.
● SDR Receiver: An RTL-SDR dongle captures the raw radio frequency signals.
● Onboard Processing (SBC): A Single Board Computer (e.g., Raspberry Pi or similar)
interfaces with the SDR. It handles the initial data stream and bundles it with telemetry
metadata.
● Sensor Fusion: An integrated GPS module and a high-precision magnetometer provide
the drone’s exact coordinates and the antenna's heading (azimuth). This data is critical for
accurate vector mapping.
● Communication Link: * LTE Module: Used in urban or covered areas for internet-based
data streaming.
○ Wi-Fi Bridge (Point-to-Point): A high-power wireless link for remote, mountainous, The ground station is the central hub for data visualization and decision-making.
● Hardware: A ruggedized laptop or portable workstation.
● Software Stack: SDR analysis tools such as SDR# (SDRSharp) or SDR++. These tools
allow the operator to visualize the signal’s "waterfall" and accurately measure the
Signal-to-Noise Ratio (SNR) and Peak Strength.
● Mapping Interface: A GIS (Geographic Information System) application where radio
bearings are plotted as vectors over topographic maps.


4. Operational Methodology

4.1 Tagging and Deployment
A hornet is captured and equipped with a miniature VHF transmitter (weighing approx. 0.15g).
Once released, the hornet returns to its nest. The drone is then deployed to an altitude of 50 to
200 meters, establishing a clear Line-of-Sight to the surrounding landscape.

4.2 Signal Acquisition and Direction Finding
1. Scanning: The drone performs a controlled rotation or follows a grid pattern to scan for
pulses at 148 MHz.
2. Peak Detection: When the operator identifies the signal, the drone is oriented to find the
"Maximum Signal Strength" (the main lobe of the Yagi antenna).
3. Vector Logging: At the point of maximum strength, a line is drawn on the map starting
from the drone’s current GPS coordinates along the axis provided by the magnetometer.

4.3 Triangulation and Surgical Localization
A single bearing only provides a direction, not a distance. To solve this:
● The drone moves to a second, distant GPS location (creating a baseline).
● A second measurement is taken, creating an intersecting line.
● The "Area of Interest" (AoI): The intersection point of these multiple vectors identifies
the nest's location.
● Refinement: Successive measurements from 3 or 4 points further narrow the AoI to a few
square meters, allowing ground teams to locate the nest "surgically" with handheld
equipment.


5. Adaptability to Diverse Environments

A key strength of this project is its resilience to environment-specific challenges:
● Urban Contexts: High-density LTE networks allow for low-latency streaming and easy
integration with digital city maps.
● Wilderness/Forestry: In deep forests where signals are reflected by trees (multipath
interference), the drone’s altitude allows it to receive the signal "from above," minimizing
ground-level interference. The dedicated Wi-Fi bridge ensures the operator remains
connected even miles away from the nearest cell tower.


6. Technical Specifications Summary

Component Specification
Operational Frequency 148 MHz (VHF)
Antenna Type 4-Element Yagi-Uda
Flight Altitude 50m - 200m AGL
Data Transmission LTE / 5.8GHz Wi-Fi Bridge
SDR Platform RTL-SDR (R820T2)
Localization Method Multi-point RF Triangulation


7. Conclusion

The project represents a paradigm shift in invasive species management. By
elevating the receiver, we solve the most significant limitation of radio tracking: the "blindness"
caused by terrain. This system provides a scalable, efficient, and highly accurate solution for
protecting local apiculture and restoring ecological balance.