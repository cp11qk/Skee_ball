
/* 
[2434140]
DIGF_2B03
Skee-Ball
10/2/14
*/
//-----------[Variable]----------
//
//-----[Conditional pins]-----
int hole1 = 2; 
int hole2 = 3;
int hole3 = 4;
//
int holeState1 = 0;
int holeState2 = 0;
int holeState3 = 0;
//-----[Green Win LED]-----
int winPin =  13; 
//-----[LED output pins]-----
int led1 = 5;
int led2 =6;
int led3 = 7;

void setup()
{
//Set pin modes
  pinMode(winPin, OUTPUT);
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
  pinMode(hole3, INPUT);
  pinMode(hole2, INPUT);
  pinMode(hole1, INPUT);
}
//
void loop()
{
  //Setting pin numbers
  holeState1 = digitalRead(hole1);
  holeState2 = digitalRead(hole2);
  holeState3 = digitalRead(hole3);
  //
                                 // checks ifeach hole are landed in
  if(holeState1 == HIGH) {      
    digitalWrite(led1, HIGH);   // sets the LED on
    delay(1000);                // delays one second
    digitalWrite(led1, LOW);    // turns LED off
  }
  else if(holeState2 == HIGH) {      
    digitalWrite(led2, HIGH);   // sets the LED on
    delay(1000);
    digitalWrite(led2, LOW);
  }
  else if(holeState3 == HIGH) {      
    digitalWrite(led3, HIGH);   // sets the LED on
    delay(1000);
    digitalWrite(led3, LOW);
  }
  else{
    digitalWrite(led1, LOW); 
    digitalWrite(led2, LOW); 
    digitalWrite(led3, LOW);
  }
  //
  // checks if all of the holes have been landed in
  if ((holeState1 == HIGH) && (holeState1 == HIGH) && (holeState1 == HIGH)){
   // flash green win LED 3 times
    digitalWrite(winPin, HIGH);
    delay(500); // delay half a second
    digitalWrite(winPin, LOW);    
    delay(500);
    digitalWrite(winPin, HIGH); 
    delay(500);
    digitalWrite(winPin, LOW); 
    delay(500);
    digitalWrite(winPin, HIGH); 
    delay(500);
    digitalWrite(winPin, LOW); 
    //
    // turns LEDs back off
    digitalWrite(led1, LOW); 
    digitalWrite(led2, LOW); 
    digitalWrite(led3, LOW);
  }
  else{
    digitalWrite(winPin, LOW); 
  }
}


