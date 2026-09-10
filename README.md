🖥️ Hub de Telemetria IoT: Monitoramento e Alerta Térmico

![Status](https://img.shields.io/badge/Status-Em_Desenvolvimento-yellow)
![Hardware](https://img.shields.io/badge/Hardware-ESP32-blue)
![Backend](https://img.shields.io/badge/Backend-Python-3776AB?logo=python&logoColor=white)

## 📌 Sobre o Projeto
Este projeto foi desenvolvido como Projeto Final para a disciplina de **IMD0904 - Plataforma de Hardware para Internet das Coisas**.

O objetivo é solucionar a necessidade de monitoramento de performance e térmico de computadores durante cargas de trabalho intensas de forma não intrusiva. O sistema utiliza um **ESP32** atuando como um display de telemetria externo e um sistema de alerta visual periférico através de LEDs RGB, auxiliando na prevenção de *thermal throttling* (superaquecimento). O sistema cumpre o requisito de utilizar um microcontrolador em uma aplicação IoT com comunicação externa via internet e execução de tarefas em tempo real.

## ⚙️ Arquitetura do Sistema
O projeto constrói todo o ecossistema, desde o script de extração no sistema operacional até o firmware do microcontrolador, sendo dividido em três pilares:

1. **Módulo de Captura (Host PC):** Um serviço rodando em segundo plano desenvolvido em Python. Utiliza bibliotecas de acesso a hardware para ler o uso de CPU, RAM e GPU (como temperatura e clock).
2. **Mensageria (Nuvem):** Os dados são empacotados em JSON e enviados em tempo real para um Broker MQTT público, garantindo a comunicação externa via internet[cite: 1].
3. **Módulo IoT (Edge):** O ESP32, conectado via Wi-Fi, assina o tópico MQTT, processa as requisições assíncronas e atualiza os periféricos físicos.

## 🚀 Funcionalidades
- **Extração de Dados:** Leitura contínua e em tempo real dos sensores de hardware da máquina local.
- **Display Informativo:** Exibição gráfica e numérica da telemetria em uma tela controlada via I2C/SPI.
- **Alerta Térmico Inteligente:** Fita de LED endereçável (WS2812B) que transita suavemente entre cores (ex: do azul ao vermelho) refletindo a temperatura atual dos componentes.

## 🛠️ Componentes e Requisitos

### Hardware
* 1x Placa de Desenvolvimento ESP32
* 1x Display (OLED 0.96" I2C ou TFT 1.8" SPI)
* 1x Fita de LED WS2812B (5V)
* Jumpers e Protoboard
* Fonte de alimentação externa 5V (para os LEDs)

### Software / Dependências
* **Python 3.x:** `psutil`, `paho-mqtt`, `pynvml` (opcional, para GPUs NVIDIA).
* **Arduino IDE (C++):** Bibliotecas `PubSubClient` (MQTT), `Adafruit_GFX` (Display), `FastLED` (LEDs).

## 👨‍💻 Equipe
Davi Vieira de Carvalho Lima
Leandro Antony Batista Lemos
Andriel Vinicius de Medeiros Fernandes
Mariana Jamile dos Santos Ferreira
Vinicius Costa Soares

## 📝 Como Executar (Em breve)
*Instruções passo a passo sobre como rodar o script em Python, configurar o broker MQTT e fazer o flash do firmware no ESP32 serão adicionadas aqui após a conclusão do desenvolvimento.*
