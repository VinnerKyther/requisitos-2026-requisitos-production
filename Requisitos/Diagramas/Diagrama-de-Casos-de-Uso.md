flowchart LR
    %% Atores
    Prof(["👨‍🏫 Professor"])
    Atend(["💁 Atendente"])
    Admin(["⚙️ Administrador"])
    Sis(["🤖 Sistema (Auto)"])

    subgraph PlataformaGAC [Sistema GAC - Ciclo de Vida Digital]
        direction TB
        UC_Login([Autenticar Usuário / Login])
        UC1([Consultar Disponibilidade])
        UC1a([Solicitar Alerta])
        UC2([Reservar Equipamento])
        UC3([Retirar via QR/NFC])
        UC4([Transferir Equipamento])
        UC5([Assinar Termo Digital])
        UC6([Informar Sala de Destino])
        UC7([Registrar Devolução])
        UC8([Preencher Checklist Técnico])
        UC9([Registrar Avaria / Defeito])
        UC10([Cadastrar Novo Equipamento])
        UC11([Agendar Manutenção])
        UC12([Gerar Relatórios e Auditoria])
        UC13([Disparar Alertas Automáticos])
    end

    %% Herança
    Admin -.->|"<<herda>>"| Atend

    %% Associações Principais
    Prof --- UC_Login
    Atend --- UC_Login
    Admin --- UC_Login

    Prof --- UC1
    Prof --- UC2
    Prof --- UC3
    Prof --- UC4
    
    Atend --- UC1
    Atend --- UC7
    
    Admin --- UC10
    Admin --- UC11
    Admin --- UC12
    Sis --- UC13

    %% Dependências (Setas Pontilhadas)
    UC1a -.->|"<<extend>>"| UC1
    
    UC2 -.->|"<<include>>"| UC6
    UC3 -.->|"<<include>>"| UC6
    UC4 -.->|"<<include>>"| UC6
    
    UC3 -.->|"<<include>>"| UC5
    UC4 -.->|"<<include>>"| UC5

    UC7 -.->|"<<include>>"| UC8
    UC9 -.->|"<<extend>>"| UC7
    UC11 -.->|"<<extend>>"| UC9
