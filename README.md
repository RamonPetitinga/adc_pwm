# TAREFA: ADC PWM

## 📌 Descrição

Este projeto implementa a leitura de um joystick analógico utilizando o conversor analógico-digital (ADC) do microcontrolador RP2040, integrado à placa **BitDogLab**. O sistema controla a intensidade de LEDs RGB via PWM e exibe a posição do joystick em um display OLED **SSD1306** usando comunicação **I2C**. Além disso, os botões do joystick e um botão extra são utilizados para alternar funcionalidades adicionais.

## 🎥 Demonstração

O vídeo com a execução da simulação pode ser acessado em: https://youtu.be/TjWhrndvuvA

## PARA FUNCIONAR NA BITDOGLAB É NECESSARIO FAZER ALGUMAS ALTERAÇÕES NO CODIGO.

O código está funcionando perfeitamente no simulador wokwi e a BitDogLab possui o 'x' e o 'y' do Joystick invertido. Caso queira implementar o codigo na BitDogLab é só fazer essas inversões e deixar da seguinte forma:

    Altere as GPIO'S nas linhas 13 e 14:
    13 #define JOYSTICK_X_PIN 27
    14 #define JOYSTICK_Y_PIN 26

    Altere os adc_select_input(); nas linhas 114 e 118:
    114 adc_select_input(1);
    118 adc_select_input(0);


    Altere a variavel pos_x na linha 146:
    146 uint8_t pos_x = (adc_x * (WIDTH - 8)) / 4095;


    Com isso irá funcionar perfeitamente, caso voce queria implementar em uma BitDogLab.

## 🎯 Objetivos

✔️ Compreender o funcionamento do **Conversor Analógico-Digital (ADC)** no RP2040.  
✔️ Utilizar **PWM** para controlar a intensidade de LEDs RGB com base nos valores do joystick.  
✔️ Representar a posição do joystick no **display SSD1306** por meio de um quadrado móvel.  
✔️ Aplicar o **protocolo I2C** na comunicação com o display.  
✔️ Implementar **interrupções (IRQ)** e **debouncing** para os botões.

## 🛠️ Componentes Utilizados

- **Placa BitDogLab (RP2040)**
- **Joystick analógico** (Eixo X e Y analógicos + botão digital)
- **LED RGB** (controlado via PWM)
- **Display OLED SSD1306** (comunicação I2C)
- **Botão extra** para ativar/desativar os LEDs

## 📜 Funcionalidades Implementadas

1️⃣ **Controle dos LEDs RGB:**

- O **LED Azul** varia sua intensidade conforme o eixo **Y** do joystick.
- O **LED Vermelho** varia sua intensidade conforme o eixo **X** do joystick.
- Ambos são controlados via **PWM** para suavizar a transição.

2️⃣ **Movimentação no Display:**

- O display OLED **SSD1306** exibe um **quadrado 8x8 pixels** que se move proporcionalmente à posição do joystick.

3️⃣ **Botão do Joystick:**

- Alterna o estado do **LED Verde**.
- Modifica a **borda do display**, alternando entre fina e grossa.

4️⃣ **Botão A:**

- Ativa ou desativa os **LEDs RGB** controlados por PWM.

## 🔧 Como Compilar e Executar

### 1️⃣ Clonar o repositório

```bash
git clone https://github.com/RamonPetitinga/adc_pwm
```

### 2️⃣ Configurar o ambiente

Certifique-se de que o **Pico SDK** está configurado corretamente e que você tem o **CMake** instalado.

### 3️⃣ Compilar e Executar

Compile no VS Code e implemente o codigo na sua BitDogLab.
