

# Hardware Manual

- Hardware Architectural Specification (v1/hwarch.html) – a design-level view of the NVDLA hardware architecture, including detail on each sub-component, and register-level documentation.

## NVDLA v1

This is the non-configurable “full-precision” version of NVDLA. The design code is in nvdla v1 branch.

- In-memory data formats (format.html) – description of the in-memory format for weight and activation data.
- Integrator’s Manual (v1/integration\_guide.html) – a guide for SoC integrators, including a walk-through of the NVDLA build infrastructure, NVDLA’s testbenches, and synthesis scripts.
- Precision Preservation (v1/ias/precision.html) – the technologies used to keep the precision when formats INT8/INT16/FP16 are used.
- LUT programming (v1/ias/lut-programming.html) – the guide to programming lut tables
- Unit Description (v1/ias/unit\_description.html) – description of internal architecture of sub-units
- Programming Guide (v1/ias/programming\_guide.html) – programming guide of sub-units

## NVDLA v2

This version is scalable design of NVDLA. Currently, the config nv\_small is verified. The architecture of sub-units is same as NVDLA v1.

- NVDLA Environment Setup Guide (v2/environment\_setup\_guide.html) – Please follow this document to setup tools and dependency libraries
- Scalability parameters and ConfigROM (v2/scalability.html) – Scalability parameters and ConfigROM contents in nv\_large and nv\_small configurations
- Integrator’s Manual (v2/integration\_guide.html) – a guide for SoC integrators, including NVDLA system inference introduction, synthesis scripts.
- NVDLA Verification Suite User Guide (v2/verif\_guide.html) – NVDLA Verification Suite User Guide