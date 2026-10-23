# Check Point 05 - Edge Computing (Vinheria Agnello)

## 📌 Descrição do Projeto
Este projeto consiste no desenvolvimento de um sistema de monitoramento IoT para a Vinheria Agnello utilizando ESP32 no simulador Wokwi, integrando sensores de temperatura/umidade (DHT22) e luminosidade (LDR) com o ecossistema FIWARE através do protocolo MQTT (UltraLight).

## 👥 Integrantes
- Evandro Marcondes - RM572473
- Pedro Marques - RMRM569307
- Raphael Oliveira - RM571065
- Renan Queiroz - RM569077

## 🛠️ Tecnologias Utilizadas
- **Wokwi:** Simulação do ESP32 e circuitos.
- **DHT22 & LDR:** Sensores de temperatura, umidade e luminosidade.
- **MQTT Broker / FIWARE:** Orion Context Broker, IoT Agent MQTT e STH Comet hospedados no servidor de testes.
- **Postman:** Provisionamento de serviços e dispositivos.
- **MyMQTT:** Aplicativo móvel para monitoramento e envio de comandos.

## 🚀 Instruções de Execução

### 1. Simulação no Wokwi
1. Abra o projeto no Wokwi.
2. Certifique-se de que o código está configurado com o broker correto (`3.135.234.101`) e os tópicos correspondentes ao seu dispositivo (ex: `/TEF/device002/attrs`).
3. Inicie a simulação e verifique o Monitor Serial.

### 2. Integração com o FIWARE
- Os dados são enviados automaticamente no formato UltraLight (`t|XX|h|XX|l|XX`).
- Você pode validar a chegada dos dados no Orion Context Broker utilizando o Postman com a requisição `GET` para a entidade correspondente (`urn:ngsi-ld:Lamp:002`), utilizando os headers:
  - `fiware-service: smart`
  - `fiware-servicepath: /`

### 3. Utilização do MyMQTT
1. Conecte o app MyMQTT ao broker `3.135.234.101` na porta `1883`.
2. Inscreva-se no tópico `/TEF/device002/attrs` para visualizar as leituras dos sensores no celular.
