// **** MUHAMMED ALİ ÖZEN***
const int trig = 11;//** ULTRASONİK  SENSÖRÜN BAĞLANTI PİNLERİ
const int echo = 12;//**

const int sagileri = 2;//***
const int saggeri = 3;//***
const int solileri = 4;//***MOTORLARIN BAĞLANTI PİNLERİ
const int solgeri = 5;//***

int  sure  = 0;
int  mesafe = 0;


void setup() {
  
  pinMode (trig , OUTPUT);//*HCSR04 ÜN BAĞLANTI PİNLERİ
  pinMode (echo , INPUT);//*
    
  pinMode (sagileri , OUTPUT); //MOTORLARI ÇIKIŞ OLARAK ATIYORUZ.
  pinMode (saggeri , OUTPUT);
  pinMode (solileri , OUTPUT);
  pinMode (solgeri , OUTPUT);
 



 }

void loop() {
  digitalWrite(trig , HIGH);
  delayMicroseconds(1000);
  digitalWrite(trig, LOW);

  sure = pulseIn(echo ,HIGH);
  mesafe = (sure/2) / 28.5;
  Serial.println(mesafe);
  if ( mesafe <= 30 ) // MESAFE Yİ AYARLIYORUZ
  

  {  
     digitalWrite(sagileri , LOW);
     digitalWrite(solileri , HIGH);// BU  KOMUTTA  ARABA 30 CM İLERİDE ENGEL GÖRÜRSE SAĞA DOĞRU DÖNER.
     digitalWrite(saggeri , HIGH);
     digitalWrite(solgeri , LOW);
    
    
  }
     else
  {
     digitalWrite(sagileri , HIGH);
     digitalWrite(solileri , HIGH);//BURDA İSE ARABA 30 CM İÇİNDE ENGEL YOKSA İLERİ GİDER .
     digitalWrite(saggeri , LOW);
     digitalWrite(solgeri , LOW);

  }
}
