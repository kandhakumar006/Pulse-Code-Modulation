## AIM:
The aim of Pulse Code Modulation (PCM) is to convert an analog signal into a digital form by sampling, quantizing, and encoding it into binary format. This process ensures accurate transmission and storage of signals in digital systems. PCM enhances signal quality and error detection, making it crucial in audio, telecommunications, and multimedia applications.

## Components Required:
python IDE with Numpy and Scipy

## Program:
```
import matplotlib.pyplot as plt
import numpy as np

sampling_rate = 5000
frequency = 50
duration = 0.1
quantization_levels = 16

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels
quantized_signal = np.round(message_signal / quantization_step) * quantization_step

pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step
pcm_signal = pcm_signal.astype(int)

plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)
plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')
plt.title("Message Signal (Analog)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.subplot(4, 1, 2)
plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green')
plt.title("Clock Signal (Increased Frequency)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.subplot(4, 1, 3)
plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red')
plt.title("PCM Modulated Signal (Quantized)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.subplot(4, 1, 4)
plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')
plt.title("Signal Without Demodulation")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.tight_layout()
plt.show()
```
## Output Waveforms:
![Image 2025-03-28 at 10 52 24_c0a5432e](https://github.com/user-attachments/assets/fae677be-40de-44e1-bda8-191ba402cc73)


## Result:
Pulse Code Modulation (PCM) converts analog signals into digital form by sampling and quantizing the signal. The result is a series of pulses that represent the digitized version of the original signal, widely used in audio and telecommunications.
