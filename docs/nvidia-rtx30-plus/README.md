# NVIDIA RTX 30 and newer reference

Snapshot: 2026-11-15. [UTF-8 CSV](REFERENCE-GPUS.csv) contains 27 desktop and 18 laptop model/variant groups. This is reference research for VRAM GPU Desk 1.19, not a hardware validation report.

Published wattages are not software control limits. Desktop specifications describe NVIDIA reference/Founders Edition designs; manufacturer boards may differ. RTX 4060 Ti 160/165 W represents reference variants, not an adjustable interval. Laptop values describe subsystem power ranges; OEM firmware and Dynamic Boost can change actual available limits. Empty laptop temperature cells mean the cited comparison does not provide them. Product maximum temperature is not an operating target. Regional D variants, workstation products and every OEM/memory refresh are not exhaustively covered. GeForce RTX 30-series naming must not be confused with workstation RTX 3000 Ada.

The RTX 3060 Ti row uses the NVIDIA reference specification of 200 W. It does not generalize that figure to GDDR6X or OEM/board-partner variants; their actual firmware and NVML bounds must be queried independently.

## Runtime policy

Read each physical GPU's actual power bounds, current and default limit. Preserve the starting limit and avoid raising it when control starts. Discover supported clock arguments before enabling clock control; a maximum-only query cannot provide a minimum. Use independently supported power-only control when locked clocks are unavailable. Discover fan bounds and fan count independently. Manual fan operation needs continuous thermal supervision and default-policy restoration. Unsupported laptop EC fans and passive cards must remain unavailable.

Legacy absolute thermal thresholds, modern signed T.Limit offsets and the user target have different meanings. Unknown data must remain unknown rather than becoming a fabricated hardware limit. Probe both cards independently: never copy another GPU's bounds or fan indexes. Successful telemetry does not establish write support. Exclusive ownership against another privileged controller cannot be guaranteed.

These are engineering recommendations derived from the APIs, not a claim that every listed product supports every NVML command. Real model/driver testing remains necessary.

## Official sources

- [Desktop comparison](https://www.nvidia.com/en-us/geforce/graphics-cards/compare/): RTX 40/50 references and manufacturer variation.
- [RTX 30 desktop](https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/).
- [RTX 40/50 laptops](https://www.nvidia.com/en-us/geforce/laptops/compare/).
- [RTX 30 laptops](https://www.nvidia.com/en-gb/geforce/laptops/compare/30-series/).
- [NVML queries](https://docs.nvidia.com/deploy/nvml-api/latest/api/group__nvmlDeviceQueries.html), [commands](https://docs.nvidia.com/deploy/nvml-api/latest/api/group__nvmlDeviceCommands.html), [enums](https://docs.nvidia.com/deploy/nvml-api/latest/api/group__nvmlDeviceEnums.html), [fields](https://docs.nvidia.com/deploy/nvml-api/latest/api/group__nvmlFieldValueEnums.html).
- [NVIDIA signed T.Limit hardware-capture schema](https://github.com/NVIDIA/k8s-test-infra/blob/main/docs/configuration.md).
