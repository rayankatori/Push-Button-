# Push-Button Project 🔘

A simple and beginner-friendly project to demonstrate how to use a **push button** with an Arduino (or any microcontroller). The button can be used to control LEDs, trigger events, or act as a basic user interface input.

---

## 🎯 Project Objectives

- Detect and respond to button presses
- Eliminate false triggers using software debounce
- Control external outputs (e.g., LED) based on button state
- Serve as a foundation for more advanced interaction (e.g., long press, toggle, multi-button input)

---

## 🧰 Components Required

- Arduino Uno / Nano / ESP32 (or compatible board)
- Push button (normally open)
- 10kΩ resistor (optional if not using internal pull-up)
- Breadboard and jumper wires
- (Optional) LED and 220Ω resistor for output testing

---

## 🔌 Circuit Wiring

| Component     | Arduino Pin   |
|---------------|----------------|
| One leg of button | GND         |
| Other leg of button | D2 (digital input with internal pull-up) |

If using the internal pull-up resistor, configure the pin as:

```cpp
pinMode(buttonPin, INPUT_PULLUP);
This means the button reads HIGH when not pressed, and LOW when pressed.

💻 Example Arduino Code
cpp
Copy
Edit
const int buttonPin = 2;
const int ledPin = 13;

bool lastButtonState = HIGH;
bool ledState = LOW;

void setup() {
  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  bool currentButtonState = digitalRead(buttonPin);

  if (currentButtonState == LOW && lastButtonState == HIGH) {
    ledState = !ledState; // Toggle LED
    digitalWrite(ledPin, ledState);
    delay(200); // Debounce delay
  }

  lastButtonState = currentButtonState;
}
🚀 How to Use
Connect the button and LED as shown in the wiring section.

Upload the code to your Arduino using the Arduino IDE.

Open the Serial Monitor (optional) to view debug messages.

Press the button to toggle the LED on and off.

📁 Project Structure
css
Copy
Edit
Push-Button/
├── Push-Button.ino       # Main Arduino sketch
├── README.md             # Project documentation
└── docs/
    └── wiring_diagram.png (optional)
🧠 Future Enhancements
Add long press and double click detection

Use interrupts instead of polling

Add multiple buttons for advanced control

Integrate with LCD or OLED display

