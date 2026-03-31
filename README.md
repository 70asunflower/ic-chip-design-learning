# IC Chip Design Learning Journey 🖥️🔬

> A collection of resources, notes, code, and project explorations in IC chip design — from RTL to tapeout.

---

## Wiki Navigation

<details open>
<summary><b>📚 Resources</b></summary>

<details>
<summary>1-Books</summary>

_Empty — add your first book!_

</details>

<details>
<summary>2-Papers</summary>

_Empty — add your first paper!_

</details>

<details>
<summary>3-EDA-Tools</summary>

_Empty — add your first EDA tool note!_

</details>

<details>
<summary>4-OpenSource-Projects</summary>

_Empty — add your first open-source project!_

</details>

<details>
<summary>5-Courses-Tutorials</summary>

_Empty — add your first course/tutorial!_

</details>

<details>
<summary>6-Industry-Standards</summary>

_Empty — add your first industry standard!_

</details>

[📋 Full Resource Index](0-Resources/0-Index.md)

</details>

<details open>
<summary><b>📝 Personal Notes</b></summary>

<details>
<summary>1-Digital-Design</summary>

_Empty — add your first digital design note!_

</details>

<details>
<summary>2-Analog-Design</summary>

_Empty — add your first analog design note!_

</details>

<details>
<summary>3-Verification</summary>

_Empty — add your first verification note!_

</details>

<details>
<summary>4-Physical-Design</summary>

_Empty — add your first physical design note!_

</details>

<details>
<summary>5-DFT</summary>

_Empty — add your first DFT note!_

</details>

<details>
<summary>6-PDK-Process</summary>

_Empty — add your first PDK/process note!_

</details>

[📋 Note Template](1-Notes/0-Template.md)

</details>

<details>
<summary><b>💻 Code & Projects</b></summary>

<details>
<summary><a href="2-Code/README.md">Code Examples</a></summary>

<details>
<summary>rtl-examples</summary>

_Empty — add an RTL example!_

</details>

<details>
<summary>uvm-testbench</summary>

_Empty — add a UVM testbench!_

</details>

<details>
<summary>tcl-scripts</summary>

_Empty — add a TCL script!_

</details>

<details>
<summary>python-tools</summary>

_Empty — add a Python tool!_

</details>

<details>
<summary>openroad-flows</summary>

_Empty — add an OpenROAD flow!_

</details>

</details>

<details open>
<summary><a href="3-Projects/README.md">Projects</a></summary>

<details>
<summary>riscv-core</summary>

_Empty — start the RISC-V core project!_

</details>

<details>
<summary>accelerator</summary>

_Empty — start the accelerator project!_

</details>

<details>
<summary>mixed-signal-soc</summary>

_Empty — start the mixed-signal SoC project!_

</details>

<details>
<summary>tapeout-prep</summary>

_Empty — start the tapeout prep project!_

</details>

</details>

</details>

---

## Directory Structure

```
ic-chip-design-learning/
├── 0-Resources/              # External resources
│   ├── 0-Index.md            # Full resource index
│   ├── 1-Books/              # IC design textbooks & references
│   ├── 2-Papers/             # Research papers
│   ├── 3-EDA-Tools/          # EDA tool notes (Synopsys, Cadence, Si2, etc.)
│   ├── 4-OpenSource-Projects/# Open-source chip projects
│   ├── 5-Courses-Tutorials/  # Online courses & tutorials
│   └── 6-Industry-Standards/ # AMBA, UCIe, JEDEC, etc.
├── 1-Notes/                  # Personal study notes
│   ├── 1-Digital-Design/    # Combinational/sequential, HDL, microarchitecture
│   ├── 2-Analog-Design/     # Amplifiers, PLLs, ADCs/DACs, layout
│   ├── 3-Verification/      # UVM, formal verification, coverage
│   ├── 4-Physical-Design/   # Synthesis, PnR, STA, signoff
│   ├── 5-DFT/               # Scan, BIST, JTAG, ATPG
│   └── 6-PDK-Process/       # Process nodes, PDKs, DRC/LVS
├── 2-Code/                   # Runnable code & scripts
│   ├── rtl-examples/        # Verilog/SystemVerilog RTL examples
│   ├── uvm-testbench/       # UVM testbench components
│   ├── tcl-scripts/         # EDA TCL scripts (DC, ICC2, Innovus)
│   ├── python-tools/        # Python utilities for chip design
│   └── openroad-flows/      # OpenROAD ASIC flow scripts
├── 3-Projects/               # Comprehensive projects
│   ├── riscv-core/          # RISC-V CPU core implementation
│   ├── accelerator/         # Domain-specific accelerator design
│   ├── mixed-signal-soc/    # Mixed-signal SoC project
│   └── tapeout-prep/        # Tapeout preparation checklist & GDS
├── scripts/                  # Helper scripts
└── README.md
```

## How to Update

### Adding a New Resource (0-Resources/)

1. Create a `.md` file in the correct subfolder (e.g. `0-Resources/3-EDA-Tools/synopsys-dc.md`)
2. Start with this frontmatter:
   ```markdown
   ---
   source: <original URL>
   date: YYYY-MM-DD
   tags: [tag1, tag2]
   ---
   ```
3. Write the content: summary, key points, or full notes with source attribution
4. End with: `_Last updated: YYYY-MM-DD_`
5. Add it to the folder's `README.md` index
6. Add it to the wiki nav in this file under `<details>`
7. Add it to `0-Resources/0-Index.md`

### Adding a New Note (1-Notes/)

1. Create a `.md` file in the correct subfolder (e.g. `1-Notes/1-Digital-Design/fsm-design.md`)
2. Start with the same frontmatter as above
3. Write your personal understanding, code experiments, gotchas
4. End with: `_Last updated: YYYY-MM-DD_`
5. Add the link to the folder's `README.md` index
6. Add the link to the wiki nav in this file

### Adding to Code Examples (2-Code/)

1. Create a subfolder: `2-Code/<project-name>/`
2. Include: source file, `README.md`
3. Add it to `2-Code/README.md`

### Key Rules

- **File names**: lowercase, hyphen-separated (e.g. `axi-bus-protocol.md`)
- **Wiki nav**: every new file must be linked in this README
- **Resource Index**: `0-Index.md` mirrors all resources — keep it in sync
- **Always include `Last updated`**: every resource/note file ends with `_Last updated: YYYY-MM-DD_`

## Changelog

| Date       | Content                                       |
|------------|-----------------------------------------------|
| 2026-03-31 | Repository init, directory structure, wiki nav|
| 2026-03-31 | Added note template                           |
