# Ultrasonic-With-Buzzer
#define trigPin 5
#define echoPin 4
#define buzzerPin 6
long duration, distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzerPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = (duration/2) / 29.1;
  Serial.print(distance);
  Serial.println(" cm");

  if (distance < 50) {
    digitalWrite(buzzerPin, HIGH);
    delay(200);}
    else{
    digitalWrite(buzzerPin, LOW);
    delay(200);
  }
}
