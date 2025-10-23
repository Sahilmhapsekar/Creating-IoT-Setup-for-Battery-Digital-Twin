# Creating IoT Setup for Battery Digital Twin

**Short description**
IoT prototype that integrates Electrochemical Impedance Spectroscopy (EIS) with a battery digital twin. Implemented a low-amplitude sinusoidal excitation (STM32 / Arduino experiments), UART data logging, and initial impedance estimation for an INR18650-30Q cell. :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1}

## Key features
- DAC-based sine-wave generation (STM32G4 series) and PWM-based proof-of-concept (Arduino). :contentReference[oaicite:2]{index=2} :contentReference[oaicite:3]{index=3}  
- Data acquisition via ADC, UART logging and Python post-processing for plotting/analysis. :contentReference[oaicite:4]{index=4}  
- Initial EIS result: proof-of-concept impedance & phase estimation (~20 Hz test). :contentReference[oaicite:5]{index=5}

## Hardware
- Battery: INR18650-30Q (3.6–3.7 V nominal). :contentReference[oaicite:6]{index=6}  
- MCU: STM32G47x / NUCLEO-G474RE (DAC, ADC, DMA, TIM). :contentReference[oaicite:7]{index=7}  
- Shunt resistor for current sensing (used 7.5 Ω during tests). :contentReference[oaicite:8]{index=8}  
- Charger/discharger: SkyRC iMAX B6 Mini (for controlled SoC). :contentReference[oaicite:9]{index=9}

## Firmware & tools
- STM32CubeIDE project: DAC + DMA + TIM for sine generation; ADC + UART for logging. :contentReference[oaicite:10]{index=10}  
- Arduino sketch (PWM prototype) used for early testing and demonstration. :contentReference[oaicite:11]{index=11}  
- Python scripts: serial reader → Excel/CSV logger; simple plotting (MATLAB/Python used for analysis). :contentReference[oaicite:12]{index=12}

## Quick start
1. Open the STM32CubeIDE project and generate code for `NUCLEO-G474RE`. Configure DAC/ADC/UART as in `main.c`. :contentReference[oaicite:13]{index=13}  
2. Flash firmware, connect serial terminal (e.g., 115200 baud) to capture UART data. :contentReference[oaicite:14]{index=14}  
3. Run `python serial_logger.py` (reads COM port, saves CSV/XLSX). Post-process with provided analysis scripts to compute impedance/phase. :contentReference[oaicite:15]{index=15}

## Results (summary)
- Demonstrated low-amplitude sine generation and voltage/current capture.  
- Example measurement: ~20.2 Hz, applied V_pp ≈ 10 mV, calculated battery impedance ≈ 7.12 Ω and phase ≈ 101.8°. :contentReference[oaicite:16]{index=16}

## Known limitations
- Could not fully integrate simultaneous amplitude + frequency control due to timing/synchronization and UART latency. Firmware latency limited higher-frequency EIS. :contentReference[oaicite:17]{index=17}

## Files / docs
- Full report, progress report and slides are in the repo (`DEP_CP301_Report.pdf`, `DEP Progress Report-1.pdf`, `DEP_PPT.pptx`). :contentReference[oaicite:18]{index=18} :contentReference[oaicite:19]{index=19} :contentReference[oaicite:20]{index=20}

## License
MIT
