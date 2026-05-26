# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
clear;
close;

// Filter specifications
M = 50;            // Filter order
fc = 0.4;          // Normalized cutoff frequency (0 to 0.5)

// Sample points
n = 0:M;

// Ideal impulse response of High Pass Filter
hd = zeros(1, M+1);
for i = 1:M+1
    if i == (M/2 + 1) then
        hd(i) = 1 - 2*fc;
    else
        hd(i) = (-sin(2*%pi*fc*(i - (M/2 + 1)))) / (%pi*(i - (M/2 + 1)));
    end
end

// Hamming window
w = 0.54 - 0.46 * cos(2*%pi*n/M);

// Apply window
h = hd .* w;

// Plot Impulse Response
figure(1);
plot(n, h);
xlabel("n");
ylabel("h(n)");
title("Impulse Response of High Pass FIR Filter using Hamming Window");
xgrid();

// Frequency Response
[H, f] = frmag(h, 512);
figure(2);
plot(f, H);
xlabel("Normalized Frequency");
ylabel("|H(f)|");
title("Magnitude Response of High Pass FIR Filter using Hamming Window");
xgrid();

# OUTPUT
<img width="1600" height="999" alt="WhatsApp Image 2026-05-26 at 11 09 15 PM" src="https://github.com/user-attachments/assets/a2abc743-2774-423a-9b45-cd10c4559e04" />
<img width="1600" height="1000" alt="WhatsApp Image 2026-05-26 at 11 09 22 PM" src="https://github.com/user-attachments/assets/5137358f-d060-4010-8ebd-1fcb4e024cb5" />

# RESULT
The High Pass FIR digital filter was successfully designed and its waveform was plotted using the Hamming window method in Scilab.
