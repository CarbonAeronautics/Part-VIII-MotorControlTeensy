#include <PulsePosition.h>
PulsePositionInput ReceiverInput(RISING);
float ReceiverValue[]={0, 0, 0, 0, 0, 0, 0, 0};
int ChannelNumber=0; 
float InputThrottle;
void read_receiver(void){
  ChannelNumber = ReceiverInput.available();
  if (ChannelNumber > 0) {
  for (int i=1; i<=ChannelNumber;i++){
    ReceiverValue[i-1]=ReceiverInput.read(i);
    }
  }
}
void setup() {
  Serial.begin(57600);
  pinMode(13, OUTPUT); 
  digitalWrite(13, HIGH);
  ReceiverInput.begin(14);
  analogWriteFrequency(1, 250);
  analogWriteResolution(12);
  delay(250);
  while (ReceiverValue[2] < 1020 ||
    ReceiverValue[2] > 1050) {
      read_receiver();
      delay(4);
    }
}
void loop() {
  read_receiver();
  InputThrottle=ReceiverValue[2];
  analogWrite(1,1.024*InputThrottle);
}
