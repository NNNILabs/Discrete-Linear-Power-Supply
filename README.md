# Discrete Linear Power Supply
Fully discrete dual tracking linear supply with CC and CV

## Why?
I was not fully satsified with my previous linear supply based on op-amps, so I decided that I was done with the "black box" approach and decided to go fully discrete this time. 

## How?
The linear supply consists of three parts - the reference, the constant voltage circuit and the constant current circuit. The positive and negative parts are more or less mirror images of each other. 

### The References
The reference element here is a zener diode. The circuit does not operate using reference voltages, but rather reference currents supplied by degenerated PNP/NPN current sources/sinks. 
The Zener diode sets the voltage across the emitter resistors of the buffer transistors, forming current sources/sinks. This current is mirrored and fed back into the Zener diodes, creating a stable closed-loop reference. 

### The Current Limiting Circuitry
The current limiting circuitry is a mix of at least three different circuit ideas from various sources - the emitter input differential amplifier from The Art of Electronics: The X Chapters, the ZDS1009 IC, and the current comparator from Designing Analog Chips. The easiest explanantion is that a constant voltage is set across the left degeneration resistor of the mirror ladder, and when the shunt exceeds this voltage, the output transistor is turned on, pulling the output MOSFET low till the current setpoint is reached. The limit threshold is set by a constant current through the set potentiometer, the voltage across which is mirrored on a resistor which sets the current through the degeneration resistor, the voltage across whic determines the shunt voltage threshold.

### The Voltage Regulating Circuitry 
Again an example of emitter input differential amplifiers - the circuit tries to make the emitter voltages the same and drives the output MOSFET accordingly. The voltage is set by a constant current through the set potentiometer. 

### Notes
- Dual tracking is achieved by sinking/sourcing the same current through the set potentiometers, which creates a voltage across it based on the resistance. Since the current source outputs would otherwise be "floating" (i.e., the voltage across the shunt is constant but there is no guarantee as to where it is relative to ground), two 1M balance resistors connected to ground are added. 
- 
