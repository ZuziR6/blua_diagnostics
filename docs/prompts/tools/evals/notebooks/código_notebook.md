LER EM MODO "CODE", SENÃO NÃO SERÁ POSSÍVEL COPIAR CORRETAMENTE


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

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=messages,
    tools=tools,
    tool_choice="auto"
)

assistant_message = response.choices[0].message
messages.append(assistant_message)

print("RESPOSTA:")
print(assistant_message.content)


CÉLULA 9 — CHAMADA DE TOOL

if assistant_message.tool_calls:
    for tool_call in assistant_message.tool_calls:
        if tool_call.function.name == "agendar_teleconsulta":
            args = json.loads(tool_call.function.arguments)

            resultado = agendar_teleconsulta(
                especialidade=args["especialidade"],
                urgencia=args["urgencia"]
            )

            print("TOOL EXECUTADA:")
            print(resultado)

CÉLULA 10 — SEGUNDO TURNO
user_input_2 = "Agora também estou com dor leve no corpo."

messages.append({"role": "user", "content": user_input_2})

response_2 = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=messages
)

print(response_2.choices[0].message.content)

















