// Define the GPIO pins for the LEDs
const int ledPin1 = 32;  // GPIO pin for LED 1
const int ledPin2 = 26;  // GPIO pin for LED 2


// Define the GPIO pins for the sliding switches
const int switchPin1 = 21;  // GPIO pin for sliding switch 1 ac input
const int switchPin2 = 4;  // GPIO pin for sliding switch 2  dc input

void setup() {
  // Initialize the serial monitor
  Serial.begin(115200);

  // Set up the switch pins as input with internal pull-up resistors
  pinMode(switchPin1, INPUT_PULLUP); // Using internal pull-up resistor for switch 1
  pinMode(switchPin2, INPUT_PULLUP); // Using internal pull-up resistor for switch 2
  
  // Set up the LED pins as outputs
  pinMode(ledPin1, OUTPUT);
  pinMode(ledPin2, OUTPUT);
  

  // Initially, ensure all LEDs are off
  digitalWrite(ledPin1, LOW);
  digitalWrite(ledPin2, LOW);
  
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
     digitalWrite(ledPin1, HIGH);  // LED 1 on
  delay(200);                  // Wait for 1 second (1000 milliseconds)

  // Turn off all LEDs
  digitalWrite(ledPin1, LOW);   // LED 1 off
  delay(200);                  // Wait for 1 second (1000 milliseconds)
  } else {
    digitalWrite(ledPin1, LOW);   // Turn LED 1 
  }

  // Control LEDs based on the second switch (switchPin2)
  if (switchState2 == LOW) {  // If the second switch is in the "on" position (LOW)
    digitalWrite(ledPin2, HIGH);  // LED 1 on
  delay(300);                  // Wait for 1 second (1000 milliseconds)

  // Turn off all LEDs
  digitalWrite(ledPin2, LOW);   // LED 1 off
  delay(300);                  // Wait for 1 second (1000 milliseconds)
  } else {
    digitalWrite(ledPin2, LOW);   // Turn LED 2 off
  }

  delay(100);  // Small delay to debounce the switches
}
