# Image-Processing
This repository contains various scripts and tools for image processing tasks.

[https://github.com/MarwanIdrees/Image-Processing/blob/main/Fourier-transform-Exp1.m](https://github.com/MarwanIdrees/Image-Processing/blob/main/Fourier-transform-Exp1.m)
**This MATLAB code processes an image through frequency domain filtering using the Fourier transform:**
```clear all
close all
clc
MyImage = imread("https://i.stack.imgur.com/oIumJ.png");
subplot(2,2,1),imshow(MyImage),title("Orginal Image")
F=fft2(MyImage);
% The zero-frequency coefficient can be displayed in the center, useing the %function fftshift.
FS=fftshift(F);
% To increase the visual detaiels, the log function can be used
I=log(1 + abs(FS));
subplot(2,2,2),imshow(I,[]),title('Image Spectrum Of Orginal Image');
%----
FS(96:106,115:125)=0;
FS(216:226,115:125)=0;
FS(274:284,115:125)=0;
FS(298:308,115:125)=0;
FS(12:22,115:125)=0;
FS(37:47,115:125)=0;
% convert the image back to spatial domain
new = real(ifft2(ifftshift(FS)));
subplot(2,2,3),imshow(new,[]),title('Filtered image spectrum');
im=log(1 + abs(FS));
subplot(2,2,4),imshow(im,[]),title('Image Spectrum Of Filtered Image');```


