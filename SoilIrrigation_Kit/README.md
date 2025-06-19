💧 Soil Irrigation System Kit

🔌 Circuit Diagram
Arduino Uno Connections:
───────────────────────────────────────────────
Soil Moisture Sensor   → Arduino Uno
├── VCC                → 5V
├── GND                → GND
└── AOUT               → A0 (Analog Input)

Relay Module           → Arduino Uno
├── VCC                → 5V
├── GND                → GND
└── IN (Signal)        → Digital Pin 3

Water Pump Circuit:
├── Pump (+)           → NO (Normally Open) on Relay
├── Pump (-)           → Battery (-)
└── Battery (+)        → COM on Relay

 📟 Code
#define sensorPin A0    // Soil moisture sensor
#define relayPin 3      // Relay control

// Calibration (adjust based on sensor tests)
const int DRY_THRESHOLD = 400;  // Above = dry soil

void setup() {
  pinMode(sensorPin, INPUT);
  pinMode(relayPin, OUTPUT);
  digitalWrite(relayPin, HIGH);  // Start with pump OFF
  Serial.begin(9600);
}

void loop() {
  int moistureValue = analogRead(sensorPin);
  Serial.print("Moisture: ");
  Serial.print(moistureValue);

  if (moistureValue > DRY_THRESHOLD) {
    digitalWrite(relayPin, LOW);   // Activate relay → pump ON
    Serial.println(" | Pump: ON");
  } else {
    digitalWrite(relayPin, HIGH);  // Deactivate relay → pump OFF
    Serial.println(" | Pump: OFF");
  }
  delay(2000);  // Check every 2 seconds
}



 🌱 Description
This system automatically waters plants based on soil moisture level using a sensor and relay module.

 🧠 Concepts Covered:
- Soil Moisture Sensor
- Relay module for controlling pump
- Analog readings in Arduino
