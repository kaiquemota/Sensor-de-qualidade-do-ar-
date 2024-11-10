# SENSOR DE MONITORAMENTO DA QUALIDADE DO AR PARA AMBIENTES INDUSTRIAIS

Projeto de conclusão da matéria Objetos Inteligentes Conectados da Universidade Presbiteriana Mackenzie.

**Aluno: Kaique Mota Carvalho**
<br />
**RA: 10369957**
<br />
**Professores: Andre Luis de Oliveira e Leandro Carlos Fernandes**
<br />
<br />
<br />
Este projeto tem como objetivo monitorar gases poluentes em ambientes industriais utilizando uma placa ESP8266 NodeMCU, um sensor de gás MQ-2 e um atuador LED 5mm para indicar a presença de gases acima de um limite seguro. Ele se comunica com um broker MQTT, usando o serviço Adafruit IO para enviar dados em tempo real e acionar alertas remotos.

**Componentes:**
- ESP8266 NodeMCU: microcontrolador com Wi-Fi, usado para receber os dados do sensor e enviar ao broker MQTT.
- Sensor de gás MQ-2: detecta gases inflamáveis (como GLP, propano, metano) e fumaça, gerando um sinal analógico proporcional à concentração.
- Atuador LED 5mm: indica visualmente o status, acendendo quando a concentração de gás ultrapassa o limite configurado.
- Broker MQTT (Adafruit IO): permite enviar e visualizar dados remotamente pela dashboard, facilitando o monitoramento online.
- Jumpers Macho: responsáveis por fazer as conexões entre os componentes.
- Protoboard: placa com diversas conexões condutoras verticais e horizontais para a montagem do projeto.
  
**Plataforma de desenvolvimento:** Arduino IDE
  <br />
  <br />
  ## Como reproduzir
  <br />
 Para compilar e executar o código na placa ESP8266 NodeMCU, siga este guia:

### 1. Configurar o Arduino IDE para a ESP8266

Instale o Arduino IDE: Se ainda não tiver o Arduino IDE, baixe e instale a partir de [arduino.cc](https://www.arduino.cc/en/software).
<br />
Adicione a placa ESP8266 
<br />
Abra o Arduino IDE e vá em:
   - Arquivo > Preferências
   - Em URLs adicionais para Gerenciadores de Placas, insira o seguinte link: 
     ```
     http://arduino.esp8266.com/stable/package_esp8266com_index.json
     ```
   - Clique em OK.
<br />
     Instalar a placa ESP8266:
     <br />
   - Vá para Ferramentas > Placa > Gerenciador de Placas.
     <br />
   - Pesquise por ESP8266 e instale a versão mais recente da biblioteca ESP8266 by ESP8266 Community.
<br /> 
    Selecionar a placa correta:
<br />
   - Em Ferramentas > Placa, selecione NodeMCU 1.0 (ESP-12E Module).

### 2. Instalar Bibliotecas Necessárias

- ESP8266WiFi e Adafruit MQTT Library: 
  - No Arduino IDE, vá em Sketch > Incluir Biblioteca > Gerenciar Bibliotecas.
  - Pesquise por ESP8266WiFi e instale, caso ainda não esteja instalada.
  - Depois, pesquise por Adafruit MQTT Library e instale a biblioteca.

### 3. Configurar o Código

SSID e Senha Wi-Fi: No código, altere as variáveis `wifiSSID` e `wifiPassword` para as credenciais da sua rede Wi-Fi:
   ```cpp
   const char* wifiSSID = "SEU_SSID";  
   const char* wifiPassword = "SUA_SENHA";
   ```

Credenciais Adafruit IO: Altere `AIO_USERNAME` e `AIO_KEY` para os valores da sua conta no Adafruit IO:
   ```cpp
   #define AIO_USERNAME    "SEU_USERNAME"  
   #define AIO_KEY         "SUA_AIO_KEY"
   ```

Limite de Gás (gasLimit): Defina o valor de limite (`gasLimit`) conforme necessário para seu ambiente.

### 4. Conectar a Placa ao Computador

Conecte o ESP8266 ao computador usando um cabo micro-USB. Verifique se a porta correta está selecionada:
- Em Ferramentas > Porta, selecione a porta onde o ESP8266 está conectado (ex., `COM3`, `COM4` no Windows, ou `/dev/ttyUSB0` no Linux).

### 5. Compilar e Carregar o Código

Clique no botão Verificar (ícone de check) para compilar o código.
<br />
Depois, clique em Carregar (ícone de seta) para enviar o código para a placa.
<br />
Acompanhe o console para verificar se o carregamento foi concluído sem erros.

### 6. Monitoramento em Tempo Real

Após carregar o código com sucesso, você pode visualizar as leituras do sensor de gás no Monitor Serial:
<br />
Vá em Ferramentas > Monitor Serial.
<br />
Defina a velocidade de comunicação para **9600 baud** no canto inferior direito do Monitor Serial.
<br />
O código mostrará o nível de gás em tempo real, indicando "Nível Seguro" ou "Nível Perigoso" e acendendo o LED quando o limite for ultrapassado. Os dados também serão enviados para o feed `gaslevel` no Adafruit IO, permitindo monitoramento remoto.

### 7. Visualizar Dados no Adafruit IO

Acesse [io.adafruit.com](https://io.adafruit.com/) e faça login.
<br />
No painel da sua conta, vá até o feed `gaslevel` para visualizar os dados recebidos.
<br />
Você pode configurar gráficos ou indicadores no **Dashboard** do Adafruit IO para acompanhar as leituras de gás em tempo real e ver o status do ambiente.


  
