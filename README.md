### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**

/* write all the steps invloved */

**PROGRAM**
upcounter
```
module Upcounter (out, clk, rstn);
input clk, rstn;
output reg [3:0] out;

always @(posedge clk)
begin
    if (!rstn)
        out <= 0;
    else
        out <= out + 1;
end
endmodule
```
downcounter
method 1
```
module Downcounter (
    output reg [3:0] out,
    input clk,
    input rstn
);

always @ (posedge clk) begin
    if (!rstn)
        out <= 4'b1111;                                                 
    else if (out == 4'b0000)
        out <= 4'b1111; // Wrap around to maximum count when reaching 0
    else
        out <= out - 1; // Decrement count
end

endmodule
```
method 2
```
module Downcounter (
    output reg [3:0] out,
    input clk,
    input rstn
);

always @ (posedge clk) begin
    if (!rstn)
        out <= 4'b1111;                                                 
    else
        out <= out - 1'b1; // Decrement count using 1'b1
end

endmodule

```
/* Program for flipflops and verify its truth table in quartus using Verilog programming. 

Developed by: RegisterNumber:25017492
*/

**RTL LOGIC UP COUNTER**
<img width="1919" height="1079" alt="Screenshot 2025-12-17 203636" src="https://github.com/user-attachments/assets/3a01f7e1-85d0-429f-803a-8c268dcddfd9" />


**TIMING DIAGRAM FOR IP COUNTER**
<img width="1919" height="1079" alt="Screenshot 2025-12-17 203839" src="https://github.com/user-attachments/assets/863001b3-fd1d-4efc-95a7-a3355b912668" />


**TRUTH TABLE**
<img width="408" height="287" alt="Screenshot 2025-12-17 204940" src="https://github.com/user-attachments/assets/7b509af4-3a11-4158-b9c8-ecf1461991f3" />


**RESULTS**
To implement 4 bit synchronous up counter and validate functionality is succeed.

