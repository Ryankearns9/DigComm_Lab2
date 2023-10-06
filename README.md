# Lab 2
## Introduction
Lab 2's objective is to build an FM radio reciever using an SDR kit along with the program gnu radio. This document outlines the critical features of the GNU radio which I built.

## Equipment List
The following section outlines the equipment used in this lab. All equipment can be purchased following the links provided

### Hardware
1. ASUS Laptop
 - https://www.amazon.com/Performance-Premium-Processor-SuperMulti-10-Silver/dp/B01KAP7RJG
2. Nooelec NESDR SMArt XTR Bundle
 - https://www.nooelec.com/store/nesdr-smart-xtr.html
  - Details on the specific SDR kit can be found following the attached link. Further information is contained in the Lab 1 report

![alt text](https://github.com/Ryankearns9/DigComm_Lab2/blob/main/imgs/FlowDiagram.PNG)

### Software
1. GNU Radio
 - https://www.gnuradio.org/

## Algorithm Description
This section details the specific algorithm implimented in GNU Radio. It includes the overall flow diagram along with specific descriptions of each part.

### Flow Diagram
The below figure shows the overall flow diagram of the algorithm. It includes the RTL-SDR hardware, resamplers, FM Demod, low pass filter, and audio sink. Additional modules inlcude the GUI functions, GUI variables, and constants for the program. Each will be detailed throughout this section.
![alt text](https://github.com/Ryankearns9/DigComm_Lab2/blob/main/imgs/FlowDiagram.PNG)

#### RTL-SDR Source
The below image shows the RTL-SDR source.
![alt text](https://github.com/Ryankearns9/DigComm_Lab2/blob/main/imgs/RTL_Source.PNG)