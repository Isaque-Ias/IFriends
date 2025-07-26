# Casos de Uso

## Caso de Uso: CDU001 - Postar Conteúdo

**Ator principal:** Servidor ou estudante autenticado

**Objetivo:** Permitir o usuário de postar mensagens dentro da comunidade

**Pré-condições:**
- O usuário deve estar autenticado no sistema.
- O usuário está na tela inicial do aplicativo.

**Pós-condições:**
- O post do usuário é exibido no topo do feed da página.

### Fluxo Principal

1. O usuário acessa a aba de comunidade.
2. O usuário seleciona o botão "Postar".
3. O sistema exibe a interface de postagem com um campo de texto e opções.
4. O usuário digita o conteúdo do post.
5. O usuário seleciona o botão de "Enviar".
6. O sistema valida o texto.
7. O sistema publica o post dentro da comunidade.
8. O usuário é redirecionado para a tela inicial com uma confirmação de sucesso.

---

### Fluxo Alternativo - A1: Postar foto

- Início: Passo 4
- Condições: O usuário seleciona o botão "Fotos".
- Ações:
    1. O sistema exibe a interface para buscar uma foto dentro da galeria do dispositivo do usuário.
    2. O usuário retribui uma imagem.
    3. O sistema valida a imagem.
    4. Continua no passo 6.

---

### Fluxo de Exceção - E1: Conteúdo vazio

- Início: Passo 6
- Condição: Campo de texto está vazio.
- Ações: 
    1. O sistema exibe a mensagem de erro ("O conteúdo não pode estar vazio").
    2. Retorna ao passo 3.

---

### Fluxo de Exceção - E2: Falha na conexão

- Início: Passo 6
- Condição: O cliente não foi capaz de estabelecer a conexão com o servidor
- Ações:
    1. O sistema exibe a mensagem de erro ("Não foi possível publicar o post, tente novamente mais tarde.")
    2. Retorna ao passo 1.

---

## Caso de Uso: CDU002 - Participar de um evento

**Ator principal:** Servidor, estudante ou público externo

**Objetivo:** Permitir o usuário de participar de um evento dentro do IFRN

**Pré-condições:**
- O usuário deve estar autenticado no sistema.
- O usuário está na tela de eventos do aplicativo.
- O evento deve estar aberto para inscrições.

**Pós-condições:**
- A aba de "Eventos que participo" deverá ser atualizada.
- O sistema deve cadastrar a participação do usuário no evento.

### Fluxo Principal

1. O usuário acessa a aba de eventos.
2. O usuário seleciona um evento.
3. O usuário seleciona a seção de inscrições.
4. O sistema exibe a interface de cadastro para o evento.
5. O usuário preenche o formulário com seus dados pessoais.
6. O usuário seleciona o botão de confirmação da inscrição.
7. O sistema valida os dados fornecidos.
8. O usuário é redirecionado à aba de eventos.

---

### Fluxo Alternativo - A1: O usuário cancela a inscrição

- Início: Passo 5
- Condições: O usuário seleciona o botão "Cancelar".
- Ações:
    1. O sistema exibe a mensagem ("Inscrição cancelada")
    2. Continua no passo 2.

---

### Fluxo de Exceção - E1: Limite de inscrições durante cadastro

- Início: Passo 6
- Condição: O limite de inscrições é esgotado durante a inscrição
- Ações: 
    1. O sistema exibe a mensagem de erro ("Não há mais vagas disponíveis").
    2. Retorna ao passo 2.

---

### Fluxo de Exceção - E2: Dados inválidos

- Início: Passo 7
- Condição: Os dados são inválidos
- Ações: 
    1. O sistema exibe a mensagem de erro ("Os dados são inválidos. Por favor, preencha os campos corretamente.").
    2. Retorna ao passo 4.

---

### Fluxo de Exceção - E3: Falha na conexão

- Início: Passo 7
- Condição: O cliente não foi capaz de estabelecer a conexão com o servidor
- Ações:
    1. O sistema exibe a mensagem de erro ("Não foi possível realizar o cadastro, tente novamente mais tarde.")
    2. Retorna ao passo 2.

---

## Caso de Uso: CDU003 - Apoio Acadêmico

**Ator principal:** Estudante

**Ator secundário:** Chatbot

**Objetivo:** Solucionar o problema de um usuário dentro do sistema

**Pré-condições:**
- O usuário deve estar autenticado no sistema.
- O usuário está na aba de "mIFriend" do aplicativo.

**Pós-condições:**
- O chatbot deve exibir uma resposta em texto e/ou um fluxograma de solução.

### Fluxo Principal

1. O usuário acessa a aba "mIFriend".
2. O sistema exibe uma interface com um chatbot dentro de uma nova sessão.
3. O chatbot se introduz perguntando o nome do usuário.
4. O usuário digita seu nome.
5. O chatbot valida o nome.
6. O chatbot pergunta como pode ajudar o usuário.
7. O usuário descreve o seu problema.
8. O chatbot busca uma resposta dentro do sistema baseada na descrição.
9. O chatbot responde o usuário com um texto e, opcionalmente, um fluxograma.
10. O chatbot pergunta se o usuário ainda possui dúvidas.
11. O usuário responde que sim.
12. Retorna ao passo 6.

---

### Fluxo Alternativo - A1: O problema não está cadastrado

- Início: Passo 8
- Condições: O chatbot não encontra uma resposta com um nível de confiança satisfatório dentro do sistema.
- Ações:
    1. O chatbot informa que não foi capaz de encontrar a solução.
    2. O chatbot sugere o usuário de cadastrar o seu problema dentro do sistema.
    3. O usuário aceita a sugestão.
    4. O sistema é atualizado.
    5. Retorna ao passo 6.

---

### Fluxo Alternativo - A2: O responde que não possui dúvidas

- Início: Passo 11
- Condições: O usuário responde que não.
- Ação: O chatbot finalizará a sessão.

---

### Fluxo de Exceção - E1: Nome inválido

- Início: Passo 5
- Condição: O nome é composto por letras ou é muito curto.
- Ações: 
    1. O sistema informa que o nome do usuário é inválido e pede por uma resposta satisfatória.
    2. Retorna ao passo 4.

---

### Fluxo de Exceção - E2: Falha na conexão

- Início: Passo 8
- Condição: O chatbot não foi capaz de estabelecer a conexão com o servidor
- Ações:
    1. O sistema exibe a mensagem de erro ("Não foi possível encontrar uma resposta para a dúvida. Por favor, volte mais tarde.")
    2. A sessão é finalizada.