# BluaDiagnostics

## Integrantes
- Nome — RM
- Nome — RM
- Nome — RM

---

# Persona Escolhida

A persona escolhida para o BluaDiagnostics foi o beneficiário final em processo de autoavaliação digital de saúde.

A escolha foi motivada pelos seguintes fatores:

- Redução da sobrecarga operacional em atendimentos iniciais;
- Potencial de escalabilidade do cuidado preventivo remoto;
- Melhor aderência ao conceito de cuidado proativo da Care Plus;
- Menor risco clínico comparado à automação direta de prescrições;
- Maior viabilidade técnica para a Sprint 1.

O agente atua apenas como suporte inicial de triagem e orientação, sem substituir profissionais da saúde.

---

# Objetivo do Projeto

O BluaDiagnostics tem como objetivo transformar o aplicativo Blua em uma plataforma de cuidado remoto proativo utilizando IA conversacional.

A solução busca:

- Realizar check-up digital conversacional;
- Coletar sintomas e sinais vitais;
- Detectar sinais de alerta clínico (red flags);
- Apoiar o encaminhamento médico;
- Automatizar processos como agendamento de teleconsulta.

O sistema foi desenvolvido com foco em segurança clínica, LGPD e abordagem human-in-the-loop.

---

# Escopo da Sprint 1

A Sprint 1 contempla uma prova de conceito funcional contendo:

- Chatbot conversacional com contexto clínico;
- System prompt especializado;
- Memória de conversa multi-turno;
- Simulação de function calling;
- Estrutura inicial para RAG;
- Encaminhamento para teleconsulta.

Limitações da Sprint 1:

- Não realiza diagnóstico definitivo;
- Não gera prescrição médica real;
- Não acessa prontuários reais;
- Não substitui profissionais de saúde.

---

# Riscos Clínicos e Éticos

## 1. Alucinação médica
O modelo pode gerar informações incorretas ou imprecisas.

Mitigação:
- Uso de system prompt restritivo;
- Limitação do escopo clínico;
- Escalada obrigatória para atendimento humano em casos críticos.

---

## 2. Diagnóstico indevido
O sistema não pode substituir avaliação médica profissional.

Mitigação:
- Proibição explícita de diagnóstico definitivo;
- Human-in-the-loop obrigatório;
- Encaminhamento para teleconsulta.

---

## 3. LGPD e privacidade
Dados clínicos são sensíveis.

Mitigação:
- Uso apenas de dados simulados;
- Não armazenamento de dados pessoais;
- Uso de variáveis de ambiente para credenciais.

---

## 4. Jailbreak e uso indevido
Usuários podem tentar forçar diagnósticos ou prescrições.

Mitigação:
- Restrições explícitas no system prompt;
- Eval set com cenários de jailbreak;
- Validação de respostas.

---

# Stack Técnica

| Categoria | Tecnologia |
|---|---|
| Modelo de IA | GPT-4o-mini |
| Framework | LangChain |
| Orquestração | LangGraph |
| Linguagem | Python |
| Banco Vetorial | FAISS |
| Ambiente | Google Colab |
| Versionamento | GitHub |

---

# Comparação de Modelos

| Critério | GPT-4o-mini | Claude 3.5 Sonnet |
|---|---|---|
| Qualidade clínica | Alta | Alta |
| Function Calling | Excelente | Muito bom |
| Latência | Baixa | Média |
| Custo | Baixo | Médio |
| Contexto | Alto | Alto |
| Facilidade de integração | Alta | Média |

O GPT-4o-mini foi escolhido devido ao melhor equilíbrio entre custo, velocidade e suporte robusto a function calling.
