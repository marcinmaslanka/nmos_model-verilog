# ⚙️ From Verilog-A to Simulation in ADE (Cadence Virtuoso)

This repository shows how to model a nMOS Transistor in Verilog-A, integrate it into a Cadence Virtuoso project, and simulate it using ADE.

---

## 📄 1. Write the Verilog-A Model

Create your Verilog-A module in a file with `.va` extension. Example:

```verilog
`include "discipline.h"

module nmos_simple (
    input  electrical gate,
    input  electrical source,
    output electrical drain
);

    parameter real K   = 1e-3;   // Transconductance parameter
    parameter real Vth = 0.7;    // Threshold voltage

    analog begin
        I(drain, source) <+ (V(gate, source) > Vth) ?
            0.5 * K * (V(gate, source) - Vth)**2 : 0;
    end

endmodule

```

## 🧱 2. Create the Verilog-A Cell in Virtuoso

  Open Library Manager.
  Choose your target library or create a new one.
  Go to: File → New → CellView
  Cell Name: e.g. nmos_simple
  View Name: veriloga
  Tool: Verilog-A
  Paste your Verilog-A code.
  Click Check and Save.

## 🧩 3. Create Symbol for the Verilog-A Model

  In the Verilog-A cell, go to Tools → Create Cellview → From Cellview.
  Set Tool to Symbol.
  Click OK to generate a symbol.

## 🔌 4. Instantiate in a Schematic

  Open your testbench schematic.
  Place the Verilog-A symbol into the design.
  Connect it with other components.
  Save the schematic.

  
![nmos](https://github.com/user-attachments/assets/12e0874e-9d06-49ca-ae23-8ee06ae9d632)

  

## 🧪 5. Run Simulation in ADE

  Open ADE (Assembler/Explorer).
  Set up your testbench as the top-level.
  Configure simulation type (e.g. tran, dc, ac).
  Choose outputs to plot (e.g. node voltages).
  Click Run.

![nmos](https://github.com/user-attachments/assets/40f6b3e4-0a29-4c82-83e1-fd89662d88b6)


---


🙌 Contributions Welcome

Feel free to fork this repo and adapt it for other Verilog-A components like resistors, amplifiers, or sensors!
