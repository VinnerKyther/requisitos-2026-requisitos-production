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

### 
