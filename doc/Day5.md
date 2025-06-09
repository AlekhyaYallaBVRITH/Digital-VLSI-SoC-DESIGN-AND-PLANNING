Final Steps Overview:
The following key steps are performed as part of the final stages of the RTL2GDS flow: 3 steps are done here: 
1. Power Routing:
Normally, Power Delivery Network (PDN) creation is done during the floorplan stage. However, in the OpenLane flow, power routing is done at this stage. This is where power grid and supply connections to cells are established to ensure that each component gets proper power distribution throughout the chip.
Proper power routing is crucial for the chip's operation, as insufficient power delivery or poor routing can cause reliability issues and timing failures due to voltage drops.
2. Signal Routing with TritonRoute:
Signal routing refers to the interconnection of the cells (gates, flip-flops, etc.) with the metal layers that carry the signal between them. In this stage, TritonRoute is used for physical routing of signal connections.
This step ensures that all the signal paths are properly connected, avoiding congestion or routing violations, which could affect chip performance.
3. RC Extraction:
RC Extraction involves extracting the resistance (R) and capacitance (C) values of the interconnects (wires and vias) in the layout. This information is essential for post-layout timing analysis as these parasitic values impact the signal propagation speed, timing, and overall performance of the chip.
4. Post-Route Timing Analysis with OpenSTA:
OpenSTA (Static Timing Analysis) is then used to perform post-route timing analysis. This step analyzes the timing of the design after the physical routing has been completed. It checks whether the design meets the required timing constraints, such as setup and hold times for flip-flops, and if the signal transitions occur within the allowed timing windows.
The post-route timing analysis takes into account the RC delays from the extracted interconnects, which might not have been present in pre-route timing analysis. Any violations discovered at this stage will be fixed by adjusting the design or routing to ensure that all timing requirements are met.
