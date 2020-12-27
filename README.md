/*this code depends on Arduino. And just for the searching fundemation.*/
#define in1 1
#define in2 2
#define in3 3
#define in4 4
#define ena1 6
#define ena2 5
void left_go()
{
     digitalWrite(in3,LOW);
     digitalWrite(in4,HIGH);
}

void right_back()
{
     digitalWrite(in1,LOW);
     digitalWrite(in2,HIGH);
}

void left_stop()
{
     digitalWrite(in3,HIGH);
     digitalWrite(in4,HIGH);
}

void right_stop()
{
     digitalWrite(in1,HIGH);
     digitalWrite(in2,HIGH);
}

void left_back()
{
     digitalWrite(in3,HIGH);
     digitalWrite(in4,LOW);
}

void right_go()
{
     digitalWrite(in1,HIGH);
     digitalWrite(in2,LOW);
}

void go_forward()
{    
      left_go();
      right_go();
}
void go_backward()
{    
      left_back();
      right_back();

}
void turn_left()
{
     left_back();
     right_go();
}
void turn_right()
{
     right_back();
     left_go();
}
void setup()
{
     pinMode(in1,OUTPUT);
     pinMode(in2,OUTPUT);
     pinMode(in3,OUTPUT);
     pinMode(in4,OUTPUT);
     pinMode(10,INPUT);
     pinMode(11,INPUT);
     pinMode(ena1,OUTPUT);
     pinMode(ena2,OUTPUT);
}
void loop()
{
    int p=digitalRead(10);
    int q=digitalRead(11);
    if ((q)&&(p))
       {
           turn_left();
           delay(10);
       }
    else
    if ((q)&&(!p)) 
       {
           turn_left();
           delay(10);
       }
    else
    if ((!q)&&(p)) 
       {
          turn_right();
          delay(10);
       }
    else
          go_forward();
}
