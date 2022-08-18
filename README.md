# MICROCOMPUTERS LAB-4

# OBJECTIVES

The paper presents the design and implementation of the water level monitoring and controlling system, which aims to overcome of issues that may present because of using manual systems for filling up domestic water tanks. <br>

# INTRODUCTION

<img src="https://user-images.githubusercontent.com/109506588/184952529-a0aef32c-915b-4d82-9b5e-a58292d770b9.png" width=300>

The block diagram illustrated in FIG. 1 gives an overview of the proposed water level monitoring and control system, which consists of a PIC microcontroller as the heart of the system and the oscillator to generate the clock pulses needed to synchronize all the internal operations of the  PIC microcontroller, the power supply, to provide the necessary voltages for the proposed system, the water level sensor to measure the water level in a domestic tank, the water pump control unit to switch on or turn off the pump according to the water level. In the proposed system, the infrared sensor is used to measure the water level by measuring the distance between the water surface and the sensor and based on this distance, the amount of water inside the tank. can be determined.



<img src="https://user-images.githubusercontent.com/109506588/185412371-b3f1c17d-8b9f-4a5c-bd4d-f5d1ac601ccf.png" width=300>

The benefits of the proposed water level monitoring and control system can be surmised as follows: 

(i)	Saving power, this is because the amount of electricity used is limited due to the automatic controlling of water level. 

(ii)	Since the motor pump is turned off automatically when water is reaching the high level of the tank, there is no need to check the water level manually and as result of that the time is saving.   

(iii)	Water usage can be maximized with a water level control system. This is because the proposed monitoring system automatically provides more water during the middle of the day and less water at night based on the water level. As a result, water always remains at its appropriate level.

Water regulation is optimized using the water level control system, which means that wasted electricity and water is kept at a minimum and as result of this a substantial amount of money over time is saved.

# APPARATUS


•	PCB board

•	PIC16F877A

•	IR sensors 3

•	motors

•	jumper cables 

•	motor module

•	capacitors

•	crystal oscillators

•	resistors

•	pic adapter 

•	soldering iron

<img src="https://user-images.githubusercontent.com/109506588/185413210-c08e7abd-864e-40fa-b161-774bb7ed53bb.png" width=300>

<img src="https://user-images.githubusercontent.com/109506588/185413775-6dc34581-9568-455a-a558-91cc511731d3.png" width=300>

<img src="https://user-images.githubusercontent.com/109506588/185414965-ab482797-e3d8-4ac7-a4f2-0f378c521c0b.png" width=300>



# PROCEDURE

* First, PCB design of the circuit has been designed by the proteus software.
* By using that design, PCB board has been made from a copper board, and ferric chloride was used to remove excessive copper parts.
* Components are soldered to PCB board. 
*	After that, appropriate code has been written by MP lab.
*	By using pik kit 3, that code was uploaded to the PIC16F877A.
*	After that, 3 sensors are connected to the PIC16F877A through the connecters in the board.
*	Next, a motor module is connected to the PIC16F877A through the connecters of the board.
*	Motors are connected appropriate to the motor module.
* Finally, one external power supply is connected to the micro controller and another power supply is given to the motors.


# DISCUSSION

The suggested water level monitoring and control system's implementation consists of both hardware and software implementation. The power supply unit, oscillator unit and water pump are all covered by Former's implementation, as illustrated in Fig. 4. The infrared range sensor is implemented as seen in Fig. 2 and is used to monitor the water level within a tank. The IR sensor, when detects an object, it gives a logic low output and when it doesn’t detect any object, it gives a logic high. The PORTB pin 0, pin 1 and pin 2 are used to link the sensor to the microcontroller. So, in here, switch 1 is connected to the port B pin 0, switch 2 is connected to the port B pin 1 and switch 3 is connected to the port B pin 2. A water module device is used to implement the water level pump control unit, allowing low power circuits to switch a relatively high current/voltage.

The PIC microcontroller and the water pump control unit are connected by the pin 0 and 1 on the PORTC. Depending on the water level, the microcontroller produces logic low or high on the pin 0 and 1 on PORT C to turn the pump on or off.































