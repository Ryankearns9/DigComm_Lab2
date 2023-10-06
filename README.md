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


### Software
1. GNU Radio
 - https://www.gnuradio.org/

## Algorithm Description
This section details the specific algorithm implimented in GNU Radio. It includes the overall flow diagram along with specific descriptions of each part.

### Flow Diagram
The below figure shows the overall flow diagram of the algorithm. It includes the RTL-SDR hardware, resamplers, FM Demod, low pass filter, and audio sink. Additional modules inlcude the GUI functions, GUI variables, and constants for the program. Each will be detailed throughout this section.
![alt text](https://github.com/Ryankearns9/DigComm_Lab2/blob/main/imgs/FlowDiagram.PNG)

### RTL-SDR Source
The below image shows the RTL-SDR source. The specific hardware is linked above with a full description in Lab 1. This module acts as the ADC and antenna for this module. It basebands the signal of interest with the center frequency being chosen by the GUI variable "center_freq." Further description of this variable is detailed below. The sampling rate is chosen by the constant samp_rate and is set to 2 MHz.

Of note, the Nooelec NESDR SMArt XTR SDR basebands and filters the signal using the E4000 architecture. This prevents interference and aliasing from out of bandwidth signals.

![alt text](https://github.com/Ryankearns9/DigComm_Lab2/blob/main/imgs/RTL_Source.PNG)

The RTL-SDR Source is fed into the first rational resampler 

### Rational Resampler 1
The below image shows the first rational resampler used in the flow chart. It is fed by the RTL SDR source and feeds the low pass filter. A deeper description into rational resampling can be found in Lab 1.

The specific parameters for this module were chosen to be an interpolation rate of 1 and a decimation rate of 5. This decimates the sampling rate to 400 kHz. The FTC puts channel spacing at 100 kHz for FM broadcasting. Decimating to 400 kHz allows an oversampling ratio of 4 which reduces error when demodulating the waveform, thus creating a cleaner signal

![alt text](https://github.com/Ryankearns9/DigComm_Lab2/blob/main/imgs/RationalResampler.PNG)

The first rational resampler feeds the low pass filter

### Low Pass Filter
The low pass filter parameters are described in the below chart. As described in the previous section, the channel size as defined by the FTC is 100kHz. Filtering in this case prevents adjacent channel interference when demodulating the waveform. Without this filter, adjacent channels may leak through to the FM demod creating a much noiser signal.

| Parameter        | Value         |
| ---------------- |:-------------:|
| Fitler Type      | Hamming       |
| Beta             | 6.76          |
| Passband Edge    | 100kHz        |
| Transition Width | 25kHz         |

![alt text](https://github.com/Ryankearns9/DigComm_Lab2/blob/main/imgs/LowPassFilter.PNG)