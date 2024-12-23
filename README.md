# Practica-3-ESP32-con-LCD-y-DHT22

## Descripción

## En este repositorio se muestra como  podemos programar la pantalla LCD con lo anteriormente programado con el ESP32 y el DHT22

## Material Necesario

- wokwi
- ESP32
- DHT22
- lcd1602
- 
## Programación
```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

 

  lcd.clear();
  lcd.setCursor(2,0);
  lcd.print("Diplomado V");
  lcd. setCursor(2,1);
  lcd.print("Mecatronica");
  delay(2000);
  

   lcd.clear();
  lcd.setCursor(1,0);
  lcd.print("Miguel Montesinos");
  lcd. setCursor(2,1);
  lcd.print("Ing Mecanica");
  delay(2000);

   TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  delay(2000);

  
}
 ```
## Librerías

1. DHT Sensor Library for EXPx
2. LiquidCrystal I2C

## Conexión

![image](https://github.com/MiguelMontesinos/Practica-3-ESP32-con-LCD-y-DHT22/blob/main/Captura%20de%20pantalla%202024-12-12%20184824.png?raw=true)

## Instrucciones de operación 

1. Iniciar Simulador
2. Visualizar los datos en la pantalla LCD
3. Subir y Bajar la temperatura dando doble click al sensor DHT22 

## Resultados

Cuando funcione y Corra los valores serán mostrados en la pantalla LCD, cada 2 segundos se actualizará, mostrará primero el número del modulo, el nombre del diplomado. Luego mostrará mi nombre y mi carrera, y finalmente mostrará la temperatura y la humedad.

![image](https://github.com/MiguelMontesinos/Practica-3-ESP32-con-LCD-y-DHT22/blob/main/Captura%20de%20pantalla%202024-12-12%20183658.png?raw=true)

![image](https://github.com/MiguelMontesinos/Practica-3-ESP32-con-LCD-y-DHT22/blob/main/Captura%20de%20pantalla%202024-12-12%20183729.png?raw=true)

## Desarrollado por

**Ing. Miguel De Jesus Montesinos Molina** 

[GitHub](https://github.com/MiguelMontesinos).
