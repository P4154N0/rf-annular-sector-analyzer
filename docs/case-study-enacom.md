# Technical Report: Diagnosis and Mitigation of Electromagnetic Interference in Critical VHF Links

## I. Technical Situation and Problem Diagnosis
Following several technical field evaluations and a systematic analysis of the radiocommunication system's operability, critical electromagnetic interference anomalies were detected, directly affecting the primary Police Emergency network's operability. 

The reported phenomenon consisted of a total loss of the bidirectional link between the central station and the operative units, both fixed and mobile. This affectation manifested intermittently, sometimes presenting as a high level of broadband noise (elevated noise floor) or, in most cases, through absolute silence, simulating the action of a frequency jammer or high-power harmonic superposition. Initial temporal traces indicated a recurring onset pattern during the night shift, between 21:00 and 22:00 hours.

## II. Geometry and Sectorization of the Interference
Geographically, the affected area did not cover the entire 360-degree radial footprint but was strictly confined to an annular sector (partial circular crown). Final measurements determined the following spatial limits of the interference lobe:

*   **Reference Center (Base Emitter/Receiver):** Lat -37.456802, Lng -61.938778
*   **Inner Radius of Affectation:** 2196 meters
*   **Outer Radius of Affectation:** 13495 meters
*   **Azimuthal Aperture:** Directional wedge spanning between 94.9° and 204.6°

This propagation vector specifically compromised the geographical corridor oriented towards the south and southeast of the central station, covering the jurisdictions of Santa Trinidad, San José, and Santa María.

## III. Hardware Impact and Saturation
A collateral effect of physical saturation and lock-up (*latch-up*) was verified in the central base station units, equipment operating with antennas located between 5 and 40 meters high. Faced with the incidence of this hostile electromagnetic field, these devices suffered a microcontroller lock-up that prevented conventional shutdown via the power button, requiring physical disconnection of the electrical supply, removal of the radiating elements, and a preventive channel change to achieve a reset and operational restoration.

Following an exhaustive technical survey of all proprietary infrastructure (including cables, transmission lines, antennas, and base equipment), it was categorically ruled out that the anomaly was a product of internal failures or physical deficiencies. This technical certainty was based on the fact that, once the interference incidence period ended, the entire coverage circle fully recovered its normal communication without registering mechanical or tuning alterations in the hardware.

## IV. Mitigation Measures and Operative Action Protocol
Faced with the impossibility of guaranteeing continuous coverage on the main frequency under the described conditions, the following contingency protocol was executed to avoid interrupting the essential service:

1. **Directed Monitoring:** Operation on the primary network was maintained as a priority for as long as possible to verify the interference's intrusion patterns and temporal traceability.
2. **Traffic Rerouting Protocol:** In the event of communications collapse or absence of modulation in the delimited sector, an immediate frequency migration (failover) of the affected fixed and mobile units to a backup contingency network was carried out, ensuring dispatch continuity without interruptions.
3. **Logging and Centralization of Events:** It was established that any outage, anomaly, or indication of saturation in the stations would no longer be communicated in isolation; it had to be reported directly and centrally, detailing the exact time, units involved, and the status of the base equipment.