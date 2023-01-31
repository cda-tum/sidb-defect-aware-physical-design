# Atomic Defect-Aware Physical Design of Silicon Dangling Bond Logic on the H-Si(100)-2×1 Surface

This repository provides supplementary data for the paper *Atomic Defect-Aware Physical Design of Silicon Dangling Bond
Logic on the H-Si(100)-2×1 Surface* by M. Walter, J. Croshaw, S. S. H. Ng, K. Walus, R. Wolkow, and R. Wille.

## H-Si(100)-2×1 Surfaces

Of the hydrogen-passivated silicon surfaces used in this evaluation, two were experimentally fabricated in a lab and
measured with an STM, the others were simulated based on experimental findings.

### STM surface scans

<img src="stm_scans/6.26_percent_defective/overlap_stitch.png" alt="Stitched STM surface scan" align="right" height="340"/>

The fabricated H-Si(100)-2×1 surfaces span a total of 830 × 652 and 740 × 1090 hydrogen sites, respectively, of which
8.57% and 6.26% are defective.

The respective STM surface scan files can be found in the `stm_scans` folder. The `.xml` files can be parsed by both
[*SiQAD*](https://github.com/siqad/siqad) and [*fiction*](https://github.com/marcelwa/fiction).

#### Fabrication process

The STM measurements were performed using an *Omicron LT-STM* system operating at 4.5K and ultra-high vacuum (3E−11
Torr). The STM tips were electrochemically etched from tungsten wire and sharpened using a field ion microscope. The
used samples are highly arsenic-doped (≈1.5E19 atoms per cm³). They were prepared in-situ via resistive heating. To this
end, they were first degassed at 600°C overnight followed by multiple flash annealing cycles at 1250°C. Finally, the
samples were hydrogen-terminated at 330°C while exposing their surface to molecular hydrogen (1E6 Torr). The H₂ gas was
converted to atomic hydrogen using a tungsten filament held at 1600°C.

The image acquisition was done using a *Nanonis SPM* controller with respective software. All images were taken in
constant height mode with an imaging bias of 1.3V and a current setpoint of 50pA.

### Simulated surfaces

We generated simulated surfaces of comparable size with variable defect rates of 1%, 0.5%, and 0.1%, including charged
defects; and 5%, 1%, and 0.5%, with only neutral defects.

The surfaces have been randomly generated with
the [`generate_defective_surface.py`](experiments/generate_defective_surface.py) Python script.

The respectively resulting surface files can be found in the `simulated_surfaces` folder. The `.txt` files represent
Python arrays and can be parsed by [*fiction*](https://github.com/marcelwa/fiction).

## Experimental Evaluation: Atomic Defect-Aware Physical Design

The `experiments` folder contains all data obtained by the physical design process laid out in the paper as well as a
C++ code file that implements the algorithm to reproduce said data via the FCN framework [
*fiction*](https://github.com/marcelwa/fiction).

### Source code: `defect_aware_physical_design.cpp`

The C++ code that implements the physical design algorithm presented in the paper. It utilizes the FCN framework [
*fiction*](https://github.com/marcelwa/fiction). To compile it, place the file in *fiction*'s `experiments` folder and
call CMake with the `-DFICTION_EXPERIMENTS=ON` flag.

To learn more, see *fiction*'s
[documentation on how to build experiments](https://fiction.readthedocs.io/en/latest/getting_started.html#building-experiments).

> **NOTE:** It might be necessary to adjust the file paths after copying the files into *fiction*'s experiment folder.

### Formatted data: `results/`

The folder contains raw data formatted as ASCII tables for all conducted experiments.

### Considered logic networks for physical design

The respective logic networks that were used as specification for the defect-aware physical design process were taken
from

*A Placement and Routing Algorithm for Quantum-dot Cellular Automata* by A. Trindade et al. in SBCCI
2016 ([IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/7724048))

and

*Placement and Routing by Overlapping and Merging QCA Gates* by G. Fontes et al. in ISCAS
2018 ([IEEE Xplore](https://ieeexplore.ieee.org/document/8351001)).

These networks are established benchmarks in the domain of FCN technologies and
are [available as Verilog files](https://github.com/marcelwa/fiction/tree/main/benchmarks) in
*fiction*'s experiment sandbox.
