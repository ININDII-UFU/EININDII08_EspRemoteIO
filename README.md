
# Tutorial: Criação de Projeto Modbus no CODESYS V3.5 SP21 utilizando ESP_Remote_IO

## 🎯 Objetivo

Este tutorial tem como objetivo orientar, de forma **didática e passo a passo**, a criação de um **projeto Modbus no CODESYS V3.5 SP21**, utilizando a ferramenta **ESP_Remote_IO**, de modo que uma **ESP32 funcione como uma Remota Modbus**, permitindo comunicação completa com o sistema de controle.

Ao final deste procedimento, o sistema estará:
- ✅ Configurado no CODESYS
- ✅ Comunicando via Modbus
- ✅ Reconhecendo a ESP32 como uma remota de I/O

---

## 👥 Público-alvo

- Estudantes de **Engenharia / Automação Industrial**
- Alunos da disciplina **Instrumentação Industrial II – UFU**
- Profissionais iniciantes em **CODESYS e comunicação Modbus**

---

## 🧰 Pré-requisitos

### Software
- ✅ Windows 11
- ✅ CODESYS V3.5 SP21
- ✅ Git instalado
- ✅ ESP_Remote_IO (GitHub):
  https://github.com/ININDII-UFU/EININDII08_EspRemoteIO

### Hardware
- ✅ ESP32 configurada conforme o repositório
- ⚠️ Rede configurada corretamente (IP, firewall, cabo)

---

## 📋 Checklist antes de iniciar

- [ ] CODESYS instalado corretamente  
- [ ] ESP32 energizada  
- [ ] Firmware da ESP_Remote_IO carregado  
- [ ] Comunicação de rede funcional  

---

## 🧭 Passo a passo

### 🔹 Passo 1 – Criar um novo projeto no CODESYS
![fig1](assets/imgs/fig1.png)

1. Abrir o CODESYS
2. Selecionar **File → New Project**
3. Escolher **Standard Project**
4. Confirmar

💡 *Este passo cria a base do projeto PLC.*

---

### 🔹 Passo 2 – Selecionar o dispositivo PLC
![fig2](assets/imgs/fig2.png)

1. Escolher o dispositivo PLC adequado
2. Definir linguagem (ex: Structured Text)
3. Confirmar

⚠️ *A escolha incorreta do dispositivo pode impedir a comunicação.*

---

### 🔹 Passo 3 – Configuração inicial do projeto
![fig3](assets/imgs/fig3.png)

1. Verificar árvore de dispositivos
2. Confirmar criação do Application
3. Salvar o projeto

---

### 🔹 Passo 4 – Inserir o dispositivo Modbus TCP
![fig4](assets/imgs/fig4.png)

1. Clique com botão direito em **Device**
2. Add Device
3. Selecionar **Modbus TCP Master**

---

### 🔹 Passo 5 – Configurar parâmetros de comunicação
![fig5](assets/imgs/fig5.png)

1. Definir IP da ESP32
2. Porta padrão Modbus (502)
3. Timeout e ciclos de comunicação

⚠️ *IP incorreto impede comunicação.*

---

### 🔹 Passo 6 – Iniciar a adição de um dispositivo
![fig6](assets/imgs/fig6.png)

1. Clicar com o botão direito sobre **Application**
2. Selecionar **Add Device…**

💡 *Todo barramento de comunicação é tratado como um dispositivo no CODESYS.*

---

### 🔹 Passo 7 – Selecionar a interface Ethernet
![fig7](assets/imgs/fig7.png)

1. Localizar o dispositivo **Ethernet**
2. Manter o fabricante padrão (CODESYS)
3. Confirmar a adição da interface

⚠️ *A comunicação Modbus TCP exige interface Ethernet configurada.*

---

### 🔹 Passo 8 – Ethernet adicionada ao projeto
![fig8](assets/imgs/fig8.png)

1. Verificar se a interface **Ethernet** aparece na árvore do projeto
2. Confirmar que está vinculada à Application

---

### 🔹 Passo 9 – Adicionar dispositivo sobre a Ethernet
![fig9](assets/imgs/fig9.png)

1. Clicar com o botão direito sobre **Ethernet**
2. Selecionar **Add Device…**
3. Abrir a lista de protocolos compatíveis

---

### 🔹 Passo 10 – Inserir o Modbus TCP Master
![fig10](assets/imgs/fig10.png)

1. Selecionar **Modbus TCP Master**
2. Confirmar o fabricante **CODESYS**
3. Adicionar o dispositivo ao projeto

💡 *O Master será responsável por iniciar a comunicação Modbus.*

---

### 🔹 Passo 11 – Verificar o Master na árvore
![fig11](assets/imgs/fig11.png)

1. Confirmar que o **Modbus_TCP_Master** aparece abaixo da Ethernet
2. Verificar a hierarquia correta do barramento

---

### 🔹 Passo 12 – Preparar a adição do dispositivo escravo
![fig12](assets/imgs/fig12.png)

1. Clicar com o botão direito no **Modbus_TCP_Master**
2. Selecionar **Add Device…**

---

### 🔹 Passo 13 – Inserir o Modbus TCP Slave
![fig13](assets/imgs/fig13.png)

1. Selecionar **Modbus TCP Slave**
2. Confirmar a adição do dispositivo

💡 *Este Slave representa a ESP32 com firmware ESP_Remote_IO.*

---

### 🔹 Passo 14 – Slave adicionado na árvore
![fig14](assets/imgs/fig14.png)

1. Verificar se o Slave aparece abaixo do Master
2. Confirmar a estrutura **Ethernet → Master → Slave**

---

### 🔹 Passo 15 – Configurar o Unit ID do Slave
![fig15](assets/imgs/fig15.png)

1. Selecionar o **Modbus TCP Slave**
2. Acessar suas propriedades
3. Configurar o **Unit ID**
4. Garantir que o valor seja igual ao configurado na ESP32

⚠️ *Unit ID incorreto impede a comunicação.*

---

### 🔹 Passo 16 – Conferir a topologia de comunicação
![fig16](assets/imgs/fig16.png)

1. Analisar a topologia completa do projeto
2. Confirmar que todos os dispositivos estão no barramento correto

---

### 🔹 Passo 17 – Verificar o ambiente CODESYS em execução
![fig17](assets/imgs/fig17.png)

1. Confirmar que o CODESYS está em execução
2. Verificar se o projeto correto está carregado

---

### 🔹 Passo 18 – Iniciar o CODESYS a partir do atalho (se necessário)
![fig18](assets/imgs/fig18.png)

1. Localizar o atalho do CODESYS na área de trabalho
2. Executar o software
3. Abrir o projeto salvo

💡 *Garante que o ambiente esteja pronto para testes e download.*
### 🔹 Passo 19 – Acessar as configurações do Modbus TCP Slave
![fig19](assets/imgs/fig19.png)

1. Selecionar o **Modbus TCP Slave** na árvore de dispositivos
2. Abrir a aba de **Configurações / Parameters**
3. Verificar endereço IP e parâmetros básicos

💡 *Essas configurações definem como o dispositivo será identificado na rede.*

---

### 🔹 Passo 20 – Configurar endereço IP do Slave
![fig20](assets/imgs/fig20.png)

1. Definir o **Endereço IP** do dispositivo remoto
2. Configurar **Subnet Mask** e **Gateway**, se necessário
3. Garantir que o IP esteja na mesma rede do PLC

⚠️ *IPs fora da mesma sub-rede impedem a comunicação.*

---

### 🔹 Passo 21 – Ajustar porta de comunicação Modbus TCP
![fig21](assets/imgs/fig21.png)

1. Verificar a **porta TCP** configurada
2. Manter o valor padrão **502**, quando aplicável
3. Confirmar compatibilidade com o firmware da ESP32

---

### 🔹 Passo 22 – Acessar configuração de canais Modbus
![fig22](assets/imgs/fig22.png)

1. Expandir o **Modbus TCP Slave**
2. Localizar a seção de **Channels / I/O Mapping**
3. Preparar a criação dos canais de comunicação

💡 *Os canais representam as variáveis que serão trocadas via Modbus.*

---

### 🔹 Passo 23 – Criar canal de leitura (Input Registers)
![fig23](assets/imgs/fig23.png)

1. Adicionar um novo canal Modbus
2. Selecionar o tipo **Input Register**
3. Definir o endereço inicial do registro
4. Configurar o tipo de dado

---

### 🔹 Passo 24 – Criar canal de escrita (Holding Registers)
![fig24](assets/imgs/fig24.png)

1. Adicionar um novo canal Modbus
2. Selecionar o tipo **Holding Register**
3. Definir endereço e tamanho
4. Ajustar tipo de dado conforme a aplicação

⚠️ *O endereço deve coincidir com o definido no firmware da ESP32.*

---

### 🔹 Passo 25 – Verificar mapeamento dos canais Modbus
![fig25](assets/imgs/fig25.png)

1. Conferir todos os canais configurados
2. Verificar endereços, tipos e tamanhos
3. Garantir que não há sobreposição de registros

---

### 🔹 Passo 26 – Criar variáveis globais para comunicação
![fig26](assets/imgs/fig26.png)

1. Criar uma **Global Variable List (GVL)**
2. Definir variáveis associadas aos canais Modbus
3. Ajustar tipos de dados compatíveis

💡 *As GVLs facilitam o acesso às variáveis no programa PLC.*

---

### 🔹 Passo 27 – Associar variáveis aos canais Modbus
![fig27](assets/imgs/fig27.png)

1. Vincular cada canal Modbus a uma variável PLC
2. Confirmar a direção de leitura/escrita
3. Salvar as configurações

---

### 🔹 Passo 28 – Inserir variáveis no PLC_PRG
![fig28](assets/imgs/fig28.png)

1. Abrir a POU **PLC_PRG**
2. Inserir as variáveis globais no programa
3. Preparar a lógica de uso dos dados Modbus

---

### 🔹 Passo 29 – Implementar lógica de teste no programa
![fig29](assets/imgs/fig29.png)

1. Criar lógica simples de leitura/escrita
2. Utilizar valores fixos ou variáveis de teste
3. Verificar coerência do fluxo do programa

💡 *Este passo ajuda a validar a comunicação antes do uso real.*

---

### 🔹 Passo 30 – Compilar o projeto
![fig30](assets/imgs/fig30.png)

1. Selecionar **Build → Build**
2. Verificar se não há erros de compilação
3. Corrigir avisos, se existirem

⚠️ *Erros impedem o download do programa.*

---

### 🔹 Passo 31 – Fazer o download para o dispositivo
![fig31](assets/imgs/fig31.png)

1. Selecionar **Online → Login**
2. Realizar o download do programa
3. Confirmar a transferência para o dispositivo

---

### 🔹 Passo 32 – Colocar o PLC em modo RUN e testar comunicação
![fig32](assets/imgs/fig32.png)

1. Colocar o PLC em modo **RUN**
2. Monitorar as variáveis Modbus
3. Verificar troca de dados com a ESP32
4. Confirmar comunicação Modbus TCP funcionando

💡 *Se os valores atualizarem corretamente, a comunicação foi estabelecida com sucesso.*

---

Nestes passos são realizados:

1. Criação dos canais Modbus
2. Associação de registradores
3. Definição de tipos de dados
4. Ligação das variáveis ao programa PLC
5. Verificação online da comunicação

💡 *Siga rigorosamente a numeração indicada em cada imagem.*

---

## ✅ Resultado esperado

Ao final:
- ESP32 operando como **Remota Modbus**
- Comunicação estável com o CODESYS
- Leituras e escritas funcionais

---

## ⚠️ Observações importantes

- Sempre salvar o projeto após grandes alterações
- Conferir IP antes de colocar em RUN
- Em caso de erro, verificar firewall do Windows

---

## 📚 Referências

- Repositório ESP_Remote_IO:
  https://github.com/ININDII-UFU/EININDII08_EspRemoteIO
- Documentação CODESYS
