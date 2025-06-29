# Projeto ESP32 - Cliente MQTT5 para Controle de LED

---

## Descrição

Este projeto implementa um cliente MQTT no ESP32 usando ESP-IDF e MQTT 5.  
O dispositivo conecta-se à rede Wi-Fi, conecta a um broker MQTT e se inscreve no tópico:

```
/ifpe/ads/embarcados/esp32/led
```

Quando recebe a mensagem `1` nesse tópico, o LED onboard acende.  
Quando recebe a mensagem `0`, o LED apaga.

---

## Configuração do ambiente

### 1. Pré-requisitos

- ESP-IDF instalado (versão recomendada: 5.x)  
- Toolchain configurada (compilador, Python, etc)  
- Cabo USB para conectar o ESP32 ao computador  

---


### 2. Criar um projeto MQTT5 usando um template da extenção ESP-IDF.



1. Abra a extenção.
2. New project.
3. Selecionar o seu esp-idf.
4. Defina nome do projeto e escolha uma pasta.
5. click em Choose Template.
6. Escolha ESP-IDF e busque por 'mqtt5'.
7. 'create project using template mqtt5'.
8. Project projetoUnidade1 has been created. Open project in a new window? 'yes'.

### 3. Configuração Wi-Fi e Broker MQTT

Antes de compilar, configure o Wi-Fi e o broker MQTT usando o menuconfig do ESP-IDF:

```bash
idf.py menuconfig
```

- Navegue até **Example Configuration > WiFi SSID** e insira sua rede Wi-Fi  
- Navegue até **Example Configuration > WiFi Password** e insira sua senha  
- Configure o broker MQTT em **Example Configuration > MQTT Broker URL**

---

## Como compilar e gravar o firmware

No terminal, estando dentro da pasta do projeto, execute:

```bash
idf.py build
idf.py -p COMx flash monitor
```

> Substitua `COMx` pela porta serial do seu ESP32 (exemplo: `COM5` no Windows).

O monitor abrirá mostrando os logs de conexão Wi-Fi, conexão MQTT e eventos diversos.

---

## Testando o controle do LED

Com o ESP32 conectado e o firmware rodando:

1. Utilize um cliente MQTT (exemplos: MQTT Explorer, MQTT.fx, mosquitto_pub)  
2. Publique mensagens no tópico:

```
/ifpe/ads/embarcados/esp32/led
```

- Envie o payload `1` para acender o LED  
- Envie o payload `0` para apagar o LED

---

## Limpeza do ambiente

Para limpar os arquivos gerados pelo build e reiniciar a compilação do zero, execute:

```bash
idf.py fullclean
```

---

## Contato

Matheus Lima  

---
