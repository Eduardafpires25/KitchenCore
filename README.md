# 🧊 KitchenCore OS

Sistema inteligente de gerenciamento de estoque para geladeiras, desenvolvido como protótipo de **Internet das Coisas (IoT)**.

O **KitchenCore OS** simula sensores capazes de identificar os produtos presentes na geladeira, controlar suas quantidades, detectar itens que estão acabando ou já acabaram e adicioná-los automaticamente a uma lista de compras.

O sistema também permite interação através de **comandos de voz utilizando o microfone do computador**.

---

## 👨‍💻 Autores

- **Eduarda Fernandes Pires**
- **Igor Samuel Candido de Souza**

---

## 🎯 Objetivo do Projeto

O objetivo do KitchenCore OS é demonstrar como tecnologias de **Internet das Coisas** podem ser utilizadas para tornar uma geladeira capaz de monitorar seu próprio estoque.

Em uma implementação real, sensores instalados na geladeira coletariam informações sobre os alimentos e enviariam esses dados para o sistema.

Neste protótipo, os sensores físicos são simulados utilizando **JavaScript**, enquanto o microfone do computador pode ser utilizado como um sensor real para receber comandos do usuário.

---

## ⚙️ Funcionalidades

O sistema possui:

- 📦 Controle de estoque dos produtos;
- 📉 Detecção de produtos com estoque baixo;
- ❌ Identificação de produtos esgotados;
- 🛒 Lista de compras automática;
- ➕ Adição manual de produtos à lista;
- 🎤 Comandos de voz;
- 📷 Simulação de câmera;
- ⚖️ Simulação de sensor de peso;
- 🚪 Simulação de sensor da porta;
- 🔄 Simulação de consumo;
- 📦 Simulação de reposição;
- 💾 Salvamento das informações no navegador.

---

## 🧠 Classificação do Estoque

O KitchenCore OS classifica os produtos em três estados:

| Status | Descrição |
|---|---|
| 🟢 **SUFICIENTE** | Produto com quantidade adequada |
| 🟡 **ACABANDO** | Produto atingiu o estoque mínimo |
| 🟠 **ACABOU** | Produto sem estoque |

Quando um produto entra nos estados **ACABANDO** ou **ACABOU**, ele é automaticamente incluído na lista de compras.

---

## 🎤 Comandos de Voz

O sistema possui reconhecimento de voz em português.

Alguns comandos disponíveis são:

```text
Adicionar leite à lista
Adicionar café à lista
Remover leite da lista
Consumir um leite
Tem três ovos
Escanear geladeira
Limpar lista
```

Caso o reconhecimento de voz não esteja disponível, os mesmos comandos podem ser digitados no campo localizado na parte inferior da interface.

---

## 📡 Sensores Simulados

### 📷 Câmera

O botão **ESCANEAR** representa uma câmera instalada dentro da geladeira.

Ela seria responsável por reconhecer os produtos presentes no equipamento.

No protótipo, é realizada uma simulação de varredura do inventário.

---

### ⚖️ Sensor de Peso

O sistema simula células de carga utilizadas para detectar alterações no peso dos produtos.

Por exemplo:

```text
Leite: 2 unidades

↓

Produto retirado

↓

Leite: 1 unidade
```

O sistema interpreta a redução como consumo do produto.

---

### 🚪 Sensor da Porta

Durante ações de consumo ou reposição, o sistema simula a abertura e o fechamento da porta da geladeira.

Em um equipamento real, poderia ser utilizado um sensor magnético.

---

## 🌐 Arquitetura IoT

O funcionamento de uma versão física poderia seguir a seguinte arquitetura:

```text
┌─────────────────────────────┐
│       GELADEIRA             │
│                             │
│  📷 Câmera                  │
│  ⚖️ Sensor de Peso          │
│  🚪 Sensor da Porta         │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│     ESP32 / Raspberry Pi    │
│       Dispositivo IoT       │
└──────────────┬──────────────┘
               │
               │ Wi-Fi
               ▼
┌─────────────────────────────┐
│      Sistema / Servidor     │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│       KitchenCore OS        │
│                             │
│  Estoque                    │
│  Alertas                    │
│  Lista de Compras           │
│  Comandos de Voz            │
└──────────────┬──────────────┘
               │
               ▼
             Usuário
```

---

## 🔄 Fluxo do Sistema

```text
Sensor detecta alteração
        ↓
Dados são coletados
        ↓
Sistema processa os dados
        ↓
Estoque é atualizado
        ↓
Quantidade é analisada
        ↓
Produto suficiente?
       / \
     SIM  NÃO
      |    |
      |    └──► Produto acabando/acabou
      |                 ↓
      |         Adicionar à lista
      |                 ↓
      └────────► Atualizar painel
```

---

## 💻 Tecnologias Utilizadas

O projeto foi desenvolvido utilizando:

- **HTML5**
- **CSS3**
- **JavaScript**
- **Web Speech API**
- **LocalStorage**
- **Google Chrome**

Não é necessária a instalação de bibliotecas ou frameworks externos.

---

## 📂 Estrutura do Projeto

```text
KitchenCore/
│
├── index.html
└── README.md
```

O arquivo `index.html` contém toda a aplicação:

- Estrutura HTML;
- Estilização CSS;
- Lógica JavaScript;
- Sensores simulados;
- Sistema de voz;
- Lista de compras.

---

## 🚀 Como Executar

### Método 1 — Abrir diretamente

Baixe o projeto e abra:

```text
index.html
```

Preferencialmente utilizando o **Google Chrome**.

---

### Método 2 — Servidor Local

Para utilizar o microfone com maior compatibilidade, recomenda-se executar o projeto em um servidor local.

Abra o terminal dentro da pasta do projeto e execute:

```bash
python -m http.server 8000
```

Depois acesse no navegador:

```text
http://localhost:8000
```

Autorize o uso do microfone quando o navegador solicitar.

---

## 🎬 Como Demonstrar o Projeto

Uma demonstração simples pode seguir esta sequência:

1. Clique em **ESCANEAR**;
2. Mostre os produtos identificados;
3. Clique em **SIMULAR CONSUMO**;
4. Observe a redução da quantidade;
5. Repita até algum produto atingir estoque baixo;
6. Mostre que ele foi automaticamente para a lista de compras;
7. Clique no botão do microfone;
8. Fale:

```text
Adicionar café à lista
```

9. Mostre o café sendo adicionado automaticamente.

---

## 💾 Armazenamento

O sistema utiliza o `localStorage` do navegador.

Isso significa que alterações realizadas no estoque e na lista de compras podem permanecer salvas mesmo após atualizar a página.

---

## ⚠️ Limitações

O KitchenCore OS é atualmente um **protótipo acadêmico**.

Os seguintes componentes são simulados:

- câmera;
- sensor de peso;
- sensor da porta;
- comunicação com dispositivos IoT físicos.

O reconhecimento de voz é real, porém depende da compatibilidade do navegador e da permissão para utilizar o microfone.

---

## 🔮 Melhorias Futuras

O projeto pode futuramente receber:

- ESP32 conectado aos sensores;
- Células de carga físicas;
- Câmera com inteligência artificial;
- Reconhecimento automático de alimentos;
- Controle de validade dos produtos;
- Banco de dados em nuvem;
- Aplicativo para celular;
- Histórico de consumo;
- Notificações no smartphone;
- Sugestões inteligentes de compras;
- Integração com supermercados.

---

## 📌 Conceito de IoT aplicado

O KitchenCore OS representa os principais elementos de uma solução IoT:

```text
Sensoriamento
     ↓
Coleta de dados
     ↓
Processamento
     ↓
Tomada de decisão
     ↓
Interface
     ↓
Usuário
```

Dessa forma, mesmo utilizando sensores simulados, o projeto demonstra o funcionamento completo de uma solução de **Internet das Coisas aplicada a uma geladeira inteligente**.

---

## 📄 Projeto Acadêmico

**KitchenCore OS — Smart Fridge Inventory Management**

Desenvolvido por:

**Eduarda Fernandes Pires**  
**Igor Samuel Candido de Souza**
