# servo-motor-1
the Control the position of a servo motor with your Arduino and a potentiometer.

 # Hardware Required:
Arduino Board

Servo Motor

hook-up wires

Breadboard

potentiometers
# Circuit:
Servo motors have three wires: power, ground, and signal. The power wire is typically red, and should be connected to the 5V pin on the Arduino board. The ground wire is typically black or brown and should be connected to a ground pin on the board. The signal pin is typically yellow, orange or white and should be connected to pin 3 or 5 or 6 or 9 or 10 or 10 or 11 on the board.

Servo motor can be directly connected to Arduino. We connected the motor to the Arduino as shown in:
https://www.tinkercad.com/things/bgLSZtYmaKA-copy-of-copy-of-copy-of-brilliant-albar-rottis/editel?sharecode=WMnaKS9zPQAusDD6nuWfSXCqXOD7nk01oz3IhpWUCEk
![Copy of Copy of Copy of Brilliant Albar-Rottis](https://user-images.githubusercontent.com/86836634/124377849-e2abca80-dcb6-11eb-9402-17184aea7631.png)
كما هو موضح قمنا بتوصيل السيرفو موتور في الأردوينوأونو وأستخدمنا الكود التالي لتحريك السيرفو موتور مقدار 90 درجة ثم تعود لنقطة البداية

 # code:
 #include <Servo.h>
 Servo myservo1;// create servo object to control a servo
// twelve servo objects can be created on most boards

 Servo myservo2;// create servo object to control a servo
// twelve servo objects can be created on most boards

 Servo myservo3;// create servo object to control a servo
// twelve servo objects can be created on most boards

 Servo myservo4;// create servo object to control a servo
// twelve servo objects can be created on most boards

 Servo myservo5;// create servo object to control a servo
// twelve servo objects can be created on most boards

 Servo myservo6; // create servo object to control a servo // twelve servo objects can be created on most boards
 int pos = 0; // variable to store the servo position
 
 void setup() {
 
 myservo1.attach(3);attaches the servo on pin 3 to the servo object
 
 myservo2.attach(5);attaches the servo on pin 5 to the servo object
 
 myservo3.attach(6); attaches the servo on pin 6 to the servo object
 
 myservo4.attach(9);attaches the servo on pin 9 to the servo object
 
 myservo5.attach(10);attaches the servo on pin 10 to the servo object
 
 myservo6.attach(11); // attaches the servo on pin 11 to the servo object }
 
 void loop() {
 for (pos = 0; pos <= 90; pos += 1) { // goes from 0 degrees to 90 degrees // in steps of 1 degree

myservo1.write(pos);tell servo to go to position in variable 'pos'

myservo2.write(pos);tell servo to go to position in variable 'pos'

myservo3.write(pos);tell servo to go to position in variable 'pos'

myservo4.write(pos);tell servo to go to position in variable 'pos'

myservo5.write(pos);tell servo to go to position in variable 'pos'

myservo6.write(pos); // tell servo to go to position in variable 'pos'

delay(15);

}

for (pos = 90; pos >= 0; pos -= 1) { // goes from 180 degrees to 0 degrees

myservo1.write(pos);tell servo to go to position in variable 'pos'

myservo2.write(pos);tell servo to go to position in variable 'pos'

myservo3.write(pos);tell servo to go to position in variable 'pos'

myservo4.write(pos);tell servo to go to position in variable 'pos'

myservo5.write(pos);tell servo to go to position in variable 'pos'

myservo6.write(pos); // tell servo to go to position in variable 'pos'

delay(15); // waits 15ms for the servo to reach the position

}

}

In this piece of the project, we will set up software that reads the voltage output of the potentiometer. It then converts that number it into an angle for the servo.

 # Potentiometer:
we might want to control the angle a servo rotates without having to constantly modify the code. One way to do this is to use a potentiometer. Think of a potentiometer as a variable resistor. By turning the knob, you can control the voltage output of the potentiometer.

حيث باستخدام مجزئ الجهد (المقاومة المتغيرة ) وتدويرها ستدور محركات السيرفو فى نفس اتجاه دوران المقاومة المتغيرة وعند عكس حركة الدوران للمقاومة المتغيرة ستنعكس حركة دوران محرك السيرفو وسترى الحركة وكأن المحرك فى يدك تماماً

 # A potentiometer has 3 terminals:
 Two outer terminals are used for power: one outer pin connects to ground and the other connects to positive voltage. Potentiometers don’t have polarity, so it doesn’t matter which one is ground and which one is connected to positive voltage. A central control terminal is used for voltage output: turning the knob of the potentiometer increases or decreases the resistance, which lowers or increases the voltage output.
 https://www.tinkercad.com/things/gYgflkD4lys-copy-of-copy-of-copy-of-brilliant-albar-rottis/editel?sharecode=U66Vf4FkhDYuq_kFZSUBBS9IWFNHbC3AipGURElTUhM
 
![Copy of Copy of Brilliant Albar-Rottis](https://user-images.githubusercontent.com/86836634/124377888-1981e080-dcb7-11eb-8b99-84cd42a2567e.png)
# code:
#include <Servo.h>

Servo myservo1; // create servo object to control a servo Servo myservo2; Servo myservo3; Servo myservo4; Servo myservo5;

int pot1 = A0;

int pot2 = A1;

int pot3 = A2;

int pot4 = A3;

int pot5 = A4; // analog pin used to connect the potentiometer

int valPot1; // variable to read the value from the analog pin

int valPot2;

int valPot3;

int valPot4;

int valPot5;

void setup() {

myservo1.attach(3);

myservo2.attach(5);

myservo3.attach(6);

myservo4.attach(9); // attaches the servo on pin 9 to the servo object

myservo2.attach(5);

myservo5.attach(10);

}

void loop() {

valPot1 = analogRead(pot1); // reads the value of the potentiometer (value between 0 and 1023)

valPot1 = map(valPot1, 0, 1023, 0, 180); // scale it to use it with the servo (value between 0 and 180)

myservo1.write(valPot1); // sets the servo position according to the scaled value

delay(15); // waits for the servo to get there

valPot2 = analogRead(pot2);
valPot2 = map(valPot2, 0, 1023, 0, 180);
myservo2.write(valPot2);
delay(15);

valPot3 = analogRead(pot3);
valPot3 = map(valPot3, 0, 1023, 0, 180);
myservo3.write(valPot3);
delay(15);

valPot4 = analogRead(pot4);
valPot4 = map(valPot4, 0, 1023, 0, 180);
myservo4.write(valPot4);
delay(15);

valPot5 = analogRead(pot5);
valPot5 = map(valPot5, 0, 1023, 0, 180);
myservo5.write(valPot5);
delay(15);

}

In the end it has become easier to control the position of the servo motor using the Arduino and potentiometer.
