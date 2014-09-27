task main()
{
 SetSensorType(IN_1,SENSOR_TYPE_LIGHT_ACTIVE); SetSensorMode(IN_1,SENSOR_MODE_PULSE);
 SetSensorType(IN_4,SENSOR_TYPE_TOUCH); SetSensorMode(IN_1,SENSOR_MODE_PULSE);
 int lineas;
 int a=1 ;
 int b=0 ;
 long t0 = CurrentTick();
 long t;
 

 while(a)
 {
  lineas = SENSOR_1;
  
  t  = CurrentTick()-t0;

  NumOut(60,LCD_LINE5,lineas);
  
  if(lineas==0)
  {
  OnFwd(OUT_BC,35);
  Wait(1092);
  Off(OUT_BC);
  Wait(100);
  NumOut(60,LCD_LINE5,lineas);
  }
  
  if(lineas==1)
  {
  b=1;
  NumOut(60,LCD_LINE5,lineas);
  if(t>5000)
  {
  t  = CurrentTick()-t0;
  a=0;
  }
  }
  
  if(lineas==2)
  {
  OnFwd(OUT_BC,35);
  Wait(600);
  Off(OUT_BC);
  Wait(100);
  NumOut(60,LCD_LINE5,lineas);
   if(lineas==2)
   {
   b=2;
   NumOut(60,LCD_LINE5,lineas);
   a=0;
   }
   }
   if(lineas==3)
   {

   b=3;
   a=0;
   }
   

}

a=1;

if(b==1)
{
OnFwd(OUT_BC,70);
Wait(800);
OnFwd(OUT_C,70);
OnRev(OUT_B,70);
Wait(500);
OnFwd(OUT_BC,70);
Wait(750);
OnFwd(OUT_B,70);
OnRev(OUT_C,70);
Wait(500);
}

if(b==2)
{
OnFwd(OUT_BC,70);
Wait(800);
OnFwd(OUT_B,70);
OnRev(OUT_C,70);
Wait(500);
OnFwd(OUT_BC,70);
Wait(800);
OnFwd(OUT_C,70);
OnRev(OUT_B,70);
Wait(500);
}

if(b==3)
{
OnFwd(OUT_BC,70);
Wait(500);
}

ClearSensor(IN_1);
ClearSensor(IN_2);
ClearSensor(IN_3);
ClearSensor(IN_4);

 SetSensorLight(IN_1);
 SetSensorLowspeed(IN_2);
 SetSensorTouch(IN_4);
 SetSensorTouch(IN_3);
 int blanco =70;
 int negro = 40;

 int media = ((blanco + negro)/2);

 while(1)
 {
  t  = CurrentTick()-t0;
  int medida = SENSOR_1;
  int offset = 4*(media -medida);
  NumOut(50,LCD_LINE2,t);
  OnFwd(OUT_B,11-offset);
  OnFwd(OUT_C,18+offset);



 }


}

  
  
