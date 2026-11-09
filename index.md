---
title: Duck Robot | Four-Legged Robotic System
---

# Duck Robot
### Four-Legged Robot with Klann Linkages, Articulated Feet, and Arduino Control

**Engineering design and digital assembly project**  
**Design software:** FreeCAD  
**Control platform:** Arduino Mega (proposed architecture)

---

## Home

### Project information

| Item | Details |
|---|---|
| Project name | Duck Robot |
| Project type | Four-legged robotic platform |
| CAD software | FreeCAD |
| Proposed controller | Arduino Mega |
| Project stage | Digital design, assembly review, and proposed electrical architecture |

*Team members, course, institution, and supervisor have not been specified in the supplied Duck Robot documentation and can be added here.*

## Project overview

The Duck Robot is a four-legged robotic system represented in a FreeCAD assembly. Each of its four legs includes a geared DC motor, a Klann linkage mechanism, a foot sole, two web-style foot flaps, flap hinges, and a foot servo. The proposed control architecture uses an Arduino Mega, four independent DC motor channels, four foot servo signals, an ultrasonic sensor, and a water sensor.

The current documentation covers CAD-derived component dimensions, a digital mechanical assembly process, and a proposed electrical connection schedule. A four-leg visual movement preview was reported to run without warnings. This does **not** by itself demonstrate fully validated linkage kinematics, collision-free operation, or physical robot performance.

**Project stage:** Digital engineering design and review.  
**Physical prototype status:** Not built or tested within the documented scope.  
**Electrical status:** Proposed wiring architecture; hardware specifications and physical verification remain outstanding.

## Engineering objective

**How can a four-legged, Klann-linkage-based robot integrate motor-driven leg mechanisms, articulated foot flaps, and Arduino-based electronics in a mechanically consistent, verifiable design?**

The current engineering work focuses on arranging the complete assembly in CAD, documenting the components and electrical signals, reviewing the movement visualization, and identifying the checks needed before possible fabrication.

## Biomechanics background and initial specifications

### Mechanical principle

Each leg uses a **Klann linkage**, with crank, coupler, rocker, lower link, and foot carrier components. The geared motor provides the crank input. The foot assembly includes a sole and two hinged flaps; the exact servo-to-flap mechanical coupling must still be confirmed in the native CAD model.

### CAD-derived reference dimensions

The measurements below are **bounding-box extents**, not necessarily manufacturing length/width/thickness dimensions or fully specified part drawings. All values are in millimeters (mm).

| Component | X extent (mm) | Y extent (mm) | Z extent (mm) |
|---|---:|---:|---:|
| Main chassis body | 300.000 | 180.000 | 8.000 |
| Combined robot assembly envelope | 341.363 | 353.971 | 145.000 |
| Underside rail — left | 250.000 | 12.000 | 10.000 |
| Underside rail — right | 250.000 | 12.000 | 10.000 |
| Foot sole (representative) | 75.000 | 48.000 | 6.000 |
| Foot flap A / B (each) | 68.000 | 19.000 | 3.000 |
| Foot servo envelope | 40.000 | 20.000 | 35.000 |
| Gear motor envelope | 52.000 | 34.000 | 34.000 |

### Component inventory

| Component group | Quantity per leg | Robot total |
|---|---:|---:|
| Motor bracket | 1 | 4 |
| Geared motor | 1 | 4 |
| Motor shaft | 1 | 4 |
| Klann crank, coupler, rocker, lower link, foot link | 1 of each | 4 of each |
| Joint pins | 5 | 20 |
| Foot sole | 1 | 4 |
| Foot flaps A and B | 1 of each | 4 of each |
| Flap hinges A and B | 1 of each | 4 of each |
| Foot servo and bracket | 1 of each | 4 of each |
| Arduino Mega, motor-driver deck, battery pack | Shared | 1 set |
| Ultrasonic sensor, water sensor, and brackets | Shared | 1 set |

## System kinematics

The proposed motion path for each leg is:

**Geared motor → Motor shaft → Klann crank → Linkage components → Foot carrier and foot**

The FreeCAD project includes four leg stations: **Front Left, Front Right, Rear Left, and Rear Right**. Each station has its own named motor, linkage, joint pins, and foot components.

For a rotating crank, angular speed is conventionally related to rotational speed by:

\[
\omega = \frac{2\pi N}{60}
\]

where \(N\) is rotational speed in revolutions per minute and \(\omega\) is angular speed in radians per second. This is a general engineering relation, **not** a measured result for this robot.

**Motion-validation limitation:** The project owner reported that the four-leg visual preview macro moved all four legs without warnings. Formal FreeCAD Assembly joint references still require repair or verification; the visual preview does not prove a correctly constrained Klann gait.

## System dynamics

Physical performance values, including robot mass, motor torque, walking speed, load capacity, traction, electrical power draw, and stability, have **not** been established by the supplied project documents.

Before physical development, engineering checks should include motor shaft-to-crank engagement, pivot alignment, clearance throughout the intended movement range, motor stall current, servo load/current, and mounting integrity.

## Design optimization

The current documents identify design-review priorities rather than a tested optimization study or weighted decision matrix:

1. Confirm all intended revolute pivot axes are coaxial.
2. Repair invalid `Reference1` / `Reference2` FreeCAD joint references.
3. Verify motor shaft and crank interfaces using actual geometry.
4. Confirm clearance among moving linkages, the chassis, feet, flaps, and hinges.
5. Check selected motor and servo dimensions against real hardware.
6. Complete the missing manufacturing information, including tolerances, hole positions, fits, materials, and fasteners.

No experimentally supported optimal mechanism or component selection is claimed at this stage.

## Design and manufacturing

The CAD dimension schedule contains component bounding-box extents and selected cylindrical-feature evidence. Representative features include **Ø8 mm** linkage cylindrical faces, **Ø6 mm** joint-pin cylindrical faces, and **Ø4 mm** flap hinge cylindrical features. The motor shaft includes a reported **Ø10 mm** cylindrical feature.

These data do **not** establish all pivot centre-to-centre dimensions, fully dimensioned 2D profiles, hole patterns, mating fits, material grades, general tolerances, or surface finishes. The native FreeCAD model must be used to verify the geometry before fabrication.

### Proposed digital assembly sequence

1. Open the latest native `.FCStd` model; use a copy for edits and establish the chassis datum.
2. Check the two underside rails and the electronics deck against the assembly.
3. Position all four motor brackets, motors, and shafts at their named leg stations.
4. Arrange the crank, coupler, rocker, lower link, foot link, and five joint pins for each leg.
5. Verify that intended revolute joint axes and references are valid.
6. Attach the foot carrier and sole, then position the two flaps, hinges, servo bracket, and servo envelope.
7. Repeat and review each leg station without interchanging station-specific components.
8. Position the Arduino Mega, motor-driver deck, battery, ultrasonic sensor, and water sensor envelopes.
9. Review fixed and moving connections and check for unintended interference.
10. Save a controlled CAD revision, keeping native CAD, exports, and documentation aligned.

## Electronics and control system

The electrical schedule proposes four independent DC motor control channels connected to an Arduino Mega. The motor driver make/model and actual power components have **not** yet been confirmed.

### DC motor pin assignments

| Motor channel | IN1 | IN2 | PWM / enable |
|---|---|---|---|
| Front Left DC motor | D22 | D23 | D5 |
| Front Right DC motor | D24 | D25 | D6 |
| Rear Left DC motor | D26 | D27 | D7 |
| Rear Right DC motor | D28 | D29 | D8 |

### Foot servo and sensor signals

| Component | Arduino signal |
|---|---|
| Front Left foot servo | D9 |
| Front Right foot servo | D10 |
| Rear Left foot servo | D11 |
| Rear Right foot servo | D12 |
| Ultrasonic trigger | D30 |
| Ultrasonic echo | D31 |
| Water sensor analog signal | A0 |

### Proposed power distribution

**Battery → Appropriately rated fuse → Master switch → Motor-driver power input**

The four foot servos require a separately rated supply. Motors and four servos should **not** be powered from the Arduino 5 V pin. The Arduino requires suitable regulated input power, and connected electronics need compatible voltage and logic levels. Ground-reference arrangements depend on the selected driver and isolation design.

The documented starter code commands a common motor speed and individual foot-servo signals. It does **not** implement validated gait phase control.

## Sensors and proposed functions

Two sensors are represented in the CAD inventory and electrical signal schedule:

- **Ultrasonic sensor:** Trigger and echo signals assigned to Arduino pins D30 and D31.
- **Water sensor:** Analog signal assigned to Arduino pin A0.

The documents do not establish tested obstacle detection, automatic avoidance, water-response behavior, or sensor performance. Those functions should not be presented as implemented capabilities until code and testing demonstrate them.

## Power and electrical safety

The proposed electrical architecture requires additional verification before physical wiring:

- Confirm battery chemistry, voltage, capacity, and polarity.
- Select motor drivers supporting four independent DC motor channels.
- Verify motor voltage, stall current, servo model, and servo current requirements.
- Size the fuse, switch, wires, and power distribution appropriately.
- Confirm sensor pinouts, logic-level compatibility, and regulated input voltages.
- Check ground-reference requirements, reverse-polarity protection, waterproofing, connectors, and strain relief.

**Important:** The electrical connections document is a **design-review schedule**, not a physically tested or certified schematic.

## Data collection and experimental validation

### Current verification record

| Test or review | Current record | Interpretation |
|---|---|---|
| Four-leg visual preview | All four legs reportedly moved without warnings | Preview animation ran; constrained gait not proven |
| Formal Assembly joint references | Invalid `Reference1` / `Reference2` warnings recorded | Repair and verify references |
| Full-cycle collision/clearance | Not established | Check in native CAD |
| Physical prototype | Not performed | No physical performance claim |
| Electrical circuit | Not physically tested | Confirm hardware and safety before wiring |

### Future checks

Potential future validation includes a full-cycle CAD movement and collision review, independent joint-constraint verification, dimensional cross-checks, electrical continuity and power checks, and physical testing if a prototype is built.

No fabricated test measurements or performance results are included.

## Project progress

### Documented work

- Created a FreeCAD-based four-leg robot assembly and extracted dimension schedules.
- Identified repeated Klann linkage and foot components across all four legs.
- Prepared a digital assembly process and a proposed Arduino Mega wiring schedule.
- Ran a four-leg visual preview reported as completing without warnings.
- Documented manufacturing, linkage, and electrical checks that remain unresolved.

### Next steps

1. Verify formal FreeCAD Assembly joint references and pivot axes.
2. Check movement and collision clearances through a complete intended cycle.
3. Confirm selected motors, motor drivers, servos, sensors, and battery specifications.
4. Complete manufacturing drawings and fits using the native CAD model.
5. Review electrical protection, power distribution, and waterproofing.
6. Align all `.FCStd`, STEP, STL, drawings, and documentation to a controlled revision.
7. Build and test a physical prototype only after the necessary design and safety checks are completed.

## Presentations

Suggested future presentation structure (not an indication that slides already exist):

- **Presentation 1:** Project overview, mechanical concept, CAD assembly, and initial specifications.
- **Presentation 2:** Linkage mechanism, articulated feet, Arduino pin schedule, and digital verification.
- **Final presentation:** Updated CAD review, validated results if available, limitations, and future work.

Screenshots, motion-preview videos, source code, and CAD exports can be added to this site as they become available.

## Project documentation and resources

The current project summary was prepared from these supplied documents:

1. **Duck Robot Electrical Wiring Schedule** — proposed Arduino pins, power architecture, and verification requirements.
2. **Duck Robot Engineering Drawing** — CAD-derived dimensions and feature register; not a certified manufacturing drawing release.
3. **Duck Robot Mechanical Assembly Instructions** — digital assembly procedure, verification record, and release checklist.

For downloadable files on GitHub, upload these documents to your repository and add links here after their paths are confirmed.

---

*Duck Robot — FreeCAD mechanical design, digital assembly documentation, and proposed Arduino-based control architecture. Current stage: digital design and review.*
