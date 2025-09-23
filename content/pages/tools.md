---
content_type: page
description: This section provides a MATLAB script that serves as an example for playing
  with a sound signal.
learning_resource_types:
- Tools
ocw_type: CourseSection
title: Tools
uid: e02af7ed-2931-202c-204c-c44a69dba8ad
---

This is a MATLAB{{< sup "®" >}} script that serves as an example for playing with a sound signal.

\[y,Fs\] = audioread('Thunderstruck.m4a'); % Change it to any audio file in your directory

%% Play it normally  
t0=audioplayer(y,Fs);  
% creates an audioplayer object for signal Y, using sample rate Fs  
play(t0);  
%% Stop it  
stop(t0);  
%% Fs/2  
t1=audioplayer(y,Fs/2); play(t1);  
%% Stop it  
stop(t1);  
%% Fs\*2  
t2=audioplayer(y,Fs\*2); play(t2);  
%% Stop it  
stop(t2);  
%% Fs\*20  
t3=audioplayer(y,Fs\*20); play(t3);  
%% Fs/4  
t4=audioplayer(y,Fs/4); play(t4);  
%%  
stop(t4);

%% Break the song into it's different frequency components  
clc; close all;  
stop L=length(y(:,1));  
stop NFFT = 2\*L; % Next power of 2 from length of y  
stop FWS = fft(y,NFFT)\*(2/L);  
stop FWS = FWS .\* conj(FWS);  
stopdB\_FWS = 10\*log10(FWS);  
%

figure(1)  
stop plot((1:L/2)/L,dB\_FWS(2:(L/2+1))); set(gca, 'FontSize', 18);  
stop xlabel('Frequency cycles/sample time'); axis tight; grid on;  
stopylabel('dB 10\*log10(y\_j)'); title('Power spectrum for AC/D Thunderstruck')  
print -dpng Thunderstruck\_Power\_Spectra.png