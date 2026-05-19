BluaDiagnostics
Integrantes
Gabriel Guimarães de Oliveira — RM 567835
Pedro Paulo Ferreira Agnelo D'angelo — RM 567564
Nicolas Henriques Fernandes — RM 567123
Descrição do Projeto
O BluaDiagnostics é uma prova de conceito de um sistema de IA conversacional voltado para saúde digital, desenvolvido para a Care Plus (Blua).

O objetivo é transformar o app Blua de um sistema reativo para uma plataforma de cuidado proativo, com foco em check-ups digitais e triagem inteligente.

Persona
A persona escolhida é o beneficiário final em autoavaliação digital de saúde.

O sistema atua como um assistente de triagem inicial, auxiliando na coleta de sintomas e sinais vitais, sem substituir profissionais de saúde.

Objetivo
O sistema tem como objetivo:

Realizar check-up digital conversacional;
Coletar sintomas e sinais vitais;
Identificar possíveis red flags clínicas;
Apoiar o encaminhamento para teleconsulta;
Simular suporte a decisões clínicas iniciais;
Estruturar base para prescrição remota futura (com supervisão médica).
Escopo da Sprint 1
Inclui:

Chatbot com system prompt clínico;
Memória de conversa;
Function calling simulado;
Estrutura inicial de RAG;
Identificação de sinais de alerta;
Encaminhamento para atendimento humano.
Limitações:

Não realiza diagnóstico médico;
Não prescreve medicamentos;
Não substitui profissionais de saúde;
Funciona apenas como triagem assistida.
Riscos Clínicos e Éticos
Alucinação médica
Mitigado com system prompt restritivo e uso futuro de RAG.

Diagnóstico incorreto
O sistema não pode emitir diagnósticos.

LGPD
Não utiliza dados reais de pacientes na Sprint 1.

Jailbreak
Testado via eval set com tentativas de burlar regras.

Human-in-the-loop
Casos críticos são sempre encaminhados para humano.

Stack Técnica
GPT-4o-mini
LangChain
LangGraph (estrutura conceitual)
Python
FAISS (RAG futuro)
Google Colab
GitHub
Comparação de Modelos
Modelo	GPT-4o-mini	Claude 3.5 Sonnet
Custo	Baixo	Médio
Latência	Baixa	Média
Function Calling	Excelente	Muito bom
Uso clínico	Adequado	Excelente
Integração	Fácil	Média
Escolha final: GPT-4o-mini por custo-benefício e integração.

Avaliação (Eval Set)
O sistema foi testado com:

Casos normais (happy path)
Emergências (red flags)
Tentativas de jailbreak
Perguntas fora de escopo
Arquitetura
A arquitetura inclui:

Chatbot conversacional
System prompt clínico
Memória de contexto
RAG (base de conhecimento médica)
Function calling
Guardrails de segurança
Escalada para humano
Estrutura do Projeto
blua-diagnostics/ ├── README.md ├── docs/ ├── prompts/ ├── tools/ ├── evals/ ├── notebooks/ ├── rag_docs/ └── requirements.txt

Notebook
O notebook contém:

System prompt aplicado
Memória multi-turno
Function calling simulado
Testes de conversa clínica
Conclusão
O BluaDiagnostics demonstra como IA pode ser usada para triagem clínica assistida, mantendo segurança, ética e escalabilidade, sem substituir profissionais de saúde.
