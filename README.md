# LineFollwerRobot
Line Follwer Robot Code

/*------ Arduino Line Follower Code----- */
/*-------definning Inputs------*/
#define LS 2     // left sensor
#define RS 3      // right sensor

/*-------definning Outputs------*/
#define LM1 11       // in1 left motor
#define LM2 10       // in2 left motor
#define RM1 9       // in3 right motor
#define RM2 8      // in4 right motor
int enA = 5;        // enable A for the Motor A
int enB = 6;        // enable B for the Motor B
void setup()
{
  pinMode(LS, INPUT);
  pinMode(RS, INPUT);
  pinMode(LM1, OUTPUT);
  pinMode(LM2, OUTPUT);
  pinMode(RM1, OUTPUT);
  pinMode(RM2, OUTPUT);
  pinMode(enA, OUTPUT);
  pinMode(enB, OUTPUT);
  Serial.begin(9600);
}

void loop()
{

  if (digitalRead(LS) && digitalRead(RS))    //  Stop
  {
    digitalWrite(LM1, LOW);
    digitalWrite(LM2, LOW);
    digitalWrite(RM1, LOW);
    digitalWrite(RM2, LOW);
    Serial.println("STOP");
  }

  if (!(digitalRead(LS)) && digitalRead(RS))    // Turn Right
  {
    analogWrite(enA, 100);
    analogWrite(enB, 100);
    digitalWrite(LM1, HIGH);
    digitalWrite(LM2, LOW);
    digitalWrite(RM1, LOW);
    digitalWrite(RM2, LOW);
    Serial.println("R");
  }

  if (digitalRead(LS) && !(digitalRead(RS)))    // turn left
  {
    analogWrite(enA, 90);
    analogWrite(enB, 90);
    digitalWrite(LM1, LOW);
    digitalWrite(LM2, LOW);
    digitalWrite(RM1, HIGH);
    digitalWrite(RM2, LOW);
    Serial.println("L");
  }

  if (!(digitalRead(LS)) && !(digitalRead(RS)))    // forward
  {
    analogWrite(enA, 90);
    analogWrite(enB, 90);
    digitalWrite(LM1, HIGH);
    digitalWrite(LM2, LOW); 
    digitalWrite(RM1, HIGH);
    digitalWrite(RM2, LOW);
    Serial.println("FORWARD");
  }
}
