### Diagrama de Casos de Uso (UML) - Visão Detalhada

```mermaid
flowchart LR
    %% Definindo os Atores
    Prof(["👨‍🏫 Professor"])
    Atend(["💁 Atendente"])
    Admin(["⚙️ Administrador"])
    Sis(["🤖 Sistema (Automático)"])

    %% Definindo os limites do sistema (Plataforma GAC)
    subgraph Sistema [Plataforma GAC - Ciclo de Vida Digital]
        direction TB
        
        %% Casos de Uso do Professor
        UC1([Consultar Disponibilidade])
        UC2([Reservar Equipamento])
        UC3([Coletar/Retirar via QR/NFC])
        UC4([Assinar Termo Digital])
        
        %% Casos de Uso do Atendente
        UC5([Registrar Devolução])
        UC6([Preencher Checklist Técnico])
        UC7([Registrar Avaria / Defeito])
        
        %% Casos de Uso do Administrador
        UC8([Cadastrar Novo Equipamento])
        UC9([Agendar Manutenção])
        UC10([Gerar Relatórios e Auditoria])
        
        %% Casos de Uso Automáticos
        UC11([Disparar Alertas de Atraso])
    end

    %% Conectando Atores aos Casos de Uso
    Prof --- UC1
    Prof --- UC2
    Prof --- UC3
    
    Atend --- UC5
    
    Admin --- UC8
    Admin --- UC9
    Admin --- UC10
    
    Sis --- UC11

    %% Relacionamentos Include (Obrigatório)
    UC2 -.->|«include»| UC1
    UC3 -.->|«include»| UC4
    UC5 -.->|«include»| UC6

    %% Relacionamentos Extend (Opcional)
    UC7 -.->|«extend»| UC5
    UC9 -.->|«extend»| UC7

### O que mudou e como explicar isso para o professor:

Se o seu professor perguntar sobre as novidades do diagrama, você pode justificar usando os próprios tópicos da visão do projeto de vocês:

*   **A Inclusão da Reserva:** Antes da **"Retirada Ágil"** [2], o professor agora tem o Caso de Uso `Reservar Equipamento`. Note que coloquei uma seta pontilhada `«include»` apontando para `Consultar Disponibilidade`. *Explicação:* O sistema obriga o professor a checar se o projetor está livre antes de deixar ele confirmar a reserva.
*   **O Caminho da Manutenção:** Nas regras de negócio, o CCT precisa de **"agendamento de manutenções preventivas"** [2]. O Administrador agora tem acesso direto a isso. Além disso, coloquei um `«extend»` da *Avaria* para a *Manutenção*. *Explicação:* Se o atendente registrar que o projetor voltou com a lente quebrada na devolução, o sistema abre a opção de já mandar esse equipamento direto para a manutenção.
*   **O Ator "Sistema Automático":** Adicionei o robozinho para representar os **"Alertas e Notificações Automáticas"** [1]. *Explicação:* Não é uma pessoa que fica mandando mensagem de cobrança; é o próprio sistema que roda em segundo plano e dispara os avisos de atraso para os professores e para o painel do CCT.
