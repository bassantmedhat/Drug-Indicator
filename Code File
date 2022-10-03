// RGB first sensor
int red_light_pin= 11;
int green_light_pin = 10;
int blue_light_pin = 9;
//RGB second sensor
int red_light_pin1= 6;
int green_light_pin1 = 3;
int blue_light_pin1 = 5; 
// two buzz
int buzzer_1=13;
int buzzer_2=12;
   
// Sensor pins
#define sensorPower 7
#define sensorPin A5
// Value for storing water level1
int val = 0;

// Sensor pins
#define sensorPower1 8
#define sensorPin1 A4
// Value for storing water level2
int val1 = 0;

//lcd  definition code 
#include <LiquidCrystal.h> 
const int rs = 4 , en = 11, d4 = A0, d5 = A1, d6 = A2, d7 = A3;
LiquidCrystal lcd (rs , en , d4 , d5 , d6 , d7);


void setup() {
  // Set D7 && D8 as an OUTPUT
  pinMode(sensorPower, OUTPUT);
  pinMode(sensorPower1, OUTPUT);

  // Set to LOW so no power flows through the sensor
  digitalWrite(sensorPower, LOW);
  digitalWrite(sensorPower1, LOW);
  
  Serial.begin(9600);
  
  pinMode(red_light_pin, OUTPUT);
  pinMode(green_light_pin, OUTPUT);
  pinMode(blue_light_pin, OUTPUT);

  pinMode(red_light_pin1, OUTPUT);
  pinMode(green_light_pin1, OUTPUT);
  pinMode(blue_light_pin1, OUTPUT);

  pinMode(buzzer_1, OUTPUT);
  pinMode(buzzer_2, OUTPUT);

  //lcd setup
  lcd.begin(16,2);
  lcd.print(" Drugs Application ");
  
  
}
void loop() {
 
  if(readSensor()<100){
    RGB_color(0, 255, 255); 
    lcd.setCursor(0,0);
    lcd.print("Water level:");
    lcd.print(readSensor());
    lcd.setCursor(1,0);
    lcd.print("   'low level' ");
    
    
  }
  else if (readSensor()<140&&readSensor()>100){
  RGB_color(255, 255, 0); 
   lcd.setCursor(0,0);
    lcd.print("Water level:");
    lcd.print(readSensor());
    lcd.setCursor(1,0);
    lcd.print("   'moderate level' ");
    
   }
  else{
     RGB_color(255, 0, 0);
    lcd.setCursor(0,0);
    lcd.print("Water level:");
    lcd.print(readSensor());
    lcd.setCursor(1,0);
    lcd.print("   'high level'  WARNING!! ");
 
     tone(buzzer_1, 1000); // Send 1KHz sound signal...
   // delay(1000);        // ...for 1 sec
     noTone(buzzer_1);     // Stop sound...
     delay(1000);        // ...for 1sec
 
  }
if(readSensor1()<300){
    RGB_color1(0, 255, 255); // Cyan
    lcd.setCursor(0,0);
    lcd.print("Water level:");
    lcd.setCursor(1,0);
    lcd.print(readSensor1());
    lcd.print("   'moderate level' ");
     
  } 
  else{
     RGB_color1(255, 0, 0);//red
    lcd.setCursor(0,0);
    lcd.print("Water level:");
    lcd.setCursor(1,0);
    lcd.print("   'high level'  WARNING!! ");
    
    tone(buzzer_2, 1000); // Send 1KHz sound signal...
    delay(1000);        // ...for 1 sec
     noTone(buzzer_2);     // Stop sound...
     delay(1000);      
     
      
     }
}
// function for making specific color in rgb for first sensor
void RGB_color(int red_light_value, int green_light_value, int blue_light_value)
 {
  analogWrite(red_light_pin, red_light_value);
  analogWrite(green_light_pin, green_light_value);
  analogWrite(blue_light_pin, blue_light_value);
}
// function for second sensor
void RGB_color1(int red_light_value1, int green_light_value1, int blue_light_value1)
 {
  analogWrite(red_light_pin1, red_light_value1);
  analogWrite(green_light_pin1, green_light_value1);
  analogWrite(blue_light_pin1, blue_light_value1);
}
// function to get reading of sensor
int readSensor() {
  digitalWrite(sensorPower, HIGH);  // Turn the sensor ON
  delay(10);              // wait 10 milliseconds
  val = analogRead(sensorPin);    // Read the analog value form sensor
  digitalWrite(sensorPower, LOW);   // Turn the sensor OFF
  return val;             // send current reading
}

int readSensor1() {
  digitalWrite(sensorPower1, HIGH);  // Turn the sensor ON
  delay(10);              // wait 10 milliseconds
  val1 = analogRead(sensorPin1);    // Read the analog value form sensor
  digitalWrite(sensorPower1, LOW);   // Turn the sensor OFF
  return val1;             // send current reading
}
