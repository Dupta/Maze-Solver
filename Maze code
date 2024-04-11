// Define motor pins
const int motor1Pin1 = 8;
const int motor1Pin2 = 9;
const int motor2Pin1 = 13;
const int motor2Pin2 = 12;
const int ena = 10;  // PWM pin for motor1 speed control
const int enb = 11;  // PWM pin for motor2 speed control

// Define ultrasonic sensor pins
const int trigPinFront = 4;
const int echoPinFront = 5;
const int trigPinLeft = 2;
const int echoPinLeft = 3;
const int trigPinRight = 6;
const int echoPinRight = 7;

void setup() {
  // Initialize serial communication
  Serial.begin(9600);

  // Set motor pins as output
  pinMode(motor1Pin1, OUTPUT);
  pinMode(motor1Pin2, OUTPUT);
  pinMode(motor2Pin1, OUTPUT);
  pinMode(motor2Pin2, OUTPUT);

// Set PWM pins as output
  pinMode(ena, OUTPUT);
  pinMode(enb, OUTPUT);

  // Initialize ultrasonic sensor pins
  pinMode(trigPinFront, OUTPUT);
  pinMode(echoPinFront, INPUT);
  pinMode(trigPinLeft, OUTPUT);
  pinMode(echoPinLeft, INPUT);
  pinMode(trigPinRight, OUTPUT);
  pinMode(echoPinRight, INPUT);
}

float getDistance(int trigPin, int echoPin) {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  float duration = pulseIn(echoPin, HIGH);
  float distance = duration * 0.034 / 2;  // Convert to cm
  return distance;
}

void moveForward() {
  analogWrite(ena, 50);
  analogWrite(enb, 50);
  digitalWrite(motor1Pin1, LOW);
  digitalWrite(motor1Pin2, HIGH);
  digitalWrite(motor2Pin1, LOW);
  digitalWrite(motor2Pin2, HIGH);
}

void turnLeft() {
  analogWrite(ena, 50);
  analogWrite(enb, 50);
  digitalWrite(motor1Pin1, HIGH);
  digitalWrite(motor1Pin2, LOW);
  digitalWrite(motor2Pin1, LOW);
  digitalWrite(motor2Pin2, HIGH);
}

void turnRight() {
  analogWrite(ena, 50);
  analogWrite(enb, 50);
  digitalWrite(motor1Pin1, LOW);
  digitalWrite(motor1Pin2, HIGH);
  digitalWrite(motor2Pin1, HIGH);
  digitalWrite(motor2Pin2, LOW);
}

// void stopMotors() {
//   digitalWrite(motor1Pin1, LOW);
//   digitalWrite(motor1Pin2, LOW);
//   digitalWrite(motor2Pin1, LOW);
//   digitalWrite(motor2Pin2, LOW);
//}

void stopMotors() {
  analogWrite(ena, 0);
  analogWrite(enb, 0);
}
void loop() {
  // Read distances from sensors
  float distanceFront = getDistance(trigPinFront, echoPinFront);
  float distanceLeft = getDistance(trigPinLeft, echoPinLeft);
  float distanceRight = getDistance(trigPinRight, echoPinRight);

  // Serial.print("Front: ");
  // Serial.print(distanceFront);
  // Serial.print(" | Left: ");
  // Serial.print(distanceLeft);
  // Serial.print(" | Right: ");
  // Serial.println(distanceRight);

  // Adjust these thresholds according to your maze and robot dimensions
  if (distanceFront > 13) {
    moveForward();
  } else {
    stopMotors();
    if (distanceLeft > distanceRight) {
      turnLeft();
    } else {
      turnRight();
    }
    delay(350); // Adjust this value to control turn duration
  }
}
