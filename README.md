# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 

 clc;  
clear; 
x = [1 1 2 1]; 
 
h = [1 2 3 4]; 
 
m = length(x);
n = length(h);
a=0:1:m-1; 
b=0:1:n-1; 
 
subplot(3,1,1);  
plot2d3(a,x); 
xlabel('Time');
ylabel('Amplitude'); 
title('Graphical Representation of Input Signal X');

subplot(3,1,2); 
plot2d3(b,h);  
xlabel('Time'); 
ylabel('Amplitude');  
title('Graphical Representation of Impulse Signal h');
for i = 1: n+m-1 
conv_sum = 0; 
 
for j = 1:i 
 
if (((i-j+1) <= n)&(j <=m)) 
 
conv_sum = conv_sum + x(j)*h(i-j+1); 
 
end; 
 
y(i) = conv_sum; 
 
end;
 
end; 
disp(y,'Convolution Sum using Direct Formula Method = ')
subplot(3,1,3); 
plot2d3(y)  
title('Graphical Representation of output Signal y'); 



## PROGRAM (Circular Convolution): 

clc;
clear;

// Input sequences
x = [1 2 2 1];
h = [1 2 3 1];

// Length for circular convolution (take max length)
N = max(length(x), length(h));

// Zero padding if needed
x = [x, zeros(1, N-length(x))];
h = [h, zeros(1, N-length(h))];

disp("Zero-padded input:");
disp(x);
disp("Zero-padded impulse:");
disp(h);

// ---- Circular convolution using modulo ----
y = zeros(1, N);

for n = 1:N
    for k = 1:N
        j = pmodulo(n-k, N) + 1;   // pmodulo avoids negative indices
        y(n) = y(n) + x(k) * h(j);
    end
end

disp("Circular convolution result:");
disp(y);

// ---- Plot results ----
subplot(3,1,1);
plot2d3(0:N-1, x);
title("Input sequence x[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,2);
plot2d3(0:N-1, h);
title("Impulse response h[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,3);
plot2d3(0:N-1, y);
title("Circular Convolution y[n]");
xlabel("n"); ylabel("Amplitude");


## OUTPUT (Linear Convolution): 
<img width="898" height="701" alt="Screenshot 2025-09-08 161943" src="https://github.com/user-attachments/assets/2a92b570-fa1d-439d-b48e-6f66f49e6e68" />

<img width="647" height="327" alt="Screenshot 2025-09-08 161931" src="https://github.com/user-attachments/assets/b6f68a0d-1d30-460b-aac2-d2d2db79ccf7" />


## OUTPUT (Circular Convolution): 

<img width="475" height="408" alt="Screenshot 2025-09-08 162407" src="https://github.com/user-attachments/assets/a4f8e959-eb9a-4b38-b786-f01bb98d1add" />
<img width="1081" height="764" alt="Screenshot 2025-09-08 162426" src="https://github.com/user-attachments/assets/24b8d0f6-86f1-4212-a4e0-ce89b3dd5a6c" />


## RESULT: 
thus the linear and circular convulation are verified
