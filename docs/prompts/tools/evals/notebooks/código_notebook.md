CÉLULA 1 — INSTALAÇÃO
!pip install openai python-dotenv

CÉLULA 2 — IMPORTS
from openai import OpenAI
import json
import os

CÉLULA 3 — CLIENTE
from openai import OpenAI

client = OpenAI(
    api_key="cole sua chave API aqui"
)

CÉLULA 4 — SYSTEM PROMPT
system_prompt = """
Você é o BluaDiagnostics, um assistente virtual de saúde da plataforma Blua da Care Plus.

Você realiza triagem inicial conversacional e orientação básica.

Você NÃO pode:
- diagnosticar doenças,
- prescrever medicamentos,
- substituir médicos.

Caso existam sintomas graves, encaminhe imediatamente para emergência ou teleconsulta.
"""

CÉLULA 5 — TOOLS
tools = [
    {
        "type": "function",
        "function": {
            "name": "agendar_teleconsulta",
            "description": "Agenda uma teleconsulta médica.",
            "parameters": {
                "type": "object",
                "properties": {
                    "especialidade": {
                        "type": "string"
                    },
                    "urgencia": {
                        "type": "string"
                    }
                },
                "required": ["especialidade", "urgencia"]
            }
        }
    }
]


CÉLULA 6 — FUNÇÃO MOCK
def agendar_teleconsulta(especialidade, urgencia):
    return {
        "status": "sucesso",
        "especialidade": especialidade,
        "urgencia": urgencia,
        "mensagem": "Teleconsulta agendada com sucesso."
    }


CÉLULA 7 — MEMÓRIA
messages = [
    {
        "role": "system",
        "content": system_prompt
    }
]


CÉLULA 8 — PRIMEIRA INTERAÇÃO
print(client.models.list())

CÉLULA 8.1

user_input = "Estou com febre e dor de garganta há dois dias."

messages.append({
    "role": "user",
    "content": user_input
})

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=messages,
    tools=tools
)

assistant_message = response.choices[0].message

messages.append(assistant_message)

print(assistant_message.content)


CÉLULA 9 — CHAMADA DE TOOL

tool_call = {
    "especialidade": "Clínico Geral",
    "urgencia": "baixa"
}

resultado = agendar_teleconsulta(
    especialidade=tool_call["especialidade"],
    urgencia=tool_call["urgencia"]
)
print(resultado)


CÉLULA 10 — SEGUNDO TURNO
user_input_2 = "Também estou com tosse leve."

messages.append({
    "role": "user",
    "content": user_input_2
})

response_2 = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=messages
)

assistant_message_2 = response_2.choices[0].message

messages.append(assistant_message_2)

print(assistant_message_2.content)


















