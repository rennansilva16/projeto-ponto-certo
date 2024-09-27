# Anotações Gerais sobre o Projeto

## Descrição do projeto.
- Desenvolver um aplicativo móvel Android que atenda aos seguintes
requisitos utilizando tecnologias nativas (preferencialmente Kotlin ou Java). O
aplicativo deverá incluir funcionalidades de CRUD (Create, Read, Update,
Delete), utilizando o SQLite para operações de persistência de dados, e possuir
ao menos três telas distintas.

- projeto de desenvolvimento de uma plataforma online para o controle de horas trabalhadas pelos colaboradores da empresa “Consultmais”
- Adicionar ponto
    - Entrada
    - Saída
    - Solicitar Ajuste
- Administrador
    - Cadastrar Usuário
    - Remover Usuário
    - Autorizar Ajuste
    - Negar Ajuste
    - Notificar usuário ao responder solicitação de ajuste
    - Gerar relatório
- Relatório
    - Exibir tabela contendo:
        - Nome do colaborador
        - Horas extras
        - Horas faltantes
        - Horas trabalhadas
- Histórico de Registro
  - Exebir tela contendo: 
    - Tabela com:
      - Dia do registro
      - Entrada
      - Saída
      - Alterar registro

## Passo a passo do Desenvolvimento
Passo a Passo para Desenvolver o Aplicativo de Registro de Ponto

### 1. **Configuração Inicial do Projeto**
- **Instalar e Configurar o Android Studio**:
  - Baixar e instalar a versão mais recente do Android Studio.
  - Criar um novo projeto Android com a opção "Empty Activity".
  - Configurar o nome do projeto e o pacote (ex: `com.exemplo.registrodeponto`).

### 2. **Criar o Banco de Dados SQLite**
- **Definir as Tabelas e Estrutura do Banco de Dados**:
  - Tabela `Usuarios` com campos: `id`, `nomeUsuario`, `senha`.
  - Tabela `Registros` com campos: `id`, `usuarioId` (referência ao usuário), `entrada`, `saida`.
  - Tabela `Solicitacoes` com campos: `id`, `usuarioId` (referência ao usuário), `dataRegistro`, `tipo` (ex: entrada ou saída), `novaHora`, `status` (ex: pendente, aprovado, recusado).
- **Implementar a Classe de Banco de Dados**:
  - Criar uma classe que herda de `SQLiteOpenHelper`.
  - Definir métodos para criar e atualizar as tabelas (`onCreate()` e `onUpgrade()`).
  - Implementar métodos CRUD (Create, Read, Update, Delete) para gerenciar dados.
  - Implementar métodos específicos para gerenciar solicitações de alteração.

### 3. **Criar a Tela de Login**
- **Criar a Interface de Login (XML)**:
  - Layout com campos para inserir nome de usuário e senha.
  - Botão de login.
- **Implementar a Lógica de Login**:
  - Validar nome de usuário e senha usando o banco de dados.
  - Se válido, redirecionar para a tela de registro de ponto.
  - Exibir mensagens de erro caso as credenciais estejam incorretas.

### 4. **Criar a Tela de Registro de Ponto**
- **Criar a Interface de Registro de Ponto (XML)**:
  - Botões para registrar entrada e saída.
  - Botão para acessar o histórico de registros.
- **Implementar a Lógica de Registro**:
  - Registrar a hora de entrada e saída no banco de dados.
  - Verificar se o usuário já registrou entrada antes de permitir registrar a saída.

### 5. **Criar a Tela de Histórico de Registro de Ponto**
- **Criar a Interface de Histórico (XML)**:
  - Lista de registros com data e hora de entrada e saída.
  - Opção de editar os registros, se necessário.
- **Implementar a Lógica do Histórico**:
  - Consultar e exibir registros do banco de dados.
  - Permitir que o usuário altere registros existentes e crie solicitações de alteração.

### 6. **Criar a Tela do Administrador**
- **Criar a Interface do Administrador (XML)**:
  - Botões para acessar a tela de relatório, adicionar ou excluir usuários.
  - Listagem de solicitações de alteração de registro (pendentes).
  - Botões para aprovar ou recusar solicitações de alteração.
- **Implementar a Lógica do Administrador**:
  - Verificar permissões para acessar a tela.
  - Funções para gerenciar usuários e registros.
  - **Implementar Função de Aprovar/Recusar Solicitação**:
    - Ao clicar em "Aprovar" ou "Recusar", atualizar o status da solicitação no banco de dados.
    - Registrar a alteração diretamente no registro de ponto se aprovada.
    - Enviar uma notificação ao usuário correspondente informando sobre a aprovação ou recusa.

### 7. **Criar a Tela de Relatório**
- **Criar a Interface de Relatório (XML)**:
  - Tabela com dados dos usuários: nome, horas extras, horas faltantes, horas trabalhadas.
- **Implementar a Lógica do Relatório**:
  - Consultar dados de todos os usuários no banco de dados.
  - Mostrar os dados de forma organizada e permitir exportação se necessário.

---

### **Envio de Notificações**

#### 1. **Implementar o Sistema de Notificações**:
  - **Uso de `NotificationManager`**:
    - Configurar o `NotificationManager` no Android Studio para gerenciar as notificações.
  - **Criar Canal de Notificação**:
    - Definir um canal de notificação com um nome e descrição (necessário para Android 8.0 e superior).
  - **Configurar Notificações**:
    - Criar uma notificação personalizada com título e mensagem.
  - **Enviar Notificação**:
    - Ao aprovar ou recusar uma solicitação na **Tela do Administrador**, o sistema deve enviar a notificação ao usuário específico com a mensagem apropriada (ex: "Sua solicitação de alteração foi aprovada" ou "Sua solicitação de alteração foi recusada").

---

### 
## Autores
## Instruções de instalação.
## Explicação detalhada das funcionalidades desenvolvidas.