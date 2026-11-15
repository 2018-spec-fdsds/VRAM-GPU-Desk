# PSU telemetry capability matrix

Research snapshot: 2026-11-15. English is the primary language of this document.

Compatibility is qualified by model, USB identity and protocol, not by a vendor logo or an "AI", "digital" or "smart" product name. A rail measures an electrical supply group; it does not necessarily measure one physical GPU connector. GPU board power reported by NVIDIA is also different from total PSU power.

## NZXT E-series: additional partial reader

NZXT E500, E650 and E850 have an implemented rail-sensor reader with synthetic protocol checks only. Their protocol does not provide direct measured total output watts or individual physical GPU-port currents to this release’s PSU card. This is partial reader coverage, not full PSU-card support; missing totals are not fabricated.

## Six priority brands

| Priority | Brand and qualified scope | Available or documented telemetry | GPU socket / pin telemetry | Implementation and validation status |
| --- | --- | --- | --- | --- |
| 1 | MSI MPG Ai1300TS PCIE5 and MPG Ai1600TS PCIE5 | Direct output watts, optional efficiency/temperature/fan, rail data in the qualified SDK layout | Two 12V-2x6 groups, six current measurements per group; group current is their sum | Read-only sensor queries verified on MPG Ai1300TS; Ai1600TS remains protocol-qualified. |
| 2 | Corsair HXi/RMi models in the USB table below | Direct measured output watts, temperature, fan RPM and three rail groups | No individual GPU socket/pin data in this protocol | Original C# 5 reader implemented; synthetic checks passed; physical model validation pending. |
| 3 | Seasonic OptiGuard / OptiGuard 2.0 products, when explicitly fitted | Official sources describe connector current/temperature protection; OptiGuard 2.0 also describes voltage and power monitoring | Connector contact monitoring exists in the protection technology; a Windows-readable interface has not been qualified | Research entry only. No generic Seasonic reader or guessed USB identifiers. Hardware sensing does not establish a public software API. |
| 4 | be quiet! Dark Power Pro 14 IO 1300W / 1600W | Official IO Center monitoring; public WebHID code identifies input power, fan, temperature and rail voltage/current sensors | The inspected PSU sensor table has six 12V rail groups, not individual GPU socket/pin sensors | Model IDs and public QLink protocol identified. Adapter not implemented; session, CRC and framing validation remain necessary. Plain Dark Power 14 is a different scope. |
| 5 | ASUS ROG Thor III / related GPU-First IVS products | Product-local power display and hardware voltage sensing are documented | GPU-First IVS is voltage stabilization; it does not establish readable per-connector current telemetry | Research entry only. No Windows PSU data interface or protocol qualified for this release. This is not a statement that all present/future ASUS models lack telemetry. |
| 6 | Thermaltake DPS G / iRGB PLUS USB family 264A:2329 only | Temperature, fan RPM, rail voltages/currents; total output can be calculated from rail V × A | No individual GPU socket/pin data in the qualified protocol | Original C# 5 reader implemented; synthetic checks passed; physical model validation pending. New or other Thermaltake USB protocols are not implicitly covered. |

MSI documents dual-connector current monitoring and PSU output reporting on the official [Ai1300TS](https://www.msi.com/Power-Supply/MPG-Ai1300TS-PCIE5) and [Ai1600TS](https://www.msi.com/Power-Supply/MPG-Ai1600TS-PCIE5) pages. The implementation's word layout and device identities come from the separately inspected MSI Afterburner SDK `MSIPSU.h` and the reviewed reader; product marketing alone is not a binary protocol specification.

Seasonic describes contact current and temperature protection in its [OptiGuard explanation](https://seasonic.com/insights/seasonic-optiguard-technology/) and the wider monitoring scope of [OptiGuard 2.0 at Computex 2026](https://seasonic.com/insights/seasonic-updates-at-computex-2026/). These pages do not establish a qualified Windows read protocol or USB ID for this integration.

be quiet! confirms IO Center support on [Dark Power Pro 14 IO](https://www.bequiet.com/en/powersupply/7319) and its [launch announcement](https://www.bequiet.com/en/press/34164). Its own [review summary](https://www.bequiet.com/en/press/34207) notes the absence of dedicated connector-specific 12V-2x6 safety sensors. Public software evidence is described below.

ASUS describes automatic hardware operation of GPU-First IVS, without software configuration, in the [Thor III Titanium EVO FAQ](https://rog.asus.com/us/power-supply-units/rog-thor/rog-thor-1600t3-gaming-evo/). This is not evidence of a host-readable PSU sensor API. Aura lighting connectivity must not be treated as PSU telemetry.

Thermaltake confirms PC monitoring for its digital PSU families in the [DPS G announcement](https://latam.thermaltake.com/news/view/index?id=162) and [iRGB PLUS 1250W/1650W manual](https://file.thermaltake.com/file/qig/TOUGHPOWER_iRGB_PLUS_1250_1650W_Manual.pdf). Actual adapter scope is the specific USB protocol below.

## Qualified USB identity registry

### MSI

| VID:PID | Model | Rated output |
| --- | --- | --- |
| 0DB0:AA6F | MPG Ai1300TS PCIE5 | 1300 W |
| 0DB0:808C | MPG Ai1600TS PCIE5 | 1600 W |

The reader recognizes only these IDs and the qualified MSI layout. Other MSI families require separate qualification.

### Corsair HXi/RMi

| VID:PID | Model | Rated output |
| --- | --- | --- |
| 1B1C:1C05 | HX750i | 750 W |
| 1B1C:1C06 | HX850i | 850 W |
| 1B1C:1C07 | HX1000i | 1000 W |
| 1B1C:1C08 | HX1200i | 1200 W |
| 1B1C:1C0A | RM650i | 650 W |
| 1B1C:1C0B | RM750i | 750 W |
| 1B1C:1C0C | RM850i | 850 W |
| 1B1C:1C0D | RM1000i | 1000 W |
| 1B1C:1C1E | HX1000i (2022, CP-9020214) | 1000 W |
| 1B1C:1C1F | HX1500i (CP-9020215) | 1500 W |
| 1B1C:1C23 | HX1200i ATX 3.1 (CP-9020281) | 1200 W |
| 1B1C:1C27 | HX1200i ATX 3.1 (CP-9020307) | 1200 W |

Identity and protocol references: [liquidctl Corsair driver](https://github.com/liquidctl/liquidctl/blob/main/liquidctl/driver/corsair_hid_psu.py), [HXi/RMi guide](https://github.com/liquidctl/liquidctl/blob/main/docs/corsair-hxi-rmi-psu-guide.md), and [LibreHardwareMonitor sensor protocol](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor/blob/master/LibreHardwareMonitorLib/Hardware/Psu/Corsair/UsbApi.cs). The implementation is original; these are protocol references, not copied implementation code.

AX1600i, AX1600i SHIFT and HX1000i SHIFT CRYSTAL are excluded from this legacy reader. In particular, [Corsair's CRYSTAL announcement](https://corsair-newsroom.prgloo.com/news/corsair-launches-the-hx1000i-shift-crystal-power-supply-with-transparent-panels-and-pinprotect-gpu-protection) describes new per-pin monitoring, which must not be attributed to the older HXi protocol. Additional identities and framing need independent qualification.

### Thermaltake

| VID:PID | Qualified family | Rated output |
| --- | --- | --- |
| 264A:2329 | DPS G / iRGB PLUS controller protocol | Unknown until independently established for the physical model |

The [protocol author's DPS G command reference](https://moshimoshi0.github.io/ttrgbplusapi/controllers/dpsg.html) documents sensor queries under command 0x31. The reader uses registers 0x33–0x3B and model read 0x3D only. It does not send initialization 0xFE, control 0x30, reset, RGB or fan-setting requests. The model is read from the device; rated wattage is not guessed from arbitrary digits in that model string.

### be quiet! protocol research, no adapter

| VID:PID | Model | Status |
| --- | --- | --- |
| 373F:0023 | Dark Power Pro 14 IO 1300W | Identity found in official public WebHID software; not implemented |
| 373F:0024 | Dark Power Pro 14 IO 1600W | Identity found in official public WebHID software; not implemented |

The official [IO Center Web](https://iocenter.bequiet.com/) [public application bundle inspected on this date](https://iocenter.bequiet.com/assets/index-Zx3Q0vHz.js) maps these IDs to its PSU class. Its sensor feature is 0x30, with read functions for inventory, metadata, configuration and values. Communication requires QLink session/request identifiers, framing and CRC, not the legacy Corsair protocol. The 23-sensor table contains runtime, fan, temperature, error state, input power/voltage and rail currents/voltages. No direct total DC-output power or per-pin sensor was identified. A future reader must avoid control/configuration writes and must not take over an existing IO Center session by force.

Seasonic and ASUS have no qualified USB identity in this release. Unknown IDs are deliberately left unknown.

## Additional implemented family

NZXT E500 (7793:5911), E650 (7793:5912), and E850 (7793:2500) are an additional family outside the six priority brands. The reader exposes measured rail data, temperature and fan RPM, with no initialization command. The 12V motherboard/PCI-e group is not a physical GPU connector. See the [protocol driver](https://github.com/liquidctl/liquidctl/blob/main/liquidctl/driver/nzxt_epsu.py) and [E-series guide](https://github.com/liquidctl/liquidctl/blob/main/docs/nzxt-e-series-psu-guide.md).
