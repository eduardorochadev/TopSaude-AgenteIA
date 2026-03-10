# 🩺 Top Saúde – Agente IA de Atendimento (Camila)

Agente virtual inteligente para atendimento via **WhatsApp** da rede de clínicas **Top Saúde**, construído com **n8n** e **OpenAI (GPT-4o)**.

---

## 💡 Sobre o Projeto

A **Camila** é uma assistente virtual que atende pacientes da rede Top Saúde de forma humanizada e eficiente. Ela é capaz de:

- 🏥 Listar unidades disponíveis da rede
- 📋 Consultar especialidades, exames e procedimentos
- 💰 Informar valores de consultas e exames
- 📅 Agendar consultas e exames com escolha de data, médico e horário
- 🤝 Encaminhar para atendente humano quando necessário

## 🏢 Unidades Atendidas

| Unidade | Cidade |
|---|---|
| Centro | Caucaia |
| Jurema | Caucaia |
| Mozart Lucena | Fortaleza |
| Bezerra de Menezes | Fortaleza |

---

## 🛠️ Tecnologias

- **[n8n](https://n8n.io/)** – Orquestração do fluxo de automação
- **OpenAI GPT-4o** – Modelo de linguagem para conversação natural
- **API REST** – Integração com o sistema de gestão da clínica (agendamento, procedimentos, etc.)
- **WhatsApp** – Canal de atendimento ao paciente

---

## 📁 Estrutura do Projeto

```
├── AG1.json          # Fluxo n8n exportado (workflow completo)
├── PromptIA.md       # Prompt de sistema e instruções da IA
└── README.md         # Documentação do projeto
```

---

## 🔄 Fluxo de Atendimento

```
1. Seleção da Unidade
   └─► 2. Tipo de Atendimento (Consulta / Exame)
        └─► 3. Especialidade / Grupo
             └─► 4. Procedimento (com valores)
                  └─► 5. Data disponível
                       └─► 6. Médico e Horário
                            └─► 7. Confirmação e Agendamento (CPF + Nome)
```

---

## ⚙️ Ferramentas (Tools) da IA

O agente utiliza chamadas HTTP para a API do sistema de gestão:

| Ferramenta | Descrição |
|---|---|
| `listarUnidades` | Lista todas as clínicas da rede |
| `listarTipos` | Retorna tipos de atendimento (consulta/exame) |
| `listarGrupos` | Lista especialidades ou grupos de exames |
| `listarProcedimentos` | Lista procedimentos com valores |
| `listarDias` | Retorna datas com agenda disponível |
| `listarAgendas` | Lista médicos e horários para uma data |
| `efetuarAgendamento` | Realiza o agendamento do paciente |

---

## 🚀 Como Usar

### Pré-requisitos

- Instância do **n8n** em execução (self-hosted ou cloud)
- Chave de API da **OpenAI**
- API do sistema de gestão da clínica configurada e acessível

### Importação

1. Acesse o n8n e vá em **Workflows → Import from File**
2. Selecione o arquivo `AG1.json`
3. Atualize as variáveis de conexão:
   - Substitua `http://SEU_DOMINIO` pela URL da sua API
   - Configure a credencial do OpenAI
   - Ajuste o token de autenticação no header `Authorization`
4. Ative o workflow

---

## 📝 Personalização

O comportamento da Camila pode ser ajustado editando o arquivo `PromptIA.md`, que contém:

- **Identidade e tom de voz** da assistente
- **Regras de comportamento** (linguagem natural, empatia, concisão)
- **Fluxo completo de atendimento** passo a passo
- **Regras de UX** para formatação das mensagens

---

## 📄 Licença

Projeto de uso interno da rede **Top Saúde**.
