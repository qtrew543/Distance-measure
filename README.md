# Distance-measure

const int trigPin = 9;
const int echoPin = 10;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  Serial.begin(9600);
}

void loop() {
  long duration;
  float distance;

  digitalWrite(trigPin, LOW);
  delayMicroseconds(5);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(15);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  Serial.print("Echo Pin State: ");
  Serial.println(digitalRead(echoPin));

  if(duration == 0){
    Serial.println("No echo received");
  } else {
    distance = duration * 0.034 / 2;
    Serial.print("Duration: ");
    Serial.print(duration);
    Serial.print(", Distance: ");
    Serial.print(distance);
    Serial.println(" cm");
  }

  delay(500);
}
