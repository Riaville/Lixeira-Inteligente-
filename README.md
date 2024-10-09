PROJETO ARDUINO Lixeira Automática com sensor ultrassônico

Vídeo de referencia: https://www.youtube.com/watch?v=9yrP1CZN3Ds Materiais para fazer o projeto:

- Balde de lixo
- Placa fina de isopor
- Bateria de 9V
- Micro servo motor 9g Sg90
- Sensor ultrassonico hc – sr04
- Arduino Uno r3

**Código fonte**
} #include <Servo.h> //servo library Servo servo; int trigPin = 5; int echoPin = 6; int servoPin = 7; int led= 10; long duration, dist, average; long aver[3]; //array for average void setup() { Serial.begin(9600); servo.attach(servoPin); pinMode(trigPin, OUTPUT); pinMode(echoPin, INPUT); servo.write(0); //close cap on power on delay(100); servo.detach(); } void measure() { digitalWrite(10,HIGH); digitalWrite(trigPin, LOW); delayMicroseconds(5); digitalWrite(trigPin, HIGH); delayMicroseconds(15); digitalWrite(trigPin, LOW); pinMode(echoPin, INPUT); duration = pulseIn(echoPin, HIGH); dist = (duration/2) / 29.1; //obtain distance } void loop() { for (int i=0;i<=2;i++) { //average distance measure(); aver[i]=dist; delay(10); //delay between measurements } dist=(aver[0]+aver[1]+aver[2])/3; if ( dist<50 ) { //Change distance as per your need servo.attach(servoPin); delay(1); servo.write(0); delay(3000); servo.write(150); delay(1000); servo.detach(); } Serial.print(dist); }

LINKS DE COMPRA DOS MATERIAIS

https://www.amazon.com.br/Bateria-Philips-alcalina-9V- unidade/dp/B0977C6L1M/ref=asc_df_B0977C6L1M/?tag=googleshopp00- 20&linkCode=df0&hvadid=709964503169&hvpos=&hvnetw=g&hvrand=153498187893531803 84&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1001773&hvtarg id=pla-2308313969202&psc=1&mcid=affc5211a21f3d95bcdb87ba2867507b&gad_source=1 https://www.mercadolivre.com.br/bateria-9v-alcalina-elgin-9-volts-1- cartela/p/MLB19692869?item_id=MLB4262289938&from=gshop&matt_tool=64671177&matt _word=&matt_source=google&matt_campaign_id=14302215732&matt_ad_group_id=135254 267473&matt_match_type=&matt_network=g&matt_device=c&matt_creative=58412557311 6&matt_keyword=&matt_ad_position=&matt_ad_type=pla&matt_merchant_id=735128761& matt_product_id=MLB19692869- product&matt_product_partition_id=2269729330258&matt_target_id=pla- 2269729330258&cq_src=google_ads&cq_cmp=14302215732&cq_net=g&cq_plt=gp&cq_med= pla&gad_source=1&gclid=EAIaIQobChMIjdGKrLaqiAMVGV5IAB1VETJAEAQYByABEgLnA_D_Bw E https://produto.mercadolivre.com.br/MLB-1613482166-micro-servo-motor-9g-sg90- acessorios- JM?matt_tool=47119386&matt_word=&matt_source=bing&matt_campaign=MLB_ML_BING AO_T%20%26%20B-ALL- ALL_X_PLA_ALLB_TXS_ALL&matt_campaign_id=382858300&matt_ad_group=T%20%26%20B& matt_match_type=e&matt_network=o&matt_device=c&matt_keyword=default&msclkid=c7cf 7d8a08c614725ac71b52e2fa88e4&utm_source=bing&utm_medium=cpc&utm_campaign=ML B_ML_BING_AO_T%20%26%20B-ALL- ALL_X_PLA_ALLB_TXS_ALL&utm_term=4581733690678445&utm_content=T%20%26%20B) https://www.eletrogate.com/modulo-sensor-de-distancia-ultrassonico-hc- sr04?utm_source=Site&utm_medium=GoogleMerchant&utm_campaign=GoogleMerchant&ut m_source=google&utm_medium=cpc&utm_campaign=[MC4][G][PMax]_ArduinoRoboticaSe nsoresModuloss&utm_content=&utm_term=&gad_source=1&gclid=Cj0KCQjwiuC2BhDSARIsAL OVfBLxU0E8KlOHR5_Tv0Y4kc2xIWiw-63OEdYcGB83kBIkdBi9y7UjajkaAtMJEALw_wcB
