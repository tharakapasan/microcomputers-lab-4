# MICROCOMPUTERS LAB-4

# OBJECTIVES

The paper presents the design and implementation of the water level monitoring and controlling system, which aims to overcome of issues that may present because of using manual systems for filling up domestic water tanks. <br>

# INTRODUCTION

<img src="https://user-images.githubusercontent.com/109506588/184952529-a0aef32c-915b-4d82-9b5e-a58292d770b9.png" width=500 >

The block diagram illustrated in FIG. 1 gives an overview of the proposed water level monitoring and control system, which consists of a PIC microcontroller as the heart of the system and the oscillator to generate the clock pulses needed to synchronize all the internal operations of the  PIC microcontroller, the power supply, to provide the necessary voltages for the proposed system, the water level sensor to measure the water level in a domestic tank, the water pump control unit to switch on or turn off the pump according to the water level. In the proposed system, the infrared sensor is used to measure the water level by measuring the distance between the water surface and the sensor and based on this distance, the amount of water inside the tank. can be determined.



<img src="https://user-images.githubusercontent.com/109506588/185412371-b3f1c17d-8b9f-4a5c-bd4d-f5d1ac601ccf.png" width=500>

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

<img src="https://user-images.githubusercontent.com/109506588/185413210-c08e7abd-864e-40fa-b161-774bb7ed53bb.png" width=500>

<img src="https://user-images.githubusercontent.com/109506588/185413775-6dc34581-9568-455a-a558-91cc511731d3.png" width=500>

<img src="https://user-images.githubusercontent.com/109506588/185414965-ab482797-e3d8-4ac7-a4f2-0f378c521c0b.png" width=500>

<img src="https://user-images.githubusercontent.com/109506588/185415330-ef3d706f-6761-4a0b-bd35-5be7bb428579.png" width=500>

<img src="https://user-images.githubusercontent.com/109506588/185415884-57b330b9-6840-4885-a650-62f4f9047e27.png" width=500>


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

<img src="https://user-images.githubusercontent.com/109506588/185416303-946067c4-e77c-4c3a-9877-55bf36839e9c.png" width=600>

The suggested water level monitoring and control system's implementation consists of both hardware and software implementation. The power supply unit, oscillator unit and water pump are all covered by Former's implementation, as illustrated in Fig.2 . The infrared range sensor is implemented as seen in Fig. 4 and is used to monitor the water level within a tank. The IR sensor, when detects an object, it gives a logic low output and when it doesn’t detect any object, it gives a logic high. The PORTB pin 0, pin 1 and pin 2 are used to link the sensor to the microcontroller. So, in here, switch 1 is connected to the port B pin 0, switch 2 is connected to the port B pin 1 and switch 3 is connected to the port B pin 2. A water module device is used to implement the water level pump control unit, allowing low power circuits to switch a relatively high current/voltage.

The PIC microcontroller and the water pump control unit are connected by the pin 0 and 1 on the PORTC. Depending on the water level, the microcontroller produces logic low or high on the pin 0 and 1 on PORT C to turn the pump on or off.


<img src="https://user-images.githubusercontent.com/109506588/185545953-be95371e-e73e-4663-8667-1c07dc31f8ac.png" width= 400>

In here, we use sensors as the switches.So, this is the hardware implementation of this project. We used arduio board 5v regulated power output to give power to the pic ic.Not only that, we used 5v 2A power pack to give power to the motors and motor module. According to the above table-1, if the switch 1 is on and switch 2 and 3 are off and then the motor 1 will on and motor 2 will off. If the switch 1 and 2 are on and switch 3 is off, then the motor 1 will on and motor 2 will off. If the all swiches are on, the the motor 1 will off and the motor 2 will on at first and then it will off after 500 miliseconds. 

## The Code

    #pragma config FOSC = HS        // Oscillator Selection bits (HS oscillator)
    #pragma config WDTE = OFF       // Watchdog Timer Enable bit (WDT disabled)
    #pragma config PWRTE = OFF      // Power-up Timer Enable bit (PWRT disabled)
    #pragma config BOREN = OFF      // Brown-out Reset Enable bit (BOR disabled)
    #pragma config LVP = OFF        // Low-Voltage (Single-Supply) In-Circuit Serial Programming Enable bit (RB3 is digital I/O, HV on MCLR must be used for programming)
    #pragma config CPD = OFF        // Data EEPROM Memory Code Protection bit (Data EEPROM code protection off)
    #pragma config WRT = OFF        // Flash Program Memory Write Enable bits (Write protection off; all program memory may be written to by EECON control)
    #pragma config CP = OFF         // Flash Program Memory Code Protection bit (Code protection off)



    #include <xc.h>
    #include<htc.h> 

    #define _XTAL_FREQ 20000000


    void __interrupt() isr(void){
    if(RB1 ==1 && RB2 ==1){
        RC0 =0;
        RC1 =1;
        __delay_ms(500);
        RC1 =0;
    }
    INTF =0;
    }

    void main (void){
    INTF =0;
    INTE =1;
    GIE =1;
    INTEDG =1;
    
    TRISB0 =1;  //SWITCH 3
    TRISB1 =1;  //SWITCH 2
    TRISB2 =1;  //SWITCH 1
    TRISC0 =0;  //MOTOR 1
    TRISC1 =0;  //MOTOR 2
    
    while(1){
        if(RB2 ==1 && RB1 ==0 && RB0 ==0){
            RC0 =1;
        RC1 =0;
        }
         if(RB2 ==1 && RB1 ==1 && RB0 ==0){
            RC0 =1;
        RC1 =0;
        }
         if(RB2 ==0 && RB1 ==0 && RB0 ==0){
            RC0 =0;
        RC1 =0;
        }
    }
    return();
}





























