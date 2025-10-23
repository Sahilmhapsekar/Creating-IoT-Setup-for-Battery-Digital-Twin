# Creating IoT Setup for Battery Digital Twin

IoT prototype that integrates Electrochemical Impedance Spectroscopy (EIS) with a battery digital twin. Implemented a low-amplitude sinusoidal excitation (STM32 / Arduino experiments), UART data logging, and initial impedance estimation for an INR18650-30Q cell.

## Key features
- DAC-based sine-wave generation (STM32G4 series) and PWM-based proof-of-concept (Arduino). 
- Data acquisition via ADC, UART logging and Python post-processing for plotting/analysis.  
- Initial EIS result: proof-of-concept impedance & phase estimation (~20 Hz test).
  
## Hardware
- Battery: INR18650-30Q (3.6–3.7 V nominal).  
- MCU: STM32G47x / NUCLEO-G474RE (DAC, ADC, DMA, TIM). 
- Shunt resistor for current sensing (used 7.5 Ω during tests).
- Charger/discharger: SkyRC iMAX B6 Mini (for controlled SoC).
  
## Firmware & tools
- STM32CubeIDE project: DAC + DMA + TIM for sine generation; ADC + UART for logging. 
- Arduino sketch (PWM prototype) used for early testing and demonstration. 
- Python scripts: serial reader → Excel/CSV logger; simple plotting (MATLAB/Python used for analysis). 

## Quick start
1. Open the STM32CubeIDE project and generate code for `NUCLEO-G474RE`. Configure DAC/ADC/UART as in `main.c`. 
2. Flash firmware, connect serial terminal (e.g., 115200 baud) to capture UART data. 
3. Run `python serial_logger.py` (reads COM port, saves CSV/XLSX). Post-process with provided analysis scripts to compute impedance/phase.
   
## Results
- Demonstrated low-amplitude sine generation and voltage/current capture.  
- Example measurement: ~20.2 Hz, applied V_pp ≈ 10 mV, calculated battery impedance ≈ 7.12 Ω and phase ≈ 101.8°. 

## Known limitations
- Could not fully integrate simultaneous amplitude + frequency control due to timing/synchronization and UART latency. Firmware latency limited higher-frequency EIS. 
