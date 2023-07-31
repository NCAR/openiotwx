# Assembling the Main Unit

**Components:**

1. **Spherical Housing:**
     - Contains the microcontroller and primary wiring center.

|wiring | Side | Front |
| ---- | ---- | ---- |
| ![I2C wiring](.././build_img/I2C_wiring.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![I2C side](.././build_img/I2C_side.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![I2C front](.././build_img/I2C_front.jpg){: style="display: block; margin: 0 auto; width: 250px;"} |

2. **Radiation Shield:**
     - Contains the atmospheric sensor (BME680).

| Parts | Complete |
| ------ | ------ |
| ![radiation parts](.././build_img/radiation_parts.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![radiation built](.././build_img/radiation_built.jpg){: style="display: block; margin: 0 auto; width: 250px;"} |

3. **UV Tube and UV Cap:**
     - Contains the LTR390.
     - Is a non-threaded 1in housing such that it can sit separate (in a T) from the orb, so UV isn't
   obstructed.

| Parts | Process | Complete |
| ------ | ------ | ------ |
| ![uv parts](.././build_img/uv_parts.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![uv process](.././build_img/uv_process.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![uv complete](.././build_img/uv_complete.jpg){: style="display: block; margin: 0 auto; width: 250px;"} |

5. **AQ (Air Quality) :**
     - Contains the PMSA003I.
     - Made of three component, a base (sensor is placed there), a vented lid fastened to the base,
   and an impermeable cap (for sensor protection)

| Parts | Process | Complete |
| ------ | ------ | ------ |
| ![aq parts](.././build_img/aq_parts.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![aq process](.././build_img/aq_process.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![aq built](.././build_img/aq_built.jpg){: style="display: block; margin: 0 auto; width: 250px;"} |

6. **Hydreon RG15 Rain Sensor:**
     - Separate it from its base by removing the four Phillips head screws.
     - Connect it to the microcontroller using GPIO to Grove wire-set with the following connections:
       - Red: 5V
       - Black: Ground
       - Yellow: Input
       - White: Output
      - Attach the threaded, printed, base that you printed.

| Parts | Deconstructed | Wiring | Complete |
| ------ | ------ | ------ | ------ |
| ![rg parts](.././build_img/rg_parts.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![rg deconstructed](.././build_img/rg_deconstructed.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![rg_wiring](.././build_img/rg_wiring.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![rg complete](.././build_img/rg_built.jpg){: style="display: block; margin: 0 auto; width: 250px;"} |

7. **Qwiic Connection:**
     - The RG15 monopolizes the Grove port, and the type of connection that port uses.
     - To integrate Qwiic, attach a GPIO to qwiic jumper on ground, 5v, pin 21, and pin 25 of the microcontroller.
     - Connect a four-way qwiic splitter to this qwiic setup.


8. **Other Sensors:**
     - Qwiic compatible, I2C, sensors can be daisy-chained or connected to another splitter if needed.

**Assembly:**

1. Wire up the entire system and connect it to a power source and wireless signal.

2. Run diagnostics through CHORDS to ensure data is being received by clients.

3. Place each sensor in its respective housing and reattach all components.

4. Mount the sensor station at a height of 1.5-2 meters off the ground, in a representative area compared to the surrounding environment, and isolated from buildings for accurate measurements more suitable in use for climate models.

### Charging Assembly

| Parts | Complete |
| ------ | ------ |
| ![power parts](.././build_img/charging_process.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![power built](.././build_img/charging.jpg){: style="display: block; margin: 0 auto; width: 250px;"}|

### Rain Gauge and Air Quality Integration

| Part 1 | Part 2 | Complete |
| ------ | ------ | ------ |
| ![part 1](.././build_img/rg_aq_process_0.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![part 2](.././build_img/rg_aq_process_1.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![complete](.././build_img/rg_aq_complete.jpg){: style="display: block; margin: 0 auto; width: 250px;"} |

### Integrating RG15 and AQ with Base

| Process | Complete | 
| ------ | ------ |
| ![process](.././build_img/orb_rg_aq_process.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![complete](.././build_img/orb_rg_aq.jpg){: style="display: block; margin: 0 auto; width: 250px;"} |

### Station Assembly

| Without PVC | Without Power | Full Station |
| ------ | ------ | ------ |
| ![No PVC](.././build_img/station_no_pvc.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![No Power](.././build_img/station_no_power.jpg){: style="display: block; margin: 0 auto; width: 250px;"} | ![Full](.././build_img/full_station.jpg){: style="display: block; margin: 0 auto; width: 250px;"} |

