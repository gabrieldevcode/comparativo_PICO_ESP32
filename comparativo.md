# Raspberry Pi Pico vs ESP32 — Comparativo Completo

## Visão Geral

| | **Raspberry Pi Pico** | **ESP32** |
|---|---|---|
| Fabricante | Raspberry Pi Foundation | Espressif Systems |
| Chip | RP2040 (ou RP2350 no Pico 2) | ESP32 (várias variantes: WROOM, WROVER, S3, C3...) |
| CPU | Dual-core ARM Cortex-M0+ @ 133 MHz | Dual-core Xtensa LX6 @ 240 MHz (ou single-core em algumas variantes) |
| RAM | 264 KB SRAM | 320–520 KB SRAM (varia por modelo) |
| Wi-Fi / Bluetooth | Não (Pico W tem Wi-Fi; sem Bluetooth) | Sim, nativo (Wi-Fi + Bluetooth Classic/BLE) |
| Preço aproximado | US$ 4–6 (Pico W) | US$ 3–8 |
| GPIOs | 26 pinos | 25–36 pinos, dependendo do modelo |

---

## Principal Diferença

A diferença central é **conectividade nativa vs. controle de baixo nível preciso**.

- O **ESP32** já nasce com Wi-Fi e Bluetooth embutidos, sendo a escolha natural para qualquer projeto que precise se conectar à internet, a um app, ou a outros dispositivos sem fio.
- O **Pico** (na versão original) não tem rádio nenhum — é focado em ser um microcontrolador puro, barato e com periféricos programáveis muito flexíveis, especialmente o **PIO (Programmable I/O)**, um recurso exclusivo do RP2040 que permite implementar protocolos de hardware customizados (como controlar LEDs endereçáveis, gerar sinais de vídeo, ou emular interfaces que normalmente exigiriam chips dedicados).

---

## O que cada um faz melhor

### ESP32 se destaca em:
- Conectividade Wi-Fi/Bluetooth nativa (sem hardware extra)
- Projetos IoT (enviar dados para nuvem, controlar via app, servidores web embutidos)
- Ecossistema maduro de bibliotecas para redes, MQTT, HTTP, OTA (atualização de firmware remota)
- Mais potência de processamento bruta (240 MHz vs 133 MHz)
- Maior variedade de módulos com câmera, tela, PSRAM etc. (ex: ESP32-CAM, ESP32-S3)

### Raspberry Pi Pico se destaca em:
- Preço mais baixo e previsibilidade de fornecimento
- PIO — controle de I/O em nível de hardware, ótimo para sinais de tempo crítico
- Consumo de energia geralmente menor em modo ativo (sem rádio ligado)
- Toolchain em C/C++ e MicroPython muito bem documentada pela Raspberry Pi Foundation
- Melhor previsibilidade de timing (útil em automação industrial simples, controle de motores, protocolos customizados)
- Debugging via SWD mais acessível e barato

---

## Para quais tipos de projeto usar cada um

| Tipo de projeto | Melhor escolha |
|---|---|
| Projeto IoT com envio de dados para nuvem/app | **ESP32** |
| Automação residencial conectada (Wi-Fi/BLE) | **ESP32** |
| Controle de LEDs endereçáveis, sinais customizados de timing | **Pico** (via PIO) |
| Projeto que precisa de câmera embutida | **ESP32** (ESP32-CAM/S3) |
| Robótica com controle preciso de motores/sensores locais, sem necessidade de rede | **Pico** |
| Protótipo de baixíssimo custo, sem conectividade | **Pico** |
| Dispositivo wearable com Bluetooth | **ESP32** |
| Projeto educacional (aprender fundamentos de microcontrolador) | Ambos, mas o **Pico** é mais didático pela simplicidade e documentação da Raspberry Pi Foundation |

---

## Ecossistema e Comunidade

### ESP32
- Comunidade **enorme e madura**, construída em cima do legado do ESP8266
- Suporte nativo no **Arduino IDE**, **PlatformIO**, **ESP-IDF** (framework oficial da Espressif) e **MicroPython**
- Grande volume de tutoriais, fóruns e projetos prontos (especialmente para automação residencial, IoT e projetos "maker" em geral)
- Forte presença em produtos comerciais (muitos dispositivos IoT do mercado usam ESP32 internamente)

### Raspberry Pi Pico
- Comunidade menor, mas **muito bem organizada**, com apoio direto da Raspberry Pi Foundation
- Documentação oficial excelente (datasheets, guias "Getting Started" muito claros)
- Suporte a **MicroPython**, **CircuitPython** e **C/C++ SDK oficial**
- Beneficiado pelo ecossistema geral da marca Raspberry Pi (mesma comunidade que já usa Raspberry Pi 4/5), o que facilita quem já vem desse universo
- Crescimento mais recente, então tem menos "anos de tutoriais acumulados" que o ESP32

---

## Resumo em uma frase

**ESP32** = melhor quando o projeto precisa de conexão sem fio nativa (Wi-Fi/Bluetooth) e mais poder de processamento.
**Pico** = melhor quando o projeto precisa de controle de hardware muito preciso (PIO), baixo custo, e não depende de conectividade sem fio.

Na prática, muitos makers usam os dois: ESP32 para o "cérebro conectado" do projeto e Pico para tarefas de controle em tempo real que exigem timing preciso.
