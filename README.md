# RainGuard: Rain Detection and Outdoor Clothes Protection

> WireWizards Hackathon 2026 | KGiSL Institute of Technology (KiTE)

RainGuard is a small Arduino-based system that notices rain the moment it starts and moves the clothes line under shelter, so nobody has to run outside when the sky suddenly turns dark.

---

## Team Details

| | |
|---|---|
| **Team Name** | CURRENT AFFAIRS |
| **Team ID** | EC013 |
| **Problem Statement No.** | ECW260045 |
| **Problem Statement** | Rain Detection and Outdoor Clothes Protection Alert |
| **Faculty Mentor** | Dr. Kamalakannan S |

**Team Members**

- Ragupathi V
- Navin Kumar S
- Vignesh R
- Yashvanth B

---

## The Problem

We have all come home to clothes that were dry in the morning and soaked by evening. Rain often starts without warning, and if no one is at home, the clothes get wet again.

## Our Solution

RainGuard watches the weather for you. A rain sensor placed near the drying area detects water drops, the Arduino reads the signal, and a servo motor swings the clothes line under cover. Once the rain stops and the sensor plate dries, the clothes are moved back out.

**What makes it different**

- Low cost and built from common, easy-to-find parts
- Works without internet
- Senses, decides and moves on its own, with no one needing to be present

---

## How It Works

```
Rain falls on the sensor plate
            |
            v
   Arduino reads the signal
            |
            v
Servo moves the clothes under shelter
            |
            v
 Rain stops and the plate dries
            |
            v
   Clothes are moved back out
```

---

## Hardware Used

| Component | Purpose |
|---|---|
| Arduino Uno | Main controller |
| Rain sensor module | Detects water drops |
| Servo motor | Moves the clothes line under shelter |
| Breadboard | Quick, solder-free connections |
| Jumper wires | Wiring between components |

## Software Used

- Arduino IDE (C/C++)

---

## Circuit Connections

Update this table to match your own wiring.

| Component | Pin | Arduino Pin |
|---|---|---|
| Rain sensor | VCC | 5V |
| Rain sensor | GND | GND |
| Rain sensor | DO (digital out) | D2 |
| Servo | Signal | D9 |
| Servo | VCC | 5V |
| Servo | GND | GND |

---

## Sample Code

This is a simple example sketch. Change the pin numbers and servo angles to match your setup.

```cpp
#include <Servo.h>

const int RAIN_PIN  = 2;   // digital output of the rain sensor
const int SERVO_PIN = 9;

const int SHELTER_ANGLE = 0;    // clothes line under cover
const int OUTSIDE_ANGLE = 90;   // clothes line outside

Servo clothesServo;

void setup() {
  pinMode(RAIN_PIN, INPUT);
  clothesServo.attach(SERVO_PIN);
  clothesServo.write(OUTSIDE_ANGLE);
  Serial.begin(9600);
}

void loop() {
  // Most rain sensor modules output LOW when water is detected
  bool raining = (digitalRead(RAIN_PIN) == LOW);

  if (raining) {
    clothesServo.write(SHELTER_ANGLE);
    Serial.println("Rain detected: moving clothes to shelter");
  } else {
    clothesServo.write(OUTSIDE_ANGLE);
    Serial.println("Dry: clothes outside");
  }

  delay(500);
}
```

---

## Getting Started

1. Connect the components as shown in the circuit table.
2. Open the Arduino IDE and load the sketch.
3. Select **Tools > Board > Arduino Uno** and the correct COM port.
4. Upload the sketch to the board.
5. Drop a little water on the sensor plate and watch the servo move the clothes line.

---

## Project Structure

```
RainGuard/
├── code/
│   └── rainguard.ino
├── images/
│   ├── prototype.jpg
│   └── team.jpg
├── docs/
│   └── CURRENT_AFFAIRS_ECW260045_Presentation.pdf
└── README.md
```

---

## Future Improvements

- Mobile alerts using a Wi-Fi module
- Buzzer or LED warning for nearby people
- Weather-forecast integration
- Full-size motorised clothes line for real balconies and terraces

---

## Acknowledgements

Thanks to our faculty mentor, **Dr. Kamalakannan S**, and to the **WireWizards Hackathon 2026** organisers at **KGiSL Institute of Technology**.

---

*Team CURRENT AFFAIRS | WireWizards Hackathon 2026*
