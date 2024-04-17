# Twice win game implemented in verilog

## Problem Statement( refer to the pdf attached ) ->
 It is a game played between two individuals. This game is played by two or more individuals.
 The fundamental rule is that the selected number is subtracted by the highest possible power of two. Players take turns 
 subtracting, and the one who makes the last move wins. If played between two players, there are three rounds in total.
 The individual who wins two rounds emerges as the overall winner.

 ## Let's break the code ->

 ### Inputs and Outputs:
 Inputs:
 clk: Clock signal
 reset: Reset signal
 N1, N2, N3: 8-bit input values
 Outputs:
 vini, nai: Output signals

 ### Registers and Wires:
 temp: 9-bit register used for temporary storage.
 VINI, NAI, round: 2-bit registers.
 count: 4-bit register used for counting.
 n, sub_temp: 8-bit registers.
 stop: Wire used to determine when to stop processing based on the round signal.

### FSM States:
IDLE, START, ASSIGN_N, ASSIGN_TEMP, LEFT_SHIFT, COMP, RIGHT_SHIFT, SUB, ASSIGN_SUB, CHECK_N, ODD_RND, EVEN_RND, RESULT.
Each state performs specific operations based on the current state and input values.

### State Transition Logic:
The state transition logic is implemented in the combinational block using a case statement. Depending on the current state, it determines the next state.
The STOP signal is used to stop processing when the round exceeds 3.

### State Logic:
The combinational block also contains logic corresponding to each state. It performs various operations based on the current state.
Operations include assigning values, shifting bits left or right, subtracting, incrementing counters, and determining the next value of VINI and NAI based on conditions.

### Output Logic:
The output vini is assigned based on whether VINI is greater than NAI.
The output nai is assigned based on whether NAI is greater than VINI.

### Overall Functionality:
The code essentially processes the input values in rounds. It shifts a temporary value (temp) left or right, subtracts it from the current input value (n), and updates counters and output values accordingly.
The FSM ensures the sequence of operations and handles different cases depending on the values and the round number.
