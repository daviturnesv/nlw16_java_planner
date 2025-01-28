**PLANN.ER**

Plann.er é uma aplicação desenvolvida em Java utilizando Spring Boot para ajudar usuários a planejar e organizar viagens de maneira prática e colaborativa. A aplicação permite gerenciar atividades, compartilhar links relevantes e convidar participantes para colaborar no planejamento, oferecendo uma interface REST para interação com o backend.


**🚀 Funcionalidades**


**📋 Organização de Viagens**

Criação de viagens com informações como:

Destino

Datas de início e término

Nome e e-mail do organizador

Lista de convidados por e-mail

Confirmação de viagem através de e-mails automáticos enviados aos participantes.


**🗓️ Gerenciamento de Atividades**

Adicione atividades à viagem, especificando:

Título

Data e horário

Consulte as atividades planejadas para cada viagem.


**🔗 Compartilhamento de Links**

Adicione e gerencie links relevantes à viagem, como:

Reservas de hospedagem

Locais a visitar

Outras informações úteis.


**👥 Gestão de Participantes**

Convide participantes através do e-mail.

Confirmação de presença via link enviado automaticamente.

Gerencie e visualize a lista de participantes confirmados.


**🛠️ Tecnologias Utilizadas**

Java 17

Spring Boot 3.x:

Spring Web: para construção de APIs REST.

Spring Data JPA: para integração com banco de dados.

H2 Database: banco de dados em memória.

Flyway: controle de versão do banco de dados.

Lombok: redução de código boilerplate.

Jakarta Persistence API: mapeamento de entidades JPA.

Spring Dev Tools: aceleração do desenvolvimento com hot-reload.

Postman (ou similar): para testes das APIs.


**🧩 Estrutura da Aplicação**

A aplicação segue uma estrutura modular e bem definida:

**Pacotes principais**:

trip: gerenciamento de viagens.

participant: gerenciamento de participantes.

activity: gerenciamento de atividades.

link: gerenciamento de links associados às viagens.

**Camadas**:

Controller: Responsável por expor os endpoints REST e receber as requisições HTTP.

**Ex.:** TripController, ParticipantController.

Service: Contém a lógica de negócios.

**Ex.:** ActivityService, LinkService.

Repository: Interface para comunicação com o banco de dados via Spring Data JPA.

**Ex.:** TripRepository, ParticipantRepository.

Entity: Representações das tabelas no banco de dados, utilizando JPA.

**Ex.:** Trip, Participant.


**Banco de Dados**

**Tabelas principais:**

trips: armazena informações sobre as viagens.

participants: armazena os participantes de cada viagem.

activities: armazena as atividades planejadas.

links: armazena os links úteis associados às viagens.

Migrações gerenciadas pelo Flyway, com scripts SQL para criação e atualização das tabelas.


**📝 Como Utilizar a Aplicação**


**1️⃣ Inicie o servidor**

Execute a aplicação localmente ou utilize um ambiente de execução compatível como Docker.


**2️⃣ Endpoints Disponíveis**

**Viagens**

Criar viagem

    POST /trips


json

    {
      "destination": "Rio de Janeiro",
      "starts_at": "2025-02-01T10:00:00",
      "ends_at": "2025-02-07T22:00:00",
      "emails_to_invite": ["convidado1@email.com", "convidado2@email.com"],
      "owner_name": "João Silva",
      "owner_email": "joao@email.com"
}

**Resposta:**

json

    {
      "tripId": "UUID_da_viagem_criada"
    }

**Consultar detalhes da viagem**

    GET /trips/{tripId}


**Atualizar viagem**

    PUT /trips/{tripId}


**Confirmar viagem**

    GET /trips/{tripId}/confirm


**Participantes**

Convidar participante

    POST /trips/{tripId}/invite

json

    {
      "email": "novo_convidado@email.com"
    }

**Confirmar participação**

    POST /participants/{participantId}/confirm


**Consultar participantes**

    GET /trips/{tripId}/participants


**Atividades**

**Adicionar atividade**

    POST /trips/{tripId}/activities


json

    {
      "title": "Passeio na praia",
      "occurs_at": "2025-02-03T15:00:00"
    }

**Consultar atividades da viagem**

    GET /trips/{tripId}/activities


**Links**

**Adicionar link**

    POST /trips/{tripId}/links


json

    {
      "title": "Reserva do Hotel",
      "url": "https://www.reservas.com/hotel"
    }

**Consultar links da viagem**

    GET /trips/{tripId}/links


**3️⃣ Fluxo de Exemplo**

O organizador cria uma viagem pelo endpoint POST /trips.

Exemplo:
![image](https://github.com/user-attachments/assets/62ea93c3-0a28-4c6c-b009-86bb5924c94e)


Convidados recebem e-mails e confirmam sua presença.

Exemplo:
![image](https://github.com/user-attachments/assets/846e393c-052e-4819-8b6d-dece71ea5ca6)


O organizador adiciona atividades e links úteis através dos respectivos endpoints.

Exemplo:
![image](https://github.com/user-attachments/assets/b6d59dd1-47f5-4f18-a480-c0bacfe85d85)
![image](https://github.com/user-attachments/assets/c5c9840a-6fc4-4be2-8954-464448f28f6f)

Todos os participantes podem visualizar as informações e colaborar no planejamento.4

Exemplo:
![image](https://github.com/user-attachments/assets/1e3199d0-dd15-401f-8c93-73f528e63613)
![image](https://github.com/user-attachments/assets/db9b6489-f102-474a-8b77-8aee0852fd17)
![image](https://github.com/user-attachments/assets/f87e9ac2-248a-4619-8877-de16a81bdcf0)


**🔍 Como Testar**

**Clone o repositório:**

bash

    git clone https://github.com/daviturnesv/nlw16_java_planner

    cd nlw16_java_planner

**Compile e execute:**

bash

    ./mvnw spring-boot:run

Teste os endpoints via Insomnia, Postman, cURL ou outra ferramenta similar.


🤝 Contribuindo

Contribuições são bem-vindas! Siga as etapas:

Crie um fork do repositório.

Faça suas alterações em uma branch.

Envie um Pull Request com uma descrição clara.

