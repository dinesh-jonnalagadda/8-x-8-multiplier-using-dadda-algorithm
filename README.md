🚀 Dadda Algorithm Based 8×8 Multiplier

A high-speed, area-efficient hardware multiplier designed using the Dadda reduction tree, implemented and synthesized in Cadence RTL-to-GDS flow as part of a semi-custom VLSI design project.

       📌 This project implements and analyzes an optimized 8-bit Dadda multiplier with synthesis reports for Area, Timing, and Power.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Key points :

| Feature          | Explanation                                              |
| ---------------- | -------------------------------------------------------- |
| Input size       | 8×8 multiplier                                           |
| Partial products | 64 bits                                                  |
| Technique        | Minimum adders, staged compression                       |
| Adders used      | Full adders & half adders                                |
| Final stage      | CPA for 2-row sum                                        |
| Benefit          | Faster than array multiplier, less hardware than Wallace |





This project implements an efficient 8×8 Dadda multiplier by :

   *   Generating 64 partial products

   *   Reducing matrix height in controlled stages (6 → 4 → 3 → 2)

   *   Using only Full/Half adders for compression

   *   Producing final 16-bit output using structured carry propagation

     

✅ Why Dadda Algorithm ?

   *   Uses fewer adders compared to Wallace multipliers

   *   Maintains high speed with controlled wiring complexity

   *   Ideal for VLSI / ASIC / FPGA implementations

   *   Demonstrates deep structural digital logic handling




✅ Why dadda algorithm multiplier is considered among other multipliers  ?

| Feature          |         Dadda Multiplier                | Wallace Tree                         | Array Multiplier            | Booth Multiplier                            |
| ---------------- | --------------------------------------- | ------------------------------------ | --------------------------- | ------------------------------------------- |
| Key Idea         | Optimized partial-product reduction     | Aggressive partial-product reduction | Direct summation array      | Encoded multiplication to reduce operations |
| Speed            | **Very High**                           | Very High                            | Low                         | Medium-High                                 |
| Hardware Usage   | **Moderate (optimized)**                | High                                 | Low                         | Medium                                      |
| Area Requirement | **Low-Medium**                          | High                                 | **Lowest**                  | Medium                                      |
| Routing & Layout | **Better structured, easier placement** | Complex routing                      | Very regular                | Moderate                                    |
| Best Use Case    | **Speed + Area balance (ASIC/VLSI)**    | Maximum speed priority               | Low-cost, low-power designs | Signed multiplication & DSP                 |




🧠 Dadda Reduction Stages (8×8 Multiplier) 

| Stage           | Operation                       | Goal Height      | What Happens in Code                                            |
| --------------- | ------------------------------- | ---------------- | --------------------------------------------------------------- |
| **Stage-0**     | **Partial Product Generation**  | 8 → input matrix | `pp[i] = A & {8{B[i]}};`                                        |
| **Stage-1**     | First compression               | Reduce to ≤ 6    | First layer of **HA/FA** to shrink tallest columns              |
| **Stage-2**     | Second compression              | Reduce to ≤ 4    | Deeper **FA chain** to bring product matrix height further down |
| **Stage-3**     | Final partial-product reduction | Reduce to ≤ 3    | Remaining **FA/HA** to get only 2 rows                          |
| **Final Stage** | Final addition                  | 2 → 1            | Ripple/CPA add: `assign P = row1 + row2;`                       |




Report Analysis

This section summarizes the synthesis results (Area, Timing, and Power) for the Dadda 8×8 Multiplier synthesized using Cadence Genus.

🔧 Area Summary

| Metric       | Value                |
| ------------ | -------------------- |
| Design       | Dadda 8×8 Multiplier |
| Total Cells  | 120                  |
| Total Area   | **1332.144 μm²**     |
| Library Mode | Timing-Driven        |
| Condition    | Slow Corner          |


⏱️ Timing Summary

| Metric           | Value              |
| ---------------- | ------------------ |
| Timing Mode      | Setup Analysis     |
| Critical Path    | ✅ Meets Constraint |
| Violations       | **None**           |
| Operating Corner | Slow / Worst-Case  |


⚡ Power Summary

| Power Type      | Value                      | Share |
| --------------- | -------------------------- | ----- |
| Leakage Power   | 6.49 × 10⁻⁶ W              | 9.79% |
| Internal Power  | 2.81 × 10⁻⁵ W              | 42.3% |
| Switching Power | 3.17 × 10⁻⁵ W              | 47.9% |
| **Total Power** | **6.63 × 10⁻⁵ W (≈66 µW)** | 100%  |


📊  Overall Design Efficiency

| Metric                  | Value                        | Remarks                    |
| ----------------------- | ---------------------------- | -------------------------- |
| Total Area              | 1332.144 μm²                 | Compact layout             |
| Critical Path Delay     | Within constraint            | Timing closure achieved    |
| Total Power             | 6.63×10⁻⁵ W                  | Very low power             |
| Design Type             | Semi-Custom (Cadence Genus)  | Synthesized successfully   |
