### Diagrama de Casos de Uso (UML) - Visão Detalhada

```mermaid
fflowchart LR
    %% Atores da Esquerda
    Prof(["👨‍🏫 Professor"])
    Atend(["💁 Atendente"])

    subgraph Plataforma GAC [Sistema GAC - Ciclo de Vida Digital]
        direction TB
        
        %% Novo: Autenticação
        UC_Login([Autenticar Usuário / Login])

        %% Ações Base do Professor
        UC1([Consultar Disponibilidade])
        UC1a([Solicitar Alerta])
        UC2([Reservar Equipamento])
        UC3([Retirar via QR/NFC])
        UC4([Transferir Equipamento])
        
        %% Inclusões do Professor
        UC5([Assinar Termo Digital])
        UC6([Informar Sala de Destino])
        
        %% Ações Base e Extensões do Atendente
        UC7([Registrar Devolução])
        UC8([Preencher Checklist Técnico])
        UC9([Registrar Avaria / Defeito])
        
        %% Ações da Gestão e Sistema
        UC10([Cadastrar Novo Equipamento])
        UC11([Agendar Manutenção])
        UC12([Gerar Relatórios e Auditoria])
        UC13([Disparar Alertas Automáticos])
    end

    %% Atores da Direita
    Admin(["⚙️ Administrador"])
    Sis(["🤖 Sistema (Auto)"])

    %% Herança de Atores (O Admin herda as funções do Atendente)
    Admin -.->|«herda»| Atend

    %% Ligações Sólidas (Apenas Ações Principais)
    Prof --- UC_Login
    Atend --- UC_Login
    Admin --- UC_Login

    Prof --- UC1
    Prof --- UC2
    Prof --- UC3
    Prof --- UC4
    
    Atend --- UC1
    Atend --- UC7
    
    UC10 --- Admin
    UC11 --- Admin
    UC12 --- Admin
    UC13 --- Sis

    %% Dependências (Setas Pontilhadas)
    UC1a -.->|«extend»| UC1
    
    UC2 -.->|«include»| UC6
    UC3 -.->|«include»| UC6
    UC4 -.->|«include»| UC6
    
    UC3 -.->|«include»| UC5
    UC4 -.->|«include»| UC5

    UC7 -.->|«include»| UC8
    UC9 -.->|«extend»| UC7
    UC11 -.->|«extend»| UC9
```
