# Password Access Provided Using Arduino UNO

A simple embedded systems project that checks a password via the Serial Monitor and indicates the result using an LED.


## What it Does

We need Enter the password via Serial Monitor<br>
- LED blinks 3 times on correct password<br>
- LED stays ON for 1 second on wrong password<br>

## Components Used

-Arduino UNO<br>
-Breadboard<br>
-1× LED <br>
=1× 220Ω resistor <br>
-Jumper wires <br>


## Code

```cpp

int ledPin = 13;
String MyPassword = "1234"; 
String inputPassword = "";

void setup() 
{
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
  Serial.println("Enter your password:");
}

void loop() {
  if (Serial.available() > 0)
   {
    inputPassword = Serial.readStringUntil('\n');
    inputPassword.trim();  // remove extra spaces/newline chars

    if (inputPassword == MyPassword) {
      Serial.println("Access Granted!");
      correct();
    } else {
      Serial.println("Access Denied!");
      wrong();
    }

    Serial.println("Enter your password:");
  }
}

void correct() 
{
  for (int i = 0; i < 3; i++) 
  {
    digitalWrite(ledPin, HIGH);
    delay(300);
    digitalWrite(ledPin, LOW);
    delay(200);
  }
}

void wrong() 
{
  digitalWrite(ledPin, HIGH);
  delay(1000);
  digitalWrite(ledPin, LOW);
}
```
