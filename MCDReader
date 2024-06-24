#include <Wire.h>     // Library I2C Protocol
#include <LCD_I2C.h>  // Library for I2C Display
#include <SPI.h>      // Library for SPI Communication
#include <MFRC522.h>  // Library for managing card readers
#include <string.h>

#define SS_PIN 53      // SS Pin of RFID Module
#define RST_PIN 5      
#define I2C_ADDR 0x27  

int cont = 0;
String allowedUID = "E724C701";
String readUID = "";
MFRC522 mfrc522(SS_PIN, RST_PIN);
LCD_I2C lcd(I2C_ADDR, 16, 2);


bool timerActive = false;
unsigned long previousMillis;

void setup() {
  pinMode(12, OUTPUT);
  digitalWrite(12, HIGH);
  SPI.begin();
  mfrc522.PCD_Init();
  lcd.begin();
  lcd.backlight();
  lcd.print("Acercar tarjeta");
  lcd.setCursor(0, 1);
  lcd.print("Cant. gente: ");
  lcd.print(cont);
}

void loop() {
  unsigned long currentMillis = 0;




  if (mfrc522.PICC_IsNewCardPresent() && mfrc522.PICC_ReadCardSerial()) {
    lcd.clear();
    lcd.setCursor(0, 0);
    lcd.print("ID: ");
    readUID = "";  // Reiniciar readUID antes de comenzar a leer

    for (byte i = 0; i < mfrc522.uid.size; i++) {
      char buf[3];
      sprintf(buf, "%02X", mfrc522.uid.uidByte[i]);
      lcd.print(buf);
      readUID += String(buf);
    }

    if (readUID.equals(allowedUID)) {
      lcd.setCursor(0, 1);
      lcd.print("Permitido");
      digitalWrite(12, LOW);
      previousMillis = millis();
      cont++;
      timerActive = true;
    } else {
      cont--;
      lcd.setCursor(0, 1);
      timerActive = true;
      previousMillis = millis();
      if (timerActive) {
        if ((currentMillis - previousMillis) >= 2000) {
          lcd.setCursor(0, 1);
          lcd.print("No permitido");
          timerActive = true;
        }
      }
    }
    mfrc522.PICC_HaltA();
  }

  currentMillis = millis();
  if (timerActive) {
    if ((currentMillis - previousMillis) >= 5000) {
      digitalWrite(12, HIGH);
      lcd.clear();
      lcd.print("Acercar tarjeta");
      lcd.setCursor(0, 1);
      lcd.print("Cant. gente: ");
      lcd.print(cont);
      timerActive = false;
    }
  }
}
