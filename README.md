# Parking-system-using-IOT
Using a hardware as ultrasonic sensor and make a easy to identify the slot space 

#include<LiquidCrystal.h>
LiquidCrystal lcd (0,1,2,3,4,5);
int trigpin=9;
int echopin=10;
void setup()
{
  lcd.begin(16,2);
  
  pinMode(trigpin,OUTPUT);
  pinMode(echopin,INPUT);
   pinMode(8,OUTPUT);
   pinMode(11,OUTPUT);
    digitalWrite(13,HIGH);
    tone(5,900); 
}
void loop()
{
  
 
  int t,d;
  digitalWrite(trigpin,HIGH);          
  delayMicroseconds(100);
  digitalWrite(trigpin,LOW);                           // those all the lines are used to work the ultrasonic sensor
  t=pulseIn(echopin,HIGH);                 
    d=t*0.034/2;


  delay(1000);

if (d<=20)// if the value detect signal to the led
{
 
digitalWrite(8,HIGH);
lcd.setCursor(1,0);
  lcd.print("ALERT");
 


}
if(d<20)
{
digitalWrite(11,LOW);
delay(1000);
lcd.clear();
  
}
else
{
  lcd.setCursor(1,1);
  lcd.print("safe you can Go");
  digitalWrite(8,LOW);
  digitalWrite(11,HIGH);
  delay(1000);

}
{

}

}
