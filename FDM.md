## FDM (Flight Data Monitoring) Format

### What is FDM?

**FDM = Flight Data Monitoring** (also called Flight Data Recorder format)

Not a single format, but a category of standardized data formats used in commercial aviation to record flight parameters from aircraft systems.

### Common FDM Formats

**1. ARINC 573/717**
- Industry standard for flight data recording
- Binary format, highly compressed
- Records 100+ parameters: altitude, airspeed, engine data, control inputs, etc.
- Sample rates vary by parameter (1-8 samples/second typically)
- Used by actual Flight Data Recorders (black boxes)

**2. IRIG 106 Chapter 10**
- Military/test flight standard
- More flexible, supports multiple data types
- Used in flight test programs

**3. CSV/Parquet Derivatives**
- Many airlines convert ARINC to CSV or Parquet for analysis
- Easier to work with, less standardized
- What you'd likely target for your platform

### Key Parameters in FDM Data

A typical FDM dataset includes:
- **Position**: Lat, Long, Altitude (pressure & GPS)
- **Attitude**: Pitch, Roll, Heading
- **Speed**: IAS, TAS, GS, Vertical Speed
- **Control surfaces**: Aileron, Elevator, Rudder positions
- **Engine**: N1, N2, EGT, Fuel Flow
- **Systems**: Flap position, gear position, autopilot modes
- **Environment**: OAT, TAT, Wind
