# Flashcards com IA: O Poder da Repetição Espaçada no Estudo Contínuo para Concursos

É com alegria que apresento meu projeto da Imersão Alura com Google, espero que aproveite para ter novas ideias e descubra uma amostra do poder do Gemini IA. 

## Contextualização
Pensando no mundo dos concursos públicos, o estudo contínuo é fundamental para obter uma excelente nota na prova dos seus sonhos. Nesse sentido, o **Flashcard** possibilita um estudo de revisão inteligente, defendido por Hermann Ebbinghaus, o primeiro autor na psicologia a desenvolver testes de inteligência, ao possibilitar que o conteúdo seja revisado conforme a dificuldade indicada pelo usuário. Com isso, aplicativos como o Anki, Quizlet, Tinycards e Cram se tornam aliados dos concurseiros. Mas nem tudo são flores, o tempo de estudo nem sempre é confortável e fazer os próprios flashcards demandam certo tempo...

![image](https://github.com/user-attachments/assets/802a633f-277b-4d50-bdc8-bb2fbe769634)

**Então porque não deixar esse processo mais rápido?** 

Pensando nisso, desenvolvi um auxiliador para criação de flashcards a partir de duas perguntas iniciais: Qual assunto deseja pesquisar e de qual banca; e uma pergunta derivada da primeira pesquisa. Com isso, usando agentes do Gemini IA, foi possível chegar no resultado prometido. 

A partir deste ponto, será construida a lógica de programação referente a criação de Flashcards.

## IMPORTANTE

Para utizar o código você precisa:
- UMA API KEY DO GEMINI (https://www.youtube.com/watch?v=o8iyrtQyrZM) -> Tutorial;
- USE O GOOGLE COLAB (copie meu código);
- FAÇA UMA CÓPIA DO MEU COLAB.

## Lógica
A lógica dos agentes é o uso de chats em conjuntos que refinam a resposta final, como uma equipe de trabalho repassando a atividade adiante até sua conclusão.

### Criação dos 4 Agentes

#  Agente 1: Buscador de Notícias Sobre Assuntos (gemini-2.0-flash) #
Recebe duas informações: **Assunto para pesquisar** e **Banca Organizadora**, as quais são os motores iniciais de busca na rede.

Ele é especializado em pesquisar sobre os pontos mais cobrados de determinada banca para aquele assunto que o usuário indicou.

```
topico = input(" Por favor, digite o ASSUNTO sobre o qual você quer estudar: ")  # Ex.: Sistema Financeiro Nacional
banca = input(" Por favor, digite a BANCA organizadora: ")  # Ex.: Cesgranrio
```

---------------------

# Agente 2: Especificador de Assuntos (gemini-2.0-flash) #
Peguntará qual será o sub-assunto para pesquisar.

Os pontos relevantes apontados pelo Agente 1 seram repassados para o Agente 2, que é especializado em pesquisar um só sub-assunto escolhido pelo usuário com base nas respostas do Agente 1.

--------

# Agente 3: Criador de Flashcards (gemini-2.5-flash-preview) #
Formula as perguntas e respostas com base no assunto especificado do Agente 2.

A resposta do Agente 2 é repassada ao 3, o qual é ainda mais especializado e usa uma versão Gemini superior. Ele vai elaborar as perguntas e respostas com base no texto do Agente 2. (número de perguntas é defido aqui).

-----

# Agente 4: Revisor de Qualidade (gemini-2.5-flash-preview) #
É especializado em questões e em Flashcards, ele analiza as perguntas e respostas, caso corretas, prossege para o fim. Em caso contrário, ele mesmo conserta. Ele verifica a formatação final.

Ao final do processo, um link é sujerido para o AnkiPro (apesar do nome, é gratuito!). Link: https://ankipro.net/decks, faça login, selecione "importar" e depois, "importa CSV".

### O que fazer com as respostas?
- Abra o link sugerido.
- Clique em "importar ---> CSV".

![image](https://github.com/user-attachments/assets/227df805-d584-4544-b3a6-cfd2940f14b5)

A página irá abrir neste formato, onde basta copiar e colar as perguntas e respostas dadas pelo Agente 4. Não precisa alterar as opções no Anki. 
- Copie a tabela.
  
![image](https://github.com/user-attachments/assets/5e2edfe6-544a-43b2-9ca5-dc61632e78d9)

- Cole a tabela na área.
  
![image](https://github.com/user-attachments/assets/c6d9eed0-975e-466a-ad45-befc860ac4b4)

Lembre-se de dar um nome para o novo deck que você estará importantado, assim que nomea-lo, o botão é liberado. Basta importar.

- Nomeie a novo deck.
  
### Visualização

Abaixo, um exemplo de como será a visão após importar as questões.
  
![image](https://github.com/user-attachments/assets/7e4782d1-54fa-49a7-bdce-f5aea3b60a26)

![image](https://github.com/user-attachments/assets/e2d411b8-8db7-4823-92f8-47ac70fe1714)

🚀 Obrigado por confiar! Boa prova, acredite em você! 🚀
