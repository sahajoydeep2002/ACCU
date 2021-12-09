#include "MQ135.h"
#include<ThingSpeak.h>
#include "Wire.h"
#include <ESP8266WiFi.h>

MQ135 gasSensor = MQ135(A0);

String apiKey="SBXD6NF8AFG7VHXS";
const int sensorPin = A0;

const char* ssid     = "Aerem.";
const char* password = "volkspolo";
const char* server = "api.thingspeak.com";

WiFiClient client;

void setup()
{
     Serial.begin(115200); 
   pinMode(sensorPin, INPUT);                 
    
  Serial.println();
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);

WiFi.begin(ssid, password);


while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address of NODEMCU= ");
  Serial.print(WiFi.localIP());
  ThingSpeak.begin(client);
}
void loop()
{
  {  
  float ppm = gasSensor.getPPM();
  Serial.print("Quality : ");
  Serial.println(ppm);
  ThingSpeak.writeField(1531288,2,ppm,"SBXD6NF8AFG7VHXS");
   delay(1000);
  }

          client.stop();
     
  Serial.println();
  delay(1000);
}       
