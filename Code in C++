#include <Servo.h>

int Dist_tank1 = 0;

int Dist_tank2 = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Clear the trigger
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Sets the trigger pin to HIGH state for 10 microseconds
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // Reads the echo pin, and returns the sound wave travel time in microseconds
  return pulseIn(echoPin, HIGH);
}

Servo servo_3;

void setup()
{
  servo_3.attach(3, 500, 2500);
  Serial.begin(9600);
  pinMode(13, OUTPUT);

  Dist_tank1 = 0.01723 * readUltrasonicDistance(6, 6);
  Dist_tank2 = 0.01723 * readUltrasonicDistance(5, 5);
  if (Dist_tank2 > 50) {
    servo_3.write(75);
    delay(5000); // Wait for 5000 millisecond(s)
    servo_3.write(0);
  } else {
    Serial.println("Safe water level in tank 2");
  }
  if (Dist_tank1 > 50) {
    tone(13, 548668578, 3000); // play tone 300 (C25 = 548668578 Hz)
  } else {
    Serial.println("Safe water level");
  }
}

void loop()
{
  delay(10); // Delay a little bit to improve simulation performance
}
