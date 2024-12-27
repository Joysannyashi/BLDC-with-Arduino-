#include <Servo.h>

Servo esc;  // Create a Servo object to control the ESC

int escPin = 9;  // PWM pin connected to ESC signal wire
int throttle = 0;  // Throttle value (0-180)

void setup() {
  esc.attach(escPin);  // Attach the ESC to the defined pin
  esc.write(0);  // Initialize ESC with zero throttle
  delay(1000);  // Give ESC some time to initialize (arm process)
}

void loop() {
  for (throttle = 0; throttle <= 180; throttle += 1) {  // Increase throttle
    esc.write(throttle);  // Send throttle signal to ESC
    delay(20);  // Short delay to allow smooth speed increase
  }

  delay(2000);  // Hold maximum speed for 2 seconds

  for (throttle = 180; throttle >= 0; throttle -= 1) {  // Decrease throttle
    esc.write(throttle);  // Send throttle signal to ESC
    delay(20);  // Short delay to allow smooth speed decrease
  }

  delay(2000);  // Hold motor off for 2 seconds
}
