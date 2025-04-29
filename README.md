//ECEN-103-Final
//This includes the code used to make this circuit work.
const int ledPins[7] = {2, 3, 4, 5, 6, 7, 8};  
const int buttonPin = 15;                     

void setup() {
  for (int i = 0; i < 7; i++) {
    pinMode(ledPins[i], OUTPUT);
    digitalWrite(ledPins[i], LOW);
  }
  pinMode(buttonPin, INPUT_PULLUP);  
  randomSeed(analogRead(0));         
}

void loop() {
  if (digitalRead(buttonPin) == LOW) {  
    rollAnimation();                    
    int result = random(1, 7);          
    showDice(result);
    delay(1500);                        
    clearLEDs();
  }
  delay(20); // debounce
}

void rollAnimation() {
  for (int i = 0; i < 10; i++) {         
    int temp = random(1, 7);
    showDice(temp);
    delay(100 - i * 5);                   
    clearLEDs();
    delay(10);
  }
}

void clearLEDs() {
  for (int i = 0; i < 7; i++) {
    digitalWrite(ledPins[i], LOW);
  }
}

void showDice(int num) {
  switch (num) {
    case 1:
      digitalWrite(ledPins[3], HIGH);  
      break;
    case 2:
      digitalWrite(ledPins[0], HIGH); 
      digitalWrite(ledPins[6], HIGH);  
      break;
    case 3:
      digitalWrite(ledPins[0], HIGH);
      digitalWrite(ledPins[3], HIGH);
      digitalWrite(ledPins[6], HIGH);
      break;
    case 4:
      digitalWrite(ledPins[0], HIGH);
      digitalWrite(ledPins[2], HIGH);
      digitalWrite(ledPins[4], HIGH);
      digitalWrite(ledPins[6], HIGH);
      break;
    case 5:
      digitalWrite(ledPins[0], HIGH);
      digitalWrite(ledPins[2], HIGH);
      digitalWrite(ledPins[3], HIGH);
      digitalWrite(ledPins[4], HIGH);
      digitalWrite(ledPins[6], HIGH);
      break;
    case 6:
      digitalWrite(ledPins[0], HIGH);
      digitalWrite(ledPins[1], HIGH);
      digitalWrite(ledPins[2], HIGH);
      digitalWrite(ledPins[4], HIGH);
      digitalWrite(ledPins[5], HIGH);
      digitalWrite(ledPins[6], HIGH);
      break;
  }
}
