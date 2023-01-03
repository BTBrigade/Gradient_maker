# Gradient_maker

The purpose of this machine is to form linear gradients for ultracentrifugation. Our lab primarily uses sucrose solutions, so the parts here are sufficient for our use case. If you are forming another type of gradient, it may be wise to consult the driver and motor datasheets to confirm that these components will work for your application. As always, you can find the parts listed cheaper, but this was a project I wanted to complete quickly, so I used parts from proven manufacturers. You will need access to a 3D printer and basic power tools to complete this project. Additionally, you will need to find an enclosure to protect the electronics and provide a stable base for the stepper motor arm that turns the gradients.

Parts list

Arduino Uno REV3 (1): https://store.arduino.cc/usa/arduino-uno-rev3 

9V 2A power supply (1):
https://www.amazon.com/gp/product/B06Y1LF8T5/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1

Stepper motor driver (1) Adafruit:
https://www.amazon.com/gp/product/B00JI99DX4/ref=ppx_yo_dt_b_asin_title_o01_s00?ie=UTF8&psc=1 

Stepper motor (2): https://www.sparkfun.com/products/9238

12V 2A power supply (2):
https://www.amazon.com/gp/product/B077PW5JC3/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1

20x4 I2C LCD (1):
https://www.amazon.com/gp/product/B01GPUMP9C/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1

22 AWG solid core wire:
https://www.amazon.com/gp/product/B07TX6BX47/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1

5mm coupler (4):
https://www.amazon.com/gp/product/B081KRJBVV/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1

Push buttons (10):
https://www.amazon.com/gp/product/B07RV1D98T/ref=ppx_yo_dt_b_asin_title_o03_s00?ie=UTF8&psc=1

Neodynium magnets (100):
https://www.amazon.com/gp/product/B07MV6M12H/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1

M3 button head hex drive screws: https://www.mcmaster.com/bolts/rounded-head-screws/hex-drive-rounded- head-screws/
The length needed will depend on the enclosure width.

M2.5 x 0.45 10mm long hex drive flat head screws (25): https://www.mcmaster.com/92125A088/

Proto Pasta Black PRO Series PLA Filament - 1.75mm: https://www.matterhackers.com/store/l/pro-series-
pla/sk/MY6C8H7E

Faucet and Valve packing (1): https://www.acehardware.com/departments/plumbing/faucet-and-faucet- repair/faucet-and-valve-packing/40215
This is for softening the surface between the rack and carousel — also provides a touch of adhesion.
                 
3D printed parts list
All parts listed below were designed in Solidworks, sliced in Cura (0.2mm layer height, 215 °C hot end, 60°C bed, 50mm/s), and printed with a Creality Ender 3 using Proto Pasta filament (highly recommend). A friendly reminder: tolerances for 3D printed parts vary quite a bit. The printer, ambient temperature, and filament all play a big role in layer height, print uniformity, and part dimensions. This variability is more noticeable in smaller printed parts — think about an error of +/- 5% at 2mm vs 200mm. Because this is the case, I have included the Solidworks SLDPRT files, which should be editable even in the most basic edition, should you need to make changes. Some parts will need to be made to suit your particular enclosure, so I have not included them in this list. If you find an identical power supply from Bio-Rad and are bored enough to embark on this journey, email me and I’ll send you the files.

- Arduino basket.STL
Secures Arduino to flat surface in enclosure

- Button Plate_V5.STL
Serves as mount for buttons

- Rate Zonal Cap_V3.STL
Displaces 200μl of liquid at the top of the gradient and allows them to be tilted without losing volume

- LCD Cutting Template.STL
Allows for mocking up display to faceplate of enclosure to set/score drill points

- Support Arm.STL
Has dowel holes cut for fastening coupler from stepper #1 and for mounting stepper #2

- Motor Mount Spacer.STL
The Nema 17 stepper motors have a cylinder extruded ~2mm. This spacer allows even distribution of
load on all four machine screws to the stepper.

- Motor Drill Guide.STL
Allows for mocking up motor to the enclosure — facilliates setting/scoring drill points

- Motor wire guide_V2.STL
Protects stepper wires from abrasion during normal operation.

- Rack_bottom_V8.STL
Tapered bottom allows SW-41 tubes to sit flush. Also has 3 cylinders cut-extruded to house neodymium
magnets. Has countersunk screw holes so direct contact is made between rack bottom and carousel.

- Rack_top_V7.STL
Secures tubes in place with aid of supports. Has countersunk screw holes

- Support_V2.STL
Beefy supports to fasten rack top and bottom.

Hookup guides and Code
I focused on making this as plug and play as possible. The soldering is minimal, and the connections are listed in the .ino file. For your convenience, I have pasted them below. Despite this being straightforward, I would strongly encourage you to read the documentation and pull out the breadboard to mock everything up before soldering. I used a small prototyping board to solder VCC, GND, SDA, SCL, and resistors so I wouldn’t fuck up the motor shield.

Pin addresses
Arduino --> I2C LCD2004 GND --> GND
VCC --> 5V
SDA --> A4
SCL --> A5
Arduino --> Push button (wired with 10Kohm pulldown resitor to ground) D10 --> push 1
D11 --> push 2
D12 --> push 3
D13 --> push 4
Arduino --> Adafruit Motor Shield V2 -> Steppers
The shield is a shield, so it just plugs in to the Arduino. Shield M1 --> Yellow and Blue stepper 1
Shield M2 --> Green and Red stepper 1
Shield M3 --> Yellow and Blue stepper 2
Shield M4 --> Green and Red stepper 2
Note: wire orientation does not influence stepper behavior as long each coil is controlled independently.

References
Adafruit Motor Shield V2: https://learn.adafruit.com/adafruit-motor-shield-v2-for-arduino

Adafruit stepper motor library: https://github.com/adafruit/Adafruit_Motor_Shield_V2_Library

Sparkfun stepper motors: https://www.sparkfun.com/datasheets/Robotics/SM-42BYG011-25.pdf 

AccelStepper library: http://www.airspayce.com/mikem/arduino/AccelStepper/AccelStepper_8h_source.html 

LCD: http://wiki.sunfounder.cc/index.php?title=I2C_LCD2004

Buttons: https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button

The code I’m running is available as a separate folder and labeled “Final with delay.ino”. It is heavily commented, so should be pretty straightforward to amend and edit.
