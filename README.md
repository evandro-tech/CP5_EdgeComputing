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
- **MyMQTT:** Aplicativo que pode ser encontrado na playstore do celular pro monitoramento e envio de comandos.

## 🚀 Instruções de Execução

### 1. Acesso à Simulação (Wokwi)
1. Acesse o projeto oficial no simulador através do link:  
   👉 **[Wokwi - Vinheria Agnello CP5](https://wokwi.com/projects/478446407779040257)**
2. O código-fonte já se encontra configurado com as credenciais de rede (`Wokwi-GUEST`) e o broker MQTT do servidor.

### 2. Configuração do Servidor e Tópicos MQTT
* **Broker MQTT:** `3.135.234.101`
* **Porta:** `1883`
* **Tópico de Telemetria:** `/TEF/device002/attrs`
* **Tópico de Comando:** `/TEF/device002/cmd`

### 3. Validação no FIWARE (Postman)
Para verificar se os dados coletados pelo ESP32 estão armazenados corretamente no Context Broker, execute uma requisição **GET** utilizando o Postman:
* **URL:** `http://3.135.234.101:1026/v2/entities/urn:ngsi-ld:Lamp:002`
* **Headers:**
  * `fiware-service`: `smart`
  * `fiware-servicepath`: `/`

### 4. Utilização do Aplicativo MyMQTT (Leitura e Escrita)
1. Baixe e instale o aplicativo **MyMQTT** em um dispositivo Android.
2. Configure a conexão com o broker informando o IP `3.135.234.101` na porta `1883`.
3. **Leitura (Subscribe):** Inscreva-se no tópico `/TEF/device002/attrs` para visualizar as leituras dos sensores em tempo real.
4. **Escrita / Comandos (Publish):** No tópico `/TEF/device002/cmd`, envie os seguintes payloads para controlar o atuador (LED/Lâmpada):
   * Ligar: `device002@on|`
   * Desligar: `device002@off|`
