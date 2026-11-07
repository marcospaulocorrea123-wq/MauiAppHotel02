# 🏨 MauiAppHotel - Sistema de Gestão de Hospedagem

Aplicativo desenvolvido com **.NET MAUI** para cálculo, gerenciamento e reserva de hospedagem em hotel. Este projeto foi desenvolvido durante o curso **Técnico em Desenvolvimento de Sistemas** (Componente Curricular: *Desenvolvimento de Sistemas II* / *Programação Mobile I* — Agenda 13 e Agenda 14).

---

## 📱 Visão Geral do Projeto

O **MauiAppHotel** tem como objetivo explorar a construção de interfaces modernas com o .NET MAUI, aplicando o conceito de **Data Binding** e **BindingContext**, além da estrutura de navegação com **AppShell** e a implementação prática de **Programação Orientada a Objetos (POO)** em C#.

### 🚀 Funcionalidades da Aplicação:
- **Seleção de Suítes:** Escolha da categoria de acomodação através do componente `Picker`.
- **Controle de Hóspedes:** Incremento e decremento do número de adultos e crianças utilizando o controle numérico `Stepper`.
- **Período de Hospedagem:** Seleção das datas de entrada (*check-in*) e saída (*check-out*) via `DatePicker`, com validações de intervalos de datas.
- **Tela Sobre (Exigência do Fichário 13):** Apresentação clara das informações do desenvolvedor e ano de desenvolvimento em layout limpo com cartões (`Border`).
- **Navegação com AppShell:** Alternância entre páginas por meio de rotas integradas (menu lateral e abas).
- **Dimensionamento Responsivo no Windows:** Janela travada em 480 × 720 pixels no método `CreateWindow`, simulando com exatidão a visualização vertical de um smartphone.



---

## 🕹️ Como Utilizar a Aplicação

### 1. Executando o Projeto Localmente
1. Clone o repositório ou baixe os arquivos para o seu computador.
2. Abra a solução **`MauiAppHotel.sln`** no **Visual Studio** (com a carga de trabalho *.NET Multi-platform App UI* instalada).
3. Na barra superior de execução, certifique-se de que o destino está selecionado como **Máquina Windows** (ou um emulador Android configurado).
4. Pressione **`Ctrl + F5`** (ou clique no botão verde de play) para compilar e iniciar o aplicativo.

---

### 2. Passo a Passo no Aplicativo (Fluxo de Uso)

#### 📋 Etapa 1: Contratação de Hospedagem (Tela Principal)
* **Escolha da Acomodação:** Clique na caixa de seleção (`Picker`) para escolher o tipo de suíte desejada (ex.: *Super Luxo*, *Executiva* ou *Crise*).
* **Definição de Hóspedes:** 
  * Utilize os botões **`+`** e **`-`** do controle numérico (`Stepper`) para definir a quantidade de **Adultos**.
  * Ajuste de forma semelhante o número de **Crianças** que farão parte da estadia.
* **Período da Reserva:**
  * Toque no campo **Check-in** (`DatePicker`) para definir o dia de entrada no hotel.
  * Toque no campo **Check-out** (`DatePicker`) para indicar a data de saída.
* **Avançar:** Após preencher os dados, clique no botão para calcular e visualizar o resumo da contratação.

#### ℹ️ Etapa 2: Acessando a Tela Sobre
* No canto superior esquerdo da tela, abra o menu lateral (**AppShell**) ou navegue pelas abas disponíveis.
* Selecione a opção **"Sobre"** para visualizar as informações do desenvolvedor, ano do projeto e dados acadêmicos exigidos para a entrega da **Agenda 13**.

---

## 📸 Demonstração da Aplicação (Capturas de Tela)



......***Tela Principal (Hospedagem)*........ *Tela Menu (Hospedagem/Sobre)*........ *Tela Sobre (Desenvolvedor)***

<img width="250" height="400" alt="AppTela01" src="https://github.com/user-attachments/assets/1b2f3e99-2668-4aa5-88a7-fe6e295b443e" /> <img width="250" height="400" alt="AppTela02" src="https://github.com/user-attachments/assets/936332df-afbe-4749-b364-1df63f925137" /> <img width="250" height="400" alt="AppTela03" src="https://github.com/user-attachments/assets/de9168b9-5e7a-4828-abe4-b8f796101ccf" />


## 




## 



---

## ⚙️ Desafios Técnicos Enfrentados e Solução de Versões do SDK

Durante o ciclo de compilação e teste no ambiente local, foram diagnosticadas e superadas divergências técnicas entre as cargas de trabalho do Visual Studio e as versões do SDK:

### 1. Incompatibilidade de Pacotes e Cargas de Trabalho Legadas
- **Cenário:** O repositório herdado continha avisos de pacotes sem versão explícita (`NU1015`) e workloads apontando para versões descontinuadas do .NET com alertas de fim de suporte (`NETSDK1202`).
- **Solução:** O projeto foi reconstruído em cima de uma estrutura nova e limpa do template oficial do .NET MAUI, permitindo que as dependências fossem restauradas perfeitamente via NuGet.

### 2. Conflito do Gerador Experimental de XAML (`MauiXamlInflator=SourceGen`)
- **Cenário:** Em compilações com SDKs recentes/previews (`net10.0` / SDK `11.0.100-rc.3`), o recurso experimental `MauiXamlInflator=SourceGen` causou falha na geração das classes parciais em tempo de compilação, disparando o erro:
  > `error CS0103: O nome "InitializeComponent" não existe no contexto atual`
- **Solução:** A tela `Sobre` foi refatorada e implementada em **C# puro (Code-Behind Declarativo)** no arquivo `Views/Sobre.cs`. Isso eliminou a dependência do analisador de XAML experimental em pré-compilação, garantindo 100% de estabilidade e execução imediata com código de saída limpo `0 (0x0)`.

### 3. Ajuste de Tamanho de Janela para Desktop
- Controle da dimensão da janela no Windows configurado diretamente no método `CreateWindow` do arquivo `App.xaml.cs`, garantindo estabilidade visual e proporções ideais para testes móveis no PC.

---

## 📁 Estrutura do Projeto


MauiAppHotel/
├── Platforms/            # Configurações de plataforma (Windows, Android, etc.)
├── Resources/            # Estilos, ícones, fontes e imagens
│   └── Images/           # Ícones e imagens do aplicativo
├── Views/                # Telas da aplicação
│   ├── ContratacaoHospedagem.xaml     # Tela principal de seleção da reserva
│   ├── HospedagemContratada.xaml      # Tela de resumo e cálculo de diárias
│   └── Sobre.cs                       # Tela Sobre em C# (Layout limpo com Cards)
├── App.xaml / App.xaml.cs             # Configuração inicial e tamanho de janela
├── AppShell.xaml / AppShell.xaml.cs   # Definição das rotas de navegação

---

## 🛠️ Tecnologias e Ferramentas 

<p align="center">
  <img src="https://img.shields.io/badge/C%23-.NET%20MAUI-512BD4?style=for-the-badge&logo=dotnet&logoColor=white"/>
  <img src="https://img.shields.io/badge/.NET-MAUI-512BD4?style=for-the-badge&logo=dotnet&logoColor=white"/>
  <img src="https://img.shields.io/badge/Visual%20Studio-Community-5C2D91?style=for-the-badge&logo=visualstudio&logoColor=white"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Git-Version%20Control-F05032?style=for-the-badge&logo=git&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub-Repositories-181717?style=for-the-badge&logo=github&logoColor=white"/>
  <img src="https://img.shields.io/badge/Notepad%2B%2B-Editor-90E59A?style=for-the-badge&logo=notepadplusplus&logoColor=black"/>
</p>
└── MauiProgram.cs                     # Ponto de entrada (builder) da aplicação

---

👨‍💻 Desenvolvedor
Nome: Marcos Paulo Correa
Ano de Desenvolvimento: 2026
Curso: Técnico em Desenvolvimento de Sistemas
Componente Curricular: Desenvolvimento de Sistemas II / Programação Mobile I (Agenda 13)
---
