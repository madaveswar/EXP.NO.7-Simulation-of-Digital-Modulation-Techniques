# EXP.NO.7-Simulation-of-Digital-Modulation-Techniques
7. Simulation of Digital Modulation Techniques Such as
   i) Amplitude Shift Keying (ASK)
   ii) Frequency Shift Keying (FSK)
   iii) Phase Shift Keying (PSK)

# AIM
```
To study the python simulation for digital modulation techniques.
```
# SOFTWARE REQUIRED
```
colab software
```
# ALGORITHMS
```
Step 1:Import libraries for numerical operations, plotting, and IPython tools.
Step2:Initialize parameters like input data, bit duration, sampling frequency, and modulation frequencies.
Step3:Create time vector for one bit duration.
Step4:Define ASK function that returns a cosine wave for bit 1, and zeros for bit 0.
Step5:Modulate ASK signal by applying the ASK function to each bit.
Step6:Generate digital signal by repeating each bit for Fs samples.
Step7:Modulate FSK signal by switching frequency for each bit and generating sine waves.
Step8:Modulate PSK signal by changing phase (0 or π) based on the bit value.
Step9:Create total time axis for plotting the full signal duration.
Step10:Plot digital and modulated signals (ASK, FSK, PSK) in subplots with labels and grid.
```
# PROGRAM
```
import numpy as np
from IPython import get_ipython
from IPython.display import display
# %%
import matplotlib.pyplot as plt
data = [1, 0, 1, 1, 0]
bit_duration = 1
Fs = 1000  
t_bit = np.linspace(0, bit_duration, Fs, endpoint=False)
f1 = 20
f0 = 4
f_c = 5  
def ask(bit):
    return np.cos(2 * np.pi * f_c * t_bit) if bit == 1 else np.zeros(len(t_bit))
def repeat_waveform(fn, bitstream):
    modulated = []
    for b in bitstream:
        modulated.extend(fn(b))
    return modulated
digital = np.repeat(data, Fs)
ask_signal = repeat_waveform(ask, data)
fsk_signal = []
for bit in data:
    freq = f1 if bit else f0
    wave = np.sin(2 * np.pi * freq * t_bit)
    fsk_signal.extend(wave)
psk_signal = []
for bit in data:
    phase = 0 if bit == 1 else np.pi
    wave = np.sin(2 * np.pi * f_c * t_bit + phase)
    psk_signal.extend(wave)
time = np.linspace(0, bit_duration * len(data), Fs * len(data), endpoint=False)
plt.figure(figsize=(14, 10))
plt.subplot(4, 1, 1)
plt.plot(time, digital, color='black')
plt.title("Digital Input Signal")
plt.ylabel("Amplitude")
plt.grid(True)
plt.subplot(4, 1, 2)
plt.plot(time, ask_signal, color='green')
plt.title("Amplitude Shift Keying (ASK using Cosine Carrier)")
plt.ylabel("Amplitude")
plt.grid(True)
plt.subplot(4, 1, 3)
plt.plot(time, fsk_signal, color='blue')
plt.title("Frequency Shift Keying (FSK)")
plt.ylabel("Amplitude")
plt.grid(True)
plt.subplot(4, 1, 4)
plt.plot(time, psk_signal, color='red')
plt.title("Phase Shift Keying (PSK)")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid(True)

plt.tight_layout()
plt.show()
```
# OUTPUT

![Screenshot 2025-04-15 172831](https://github.com/user-attachments/assets/5530485e-b757-48ae-ba47-8042a37e0fba)


# RESULT / CONCLUSIONS
```
Thus the digital modulation schemes such as ASK, FSK and PSK are studied via simulation.
```

