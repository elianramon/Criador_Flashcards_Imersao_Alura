# Flashcards: O Poder da Repetição Espaçada no Estudo Contínuo  

Os **flashcards** são uma ferramenta de aprendizagem baseada na **repetição espaçada**, metodologia cientificamente comprovada para fixação de conteúdo a longo prazo. Seu princípio é simples:  

1. **Ciclos de Revisão**: O conteúdo é revisado em intervalos crescentes (ex.: 1 dia, 3 dias, 1 semana), aproveitando o "efeito de espaçamento" da memória.  

2. **Ativação Rápida**: Cada card traz uma **pergunta objetiva** (frente) e uma **resposta concisa** (verso), estimulando a **recuperação ativa** da informação – processo que fortalece conexões neurais.  

3. **Eficiência Adaptativa**: Ferramentas digitais (como Anki ou Quizlet) usam algoritmos para priorizar cards com maior dificuldade, otimizando o tempo de estudo.

   ![image](https://github.com/user-attachments/assets/802a633f-277b-4d50-bdc8-bb2fbe769634)
------
Essa imagem representa a curva de esquecimento e retenção de Hermann Ebbinghaus, o qual foi o primeiro autor na psicologia a desenvolver testes de inteligência. 

Mais informações sobre ele em: [texto do link](https://pt.wikipedia.org/wiki/Hermann_Ebbinghaus).
Pensando nisso, aplicativos como ANKI trabalham na teoria de Ebbinghaus, sendo uma boa ferramenta para estudantes e, em especial, concurseiros. 

A partir deste ponto, será construida a programação referente a criação de Flashcards.

## IMPORTANTE

PARA UTILIZAZAR O CÓDIGO, VOCÊ PRECISA DE UMA API KEY DO GEMINI (https://www.youtube.com/watch?v=o8iyrtQyrZM) -> TUTORIAL.
DICA: USE O GOOGLE COLAB, SIGA O CÓDIGO.

# Lógica

## Criação dos Agentes


Serão 4 Agentes

# --- Agente 1: Buscador de Notícias (gemini-2.0-flash)--- #
Recebe duas informações: **Assunto para pesquisar** e **Banca Organizadora**, as quais são os motores iniciais de busca na rede.

```
topico = input(" Por favor, digite o ASSUNTO sobre o qual você quer estudar: ")  # Sistema Financeiro Nacional
banca = input(" Por favor, digite a BANCA organizadora: ")  # Cesgranrio
```

---------------------

# --- Agente 2: Especificador de Assuntos (gemini-2.0-flash) --- #
Peguntará qual será o sub-assunto para pesquisar de forma mais específica, afinal um assunto possuei diversos sub-assuntos.

--------

# --- Agente 3: Criador de Flashcards (gemini-2.5-flash-preview) --- #
Fomulará as perguntas e respostas com base no assunto especificado do Agente 2 (número de perguntas é defido aqui).

```
######################################
# --- Agente 3: Criador de Flashcards --- #
######################################
def agente_criador(topico, plano_de_post):
    criador = Agent(
        name="agente_criador",
        model="gemini-2.5-flash-preview-04-17",
        instruction="""
            Você é um criador especializado em criar flahscards para concurseiros. Utilize o texto fornecido no assuntos 
            específico e, com base nisso, crie 10 flashcards de estudo sobre o tema fornecido.

            FORMATO DE SAÍDA EXIGIDO:
            1. Duas tabelas lado a lado (uma de perguntas e outra de respostas correspondentes)
            2. Cada tabela deve ter exatamente N linhas (uma por flashcard) # AQUI
            3. As perguntas devem ser diretas e testarem conhecimento objetivo
            4. As respostas devem ser concisas (máximo 2 linhas)

            EXEMPLO DE FORMATO:
            | Perguntas            | Respostas             |
            |----------------------|-----------------------|
            | Qual o objetivo...?  | Regular o sistema...  |
            | Quando foi criado...?| 31/12/1964...         |

           """,
        description="Agente criador de posts engajadores para Instagram"
    )
    entrada_do_agente_criador = f"Tópico: {topico}\nPlano de post: {plano_de_post}"
    # Executa o agente
    rascunho = call_agent(criador, entrada_do_agente_criador)
    return rascunho
```


----

# --- Agente 4: Revisor de Qualidade (gemini-2.5-flash-preview) ---  #
É especializado em questões e em flashcards, ele analiza as perguntas e respostas, caso estejam certas, prossegem para o fim. Em caso contrário, ele mesmo conserta.

------
Ao final do processo, um link é sujerido para o AnkiPro (apesar do nome, é gratuito!). Link: https://ankipro.net/decks, faça login, selecione "importar" e depois, "importa CSV".

![image](https://github.com/user-attachments/assets/227df805-d584-4544-b3a6-cfd2940f14b5)
A página irá abrir neste formato, onde basta copiar e colar as perguntas e respostas dadas pelo Agente 4. Não precisa alterar as opções no Anki. 

![image](https://github.com/user-attachments/assets/5e2edfe6-544a-43b2-9ca5-dc61632e78d9)
(AQUI VOCÊ COPIA).
![image](https://github.com/user-attachments/assets/c6d9eed0-975e-466a-ad45-befc860ac4b4)
(AQUI VOCÊ COLA).
Lembre-se de dar um nome para o novo deck que você estará importantado, assim que nomea-lo, o botão é liberado. Basta importar.
Abaixo, um exemplo de como será a visão após importar as questões.

![image](https://github.com/user-attachments/assets/7e4782d1-54fa-49a7-bdce-f5aea3b60a26)

![image](https://github.com/user-attachments/assets/e2d411b8-8db7-4823-92f8-47ac70fe1714)

🚀 Obrigado por confiar! Boa prova, acredite em você! 🚀
