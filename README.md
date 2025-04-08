# Delta-Modulation
# Aim
To implement Delta Modulation (DM) and observe its output waveform
# Tools required
Python with NumPy & Matplotlib Signal generator (for hardware implementation) Comparator & Step-size adjuster ADC & DAC
# Program
```
import numpy as np
import matplotlib.pyplot as plt
fs = 1000
t = np.arange(0, 1, 1/fs)
f = 5
analog_signal = np.sin(2 * np.pi * f * t)
delta = 0.1
dm_signal = np.zeros_like(analog_signal)
quantized_signal = np.zeros_like(analog_signal)
for i in range(1, len(analog_signal)): if analog_signal[i] > quantized_signal[i - 1]: dm_signal[i] = 1 # Output bit
'1' quantized_signal[i] = quantized_signal[i - 1] + delta else: dm_signal[i] = 0 # Output bit '0'
quantized_signal[i] = quantized_signal[i - 1] - delta
plt.figure(figsize=(10, 5))
plt.plot(t, analog_signal, label='Original Analog Signal', linestyle='dashed')
plt.step(t, quantized_signal, where='mid', label='Delta Modulated Signal', color='red')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.title('Delta Modulation')
plt.legend()
plt.grid()
plt.show()
```
# Output Waveform
![image](https://github.com/user-attachments/assets/b069872c-9d57-4ce7-84e4-6be1cb3d5628)

# Results
The analog signal was successfully converted using Delta Modulation. The signal was approximated using a stepwise function based on delta-step adjustments. The Delta Modulated waveform was observed, demonstrating the tracking process.
