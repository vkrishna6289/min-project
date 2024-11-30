/ Define the GPIO pins for the LEDs
const int ledPin1 = 32;  // GPIO pin for LED 1
const int ledPin2 = 33;  // GPIO pin for LED 2
const int ledPin3 = 27;  // GPIO pin for LED 3
const int ledPin4 = 33;  // GPIO pin for LED 4
const int ledPin5 = 25;  // GPIO pin for LED 5
const int ledPin6 = 26;  // GPIO pin for LED 6

// Define the GPIO pins for the sliding switches
const int switchPin1 = 21;  // GPIO pin for sliding switch 1
const int switchPin2 = 4;  // GPIO pin for sliding switch 2

void setup() {
  // Initialize the serial monitor
  Serial.begin(115200);

  // Set up the switch pins as input with internal pull-up resistors
  pinMode(switchPin1, INPUT_PULLUP); // Using internal pull-up resistor for switch 1
  pinMode(switchPin2, INPUT_PULLUP); // Using internal pull-up resistor for switch 2
  
  // Set up the LED pins as outputs
  pinMode(ledPin1, OUTPUT);
  pinMode(ledPin2, OUTPUT);
  pinMode(ledPin3, OUTPUT);
  pinMode(ledPin4, OUTPUT);
  pinMode(ledPin5, OUTPUT);
  pinMode(ledPin6, OUTPUT);

  // Initially, ensure all LEDs are off
  digitalWrite(ledPin1, LOW);
  digitalWrite(ledPin2, LOW);
  digitalWrite(ledPin3, LOW);
  digitalWrite(ledPin4, LOW);
  digitalWrite(ledPin5, LOW);
  digitalWrite(ledPin6, LOW);
}

void loop() {
  // Read the states of the sliding switches
  int switchState1 = digitalRead(switchPin1);
  int switchState2 = digitalRead(switchPin2);

  // Print the switch states for debugging (optional)
  Serial.print("Switch 1 state: ");
  Serial.print(switchState1);
  Serial.print(" | Switch 2 state: ");
  Serial.println(switchState2);

  // Control LEDs based on the first switch (switchPin1)
  if (switchState1 == LOW) {  // If the first switch is in the "on" position (LOW)
    digitalWrite(ledPin1, HIGH);  // Turn LED 1 on
    digitalWrite(ledPin2, HIGH);  // Turn LED 2 on
    digitalWrite(ledPin3, HIGH);  // Turn LED 3 on
  } else {
    digitalWrite(ledPin1, LOW);   // Turn LED 1 off
    digitalWrite(ledPin2, LOW);   // Turn LED 2 off
    digitalWrite(ledPin3, LOW);   // Turn LED 3 off
  }

  // Control LEDs based on the second switch (switchPin2)
  if (switchState2 == LOW) {  // If the second switch is in the "on" position (LOW)
    digitalWrite(ledPin4, HIGH);  // Turn LED 4 on
    digitalWrite(ledPin5, HIGH);  // Turn LED 5 on
    digitalWrite(ledPin6, HIGH);  // Turn LED 6 on
  } else {
    digitalWrite(ledPin4, LOW);   // Turn LED 4 off
    digitalWrite(ledPin5, LOW);   // Turn LED 5 off
    digitalWrite(ledPin6, LOW);   // Turn LED 6 off
  }

  delay(100);  // Small delay to debounce the switches
}
