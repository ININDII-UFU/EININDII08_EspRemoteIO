
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
3. Escolher **Projeto vazio**
4. Dar um nome para o projeto
5. Confirmar

💡 *Este passo cria a base do projeto PLC.*

---

### 🔹 Passo 2 – Selecionando o dispositivo PLC
![fig2](assets/imgs/fig2.png)

1. Na arvore de dispositivos **Clicar com o mouse direito** no nome do projeto 
2. Na opçoes que irão aparecer escolher **Adicionar dispositivos**

---

### 🔹 Passo 3 – Escolhendo o PLC utilizado 
![fig3](assets/imgs/fig3.png)

1. Na janela **Adicionar dispositivos** escolhar o PLC **CODESYS CONTROL Win V3 x64**
2. Na sequencia click no botão Adicionar dispositivo

⚠️ *Verifique se sua vertão é x64 ou x86*

---

### 🔹 Passo 4 – Inserir as configurações de Tarefas
![fig4](assets/imgs/fig4.png)

1. Clique com botão direito em **Application**
2. Na sequencia clique em **Adicionar Objeto**
3. Por último selecione **Configuração de Tarefas**

⚠️ *A configuração de Tarefas é o responsavel por todas as rotinas ciclicas.*
---

### 🔹 Passo 5 – Criar uma tarefa
![fig5](assets/imgs/fig5.png)

1. Clique com botão direito em **Application**
2. Na sequencia clique em **Adicionar Objeto**
3. Por último selecione **DOU**

⚠️ *Nesta etapa vc cria uma tarefa nova.*

---

### 🔹 Passo 6 – Iniciar a adição da tarefa
![fig6](assets/imgs/fig6.png)

1. De um nome para sua tarefa tipo **PLC_PRG**
2. Clicar com o botão esquerdo sobre **Programa**
3. Selecionar **Gráfico de Linguagem Ladder (LD)**

💡 *Você pode escolher um outro tipo de linguagem para sua tarefa.*

---

### 🔹 Passo 7 – Adicionar tarefa principal para o Loop
![fig7](assets/imgs/fig7.png)

1. Clique com o mouse direito sobre o **PLC_PRG** 
2. Sem soltar o mouse arraste o mesmo para dentro de **Task (IEC_Tasks)**.

⚠️ *No loop deve ter pelo menos uma tarefa, mas pode ter mais à seu critério.*

---

### 🔹 Passo 8 – Atualizar o dispositivo do PLC
![fig8](assets/imgs/fig8.png)

1. Na árvore de dispositivos, **clique com o botão direito** no **PLC (CODESYS Control RTE...)**
2. Selecione **Atualizar dispositivo...**

💡 *Isso ajuda o CODESYS a recarregar as opções e dispositivos disponíveis.*

---

### 🔹 Passo 9 – Adicionar o adaptador Ethernet
![fig9](assets/imgs/fig9.png)

1. Na janela **Adicionar dispositivo**, selecione **Ethernet**
2. Clique em **Adicionar dispositivo**

---

### 🔹 Passo 10 – Inserir dispositivo no Ethernet
![fig10](assets/imgs/fig10.png)

1. Clique com o botão direito em **Ethernet (Ethernet)**
2. Selecione **Adicionar dispositivo...**

---

### 🔹 Passo 11 – Adicionar Modbus TCP Client
![fig11](assets/imgs/fig11.png)

1. Selecione **Modbus TCP Client**
2. Clique em **Adicionar dispositivo**

---

### 🔹 Passo 12 – Adicionar dispositivo no Modbus TCP Client
![fig12](assets/imgs/fig12.png)

1. Clique com o botão direito em **Modbus_TCP_Client**
2. Selecione **Adicionar dispositivo...**

---

### 🔹 Passo 13 – Adicionar Modbus TCP Server
![fig13](assets/imgs/fig13.png)

1. Selecione **Modbus TCP Server**
2. Clique em **Adicionar dispositivo**

---

### 🔹 Passo 14 – Abrir os ícones ocultos do Windows
![fig14](assets/imgs/fig14.png)

1. Na barra do Windows, clique na seta **^** (ícones ocultos)

💡 *O CODESYS Control Win fica ativo nessa área.*

---

### 🔹 Passo 15 – Iniciar o CODESYS Control Win
![fig15](assets/imgs/fig15.png)

1. **Clique duas vezes** no ícone **CODESYS Control Win**

---

### 🔹 Passo 16 – Selecionar o controlador no projeto
![fig16](assets/imgs/fig16.png)

1. Selecione **CODESYS Control RTE...** na árvore de dispositivos

---

### 🔹 Passo 17 – Procurar o dispositivo na rede
![fig17](assets/imgs/fig17.png)

1. Em **Communication Settings**, clique em **Scan Network**

---

### 🔹 Passo 18 – Selecionar o dispositivo encontrado
![fig18](assets/imgs/fig18.png)

1. Selecione o dispositivo encontrado (ex.: **PC_...**)
2. Clique em **OK**

---

### 🔹 Passo 19 – Selecionar a interface de rede
![fig19](assets/imgs/fig19.png)

1. Clique em **Modbus_TCP_Client**
2. Clique em **Pesquisar...**
3. Selecione o **adaptador de rede correto**
4. Clique em **OK**

⚠️ *Adaptador incorreto impede a comunicação Modbus.*

---

### 🔹 Passo 20 – Habilitar reconexão automática
![fig20](assets/imgs/fig20.png)

1. Selecione **Modbus_TCP_Client**
2. Marque **Reconexão automática**

---

### 🔹 Passo 21 – Criar canais no Modbus TCP Server
![fig21](assets/imgs/fig21.png)

1. Selecione **Modbus_TCP_Server**
2. Clique em **Adicionar canal...**

---

### 🔹 Passo 22 – Configurar o Channel 0 (Coils)
![fig22](assets/imgs/fig22.png)

1. Defina o **Nome do canal** (ex.: Channel 0) 
2. Preencha tudo conforme esta a imagem.
3. Clique em **OK**

---

### 🔹 Passo 23 – Adicionar Channel 1 (Discrete Inputs)
![fig23](assets/imgs/fig23.png)

1. Clique em **Adicionar canal...**
2. Nomeie como **Channel 1**
3. Tipo: **Read Discrete Inputs (Função 2)**
4. Preencha tudo conforme esta a imagem.
5. Clique em **OK**

---

### 🔹 Passo 24 – Adicionar Channel 2 (Holding Registers)
![fig24](assets/imgs/fig24.png)

1. Clique em **Adicionar canal...**
2. Nome: **Channel 2**
3. Tipo: **Write Multiple Registers (Função 16)**
4. Preencha tudo conforme esta a imagem.
5. Clique em **OK**

---

### 🔹 Passo 25 – Adicionar Channel 3 (Input Registers)
![fig25](assets/imgs/fig25.png)

1. Clique em **Adicionar canal...**
2. Nome: **Channel 3**
3. Tipo: **Read Input Registers (Função 4)**
4. Preencha tudo conforme esta a imagem.
5. Clique em **OK**

---

### 🔹 Passo 26 – Conferir os canais criados
![fig26](assets/imgs/fig26.png)

1. Verifique se os **Channels 0 a 3** aparecem corretamente

💡 *Resumo do que o servidor Modbus irá disponibilizar.*

---

### 🔹 Passo 27 – Ajustar o Unit-ID do Modbus TCP Server
![fig27](assets/imgs/fig27.png)

1. Acesse **ModbusTCPServer Parâmetros**
2. Ajuste o **Unit-ID** para **1** 

💡 *Se estiver trabalhando com um dispositivo que não é 1 coloque o valor correspondente dele.*

---

### 🔹 Passo 28 – Mapear variáveis do PLC
![fig28](assets/imgs/fig28.png)

1. Acesse **Mapeamento de E/S**
2. Nomeie todas as variáveis do PLC aos canais Modbus conforme a imagem (ex.: **D2**)

💡 *Aqui ocorre a integração PLC ↔ Modbus.*

---

### 🔹 Passo 30 – Inserir uma bobina no Ladder
![fig30](assets/imgs/fig30.png)

1. Abra **PLC_PRG**
2. Clique com botão direito → **Inserir bobina**

---

### 🔹 Passo 31 – Selecionar a variável da bobina
![fig31](assets/imgs/fig31.png)

1. Clique no botão **...**
2. Selecione a variável (ex.: **RELE**)
3. Clique em **OK**

---

### 🔹 Passo 32 – Resultado final no Ladder
![fig32](assets/imgs/fig32.png)

1. Faça o mesmo da etapa anterior para a bobina.
✅ No final você deve ter o **Contato (RTN1)** e a **bobina (RELE)** adicionados com sucesso.

---

### 🔹 Passo 29 – Login e execução do PLC
![fig29](assets/imgs/fig29.png)

1. Clique em **Login**
2. Clique em **Run / Iniciar**

💡 *Nesta etapa o plc é inicido. Vá ate a ESP clique no botão RTN1 e a bobina RELE será acionada.*

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
