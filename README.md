# FM-using-Python

Aim


To implement and analyze frequency modulation (FM) using Python's NumPy and Matplotlib libraries. 

Apparatus Required

1.	Software: Python with NumPy and Matplotlib libraries
2.	Hardware: Personal Computer
  
Theory

Frequency Modulation (FM) is a method of transmitting information over a carrier wave by varying its frequency in accordance with the amplitude of the input signal (message signal). The frequency of the carrier wave is varied according to the instantaneous amplitude of the message signal. The general form of an FM signal is:



Algorithm


1.	Initialize Parameters: Set the values for carrier frequency, message frequency, sampling frequency, and frequency deviation.
2.	Generate Time Axis: Create a time vector for the signal duration.
3.	Generate Message Signal: Define the message signal as a cosine wave.
4.	Compute the Integral of the Message Signal: Calculate the integral of the message signal over time.
5.	Generate FM Signal: Apply the FM modulation formula to obtain the modulated signal.
6.	Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal.

Program
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import hilbert

# Parameters
A_c = 1.0
f_c = 100 # Carrier frequency in Hz
f_m = 5
A_m = 0.5
sampling_frequency = 1000
duration = 1 # Duration of the signal in seconds

# Time axis
t = np.linspace(0, duration, int(sampling_frequency * duration))

# Message Signal
m_t = A_m * np.cos(2 * np.pi * f_m * t)

# Carrier Signal
c_t = A_c * np.cos(2 * np.pi * f_c * t)

# Amplitude Modulation (AM) Signal
s_t = (1 + m_t) * c_t

# AM Demodulation
# 1. Compute the analytic signal using the Hilbert transform
analytic_signal = hilbert(s_t)

# 2. Extract the envelope of the analytic signal
envelope = np.abs(analytic_signal)

# 3. Demodulate the signal by removing the DC offset and dividing by the carrier amplitude
demodulated_message = (envelope - A_c) / A_m

# Plotting the Results
plt.figure(figsize=(12, 10))

# Original Message Signal
plt.subplot(4, 1, 1)
plt.plot(t, m_t)
plt.title('Original Message Signal')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)

# Carrier Signal
plt.subplot(4, 1, 2)
plt.plot(t, c_t)
plt.title('Carrier Signal')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)

# Amplitude Modulated (AM) Signal
plt.subplot(4, 1, 3)
plt.plot(t, s_t)
plt.title('Amplitude Modulated (AM) Signal')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)

# Demodulated Signal
plt.subplot(4, 1, 4)
plt.plot(t, demodulated_message)
plt.title('Demodulated Signal')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)

plt.tight_layout()
plt.show()

Output Waveform
<img width="1198" height="990" alt="image" src="https://github.com/user-attachments/assets/46c02d6d-4011-4460-962f-0ad368c6a17c" />


Tabular Column
![WhatsApp Image 2025-10-15 at 13 27 00_66621914](https://github.com/user-attachments/assets/1d257e10-ea24-4414-b04d-4c305ef1dff5)



Calculation
<img width="1280" height="745" alt="image" src="https://github.com/user-attachments/assets/782eb556-b498-4e36-bac1-1e19a1c0dcd1" />




Result


The message signal, carrier signal, and frequency modulated (FM) signal will be displayed in separate plots. The modulated signal will show frequency variations corresponding to the amplitude of the message signal.
