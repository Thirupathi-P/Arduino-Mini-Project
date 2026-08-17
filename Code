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
