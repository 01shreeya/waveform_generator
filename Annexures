# waveform_generator
#include<reg52.h>
#include<delay.h>
#include<lcd.h>

void blink();
//void delay(unsigned int z);
sbit LED = P1^0;
#define on 1
#define off 0
sbit ip = P3^3;

unsigned int pulses=0,freq;
bit t=0;
void main()
{	P1=0xFE;  //LED
P2=0x00; //LCD
P3=0xff; //INTR
P0=0xFF; //not used

TMOD=0x01;
TH0=0xEE;
TL0=0xFF;
IE=0x82;

LCD_Init();
LCD_Clear();
LCD_DisplayString("FREQ:       Hz");
blink();
TR0=0;

while(1)
{
if(!ip)
{
pulses++;
while(!ip);
}
}
}

void delay() interrupt 1
{	unsigned char c;
TR0=1;
c++;
freq=pulses*40;
if(c==30)
{
LCD_GoToXY(0,6);
LCD_DisplayNumber(freq);
c=0;
}
TH0=0x8B;
TL0=0xEE;
pulses=0;
TF0=1;
TR0=0;
}

void blink()
{	LED=on;
delay_ms(500);
LED=off;
}
