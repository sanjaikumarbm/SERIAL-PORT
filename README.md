# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character
```

ORG 00H 
MOV TMOD, #20H 
MOV TH1, #0FDH 
MOV SCON, #50H 
SETB TR1 
MAIN_LOOP:
MOV SBUF, #'B' 
WAIT_TI:
JNB TI, WAIT_TI 
CLR TI 
END

FOR C CODE

#include<reg51.h>
void main(void)
{
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
while(1)
{
SBUF='A';
while(TI==0);
T1=0;
}
}

```



### (ii) Serial Port to Transfer a Message

```
ORG 00H
MOV TMOD,#20H
MOV TH1,#0FCH
MOV SCON,#40H
SETB TR1
MOV DPTR,#4500H
AGAIN:MOVX A,@DPTR
MOV SBUF,A
WAIT:JNB TI,WAIT
CLR TI
INC DPTR
SJMP AGAIN
END

Void main(void)
{
unsigned char msg[]="KAILAASH";
unsigned char i;
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
for(i-0;i<=12;i++)
{
SBUF=msg[i];
while(TI==0);
TI=0;
}
while(1);
}


```

### OUTPUT:
<img width="1919" height="1109" alt="Screenshot 2025-10-13 215337" src="https://github.com/user-attachments/assets/51b56e5e-6ee7-41c5-b056-15eb4440c073" />

<img width="1919" height="1199" alt="Screenshot 2025-10-13 215910" src="https://github.com/user-attachments/assets/04bf74c2-22c7-4151-8cb3-de655efe8e34" />
<img width="1919" height="1178" alt="image" src="https://github.com/user-attachments/assets/9984cfc2-3174-4859-a9a6-80b43b5c0a9c" />
<img width="1913" height="1078" alt="image" src="https://github.com/user-attachments/assets/3e2cde3d-4a4e-46b1-8292-8ba462fec6e6" />



### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
