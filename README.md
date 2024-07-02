**Name:** NIKITA GUDE                                                                                                                                                          
**Company:** CODETECH IT SOLUTIONS                                                                                                                                                  
**ID:** CT4ES2571                                                                                                                                                               
**Domain:** EMBEDDED SYSTEMS                                                                                                                                                  
 **Duration:** JUNE 20th,2024 to JULY 20th, 2024                                                                                                                                 
 **Mentor:** MUHAMMED MUZAMMIL AHMED


## OVERVIEW OF THE PROJECT
### Temperature and Humidity Monitoring with DHT11 Sensor and Arduino
### 1. Introduction
The purpose of this project is to design and implement a simple system to monitor temperature and humidity using the DHT11 sensor and an Arduino board. The readings are displayed on the serial monitor. This project is ideal for beginners in electronics and programming, providing a hands-on experience with sensors, Arduino programming, and data monitoring.

### 2. Components
#### Hardware
Arduino Uno (or any compatible Arduino board)

DHT11 Temperature and Humidity Sensor

Jumper wires

USB cable for programming and power

#### Software
Arduino IDE

### 3. DHT11 Sensor Overview
The DHT11 sensor is a basic, low-cost digital temperature and humidity sensor. It uses a capacitive humidity sensor and a thermistor to measure the surrounding air, and outputs a digital signal on the data pin (no analog input pins needed).

#### Specifications
Humidity Range: 20-90% RH

Temperature Range: 0-50°C

Accuracy: ±5% RH and ±2°C

### 4. Circuit Connections

DHT11 Pin 1 (VCC) to Arduino 5V

DHT11 Pin 2 (Data) to Arduino Digital Pin 2

DHT11 Pin 4 (GND) to Arduino GND


### Visual Representation

![photo_2024-07-02_16-35-21](https://github.com/Nikk1729/CODETECH-Task2/assets/123321525/44aa8060-11ac-4961-9b59-fa7a753677f3)



 ### 5. Arduino Code

#include "DHT.h"

#define DHTPIN 2      // Pin where the DHT11 is connected

#define DHTTYPE DHT11 // DHT 11

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  
  Serial.begin(9600);
  
  Serial.println("DHT11 Temperature and Humidity Monitoring");
  
  dht.begin();
}

void loop() {
  
  // Wait a few seconds between measurements
  
  delay(2000);

  // Reading temperature or humidity takes about 250 milliseconds
  
  float humidity = dht.readHumidity();
  
  float temperature = dht.readTemperature();

  // Check if any reads failed and exit early (to try again)
  
  if (isnan(humidity) || isnan(temperature)) {
  
  Serial.println("Failed to read from DHT sensor!");
   return;
  }

  // Compute heat index
  
  float heatIndex = dht.computeHeatIndex(temperature, humidity, false);

  // Print results to Serial Monitor
  
  Serial.print("Humidity: ");
  
  Serial.print(humidity);
  
  Serial.print(" %\t");
  
  Serial.print("Temperature: ");
  
  Serial.print(temperature);
  
  Serial.print(" °C\t");
  
  Serial.print("Heat Index: ");
  
  Serial.print(heatIndex);
  
  Serial.println(" °C");

}

### 6. Implementation
#### Hardware Setup:

Connect the DHT11 sensor directly to the Arduino using jumper wires.
Ensure solid connections for reliable data readings.
#### Programming:

Install the DHT library in the Arduino IDE by navigating to Sketch -> Include Library -> Manage Libraries and searching for DHT.
Open the Arduino IDE, copy the provided code, and upload it to the Arduino board.

#### Monitoring:

Open the Serial Monitor from the Arduino IDE (Tools -> Serial Monitor).
Set the baud rate to 9600 to match the Serial.begin(9600); line in the code.
Observe the temperature and humidity readings displayed in the Serial Monitor.

#### 7. Results
The system continuously reads the temperature and humidity from the DHT11 sensor and outputs the data to the serial monitor every two seconds. The output includes the humidity percentage, temperature in Celsius, and the computed heat index.

#### Sample Output

DHT11 Temperature and Humidity Monitoring

Humidity: 45.00 %	Temperature: 23.00 °C	Heat Index: 23.57 °C

Humidity: 46.00 %	Temperature: 23.10 °C	Heat Index: 23.67 °C

### 8. Conclusion
This project successfully demonstrates the use of a DHT11 sensor with an Arduino to monitor temperature and humidity. The data is effectively displayed on the serial monitor, providing real-time insights into environmental conditions. This foundational project can be extended to include additional features such as data logging, graphical display, or wireless transmission of data.

#### 9. References
Arduino Official Website
DHT11 Sensor Datasheet
