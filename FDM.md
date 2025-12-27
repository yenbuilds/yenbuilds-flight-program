## FDM (Flight Data Monitoring) Format

### What is FDM?

**FDM = Flight Data Monitoring** (also called Flight Data Recorder format)

Not a single format, but a category of standardized data formats used in commercial aviation to record flight parameters from aircraft systems.

### Common FDM Formats

**1. ARINC 717 (successor to ARINC 573)**
- Industry standard for flight data recording (per FAA AC 20-141B)
- Binary format using 12-bit word structure (not compressed, but uses efficient bit packing and time-division multiplexing)
- Records 88+ parameters per FAA/ICAO requirements; modern FDM programs often record 100+
- Sample rates vary significantly by parameter type:
  - High-frequency (control surfaces, accelerations): 8–32 Hz
  - Medium-frequency (attitude, airspeed): 1–4 Hz
  - Low-frequency (selected altitude, gear position): 0.5 Hz down to 1/64 Hz
- Used by actual Flight Data Recorders (black boxes)
- *Sources: FAA AC 20-141B, ICAO Annex 6 Table A8-1, ARINC 717 specification*

**2. IRIG 106 Chapter 10**
- Military/test flight standard developed by Range Commanders Council (RCC)
- More flexible, platform/hardware/media-independent design
- Supports multiple data types: PCM, MIL-STD-1553, ARINC 429, video (H.264, MPEG), Ethernet, CAN bus, etc.
- Used on B-1, B-52, F-15, F-16, F-35, Apache helicopters, and NATO flight test programs
- *Sources: IRIG 106 Chapter 10 specification, NASA Agardograph*

**3. CSV/Parquet Derivatives**
- Many airlines convert ARINC 717 to CSV or Parquet for analysis
- Easier to work with, less standardized
- What you'd likely target for your platform

### Key Parameters in FDM Data

A typical FDM dataset includes (per ICAO Annex 6 Table A8-1 and 14 CFR 135.152):

- **Position**: Lat, Long, Altitude (pressure & GPS)
- **Attitude**: Pitch, Roll, Heading
- **Speed**: IAS, TAS, GS, Vertical Speed
- **Control surfaces**: Aileron, Elevator, Rudder positions
- **Engine**: N1, N2, EGT, Fuel Flow
- **Systems**: Flap position, gear position, autopilot modes
- **Environment**: OAT, TAT, Wind
