### Diagrama de Casos de Uso (UML) - Visão Detalhada

```mermaid
flowchart LR
    %% Atores da Interface Mobile (Esquerda)
    Prof(["👨‍🏫 Professor"])
    Atend(["💁 Atendente"])

    subgraph Sistema [Plataforma GAC - Ciclo de Vida Digital]
        direction TB
        
        %% Bloco de Consulta
        UC1([Consultar Disponibilidade])
        UC1a([Solicitar Alerta])
        
        %% Bloco de Ações e Inclusões separadas
        UC2([Reservar Equipamento])
        UC6([Informar Sala de Destino])
        
        UC3([Retirar via QR/NFC])
        UC5([Assinar Termo Digital])
        
        UC4([Transferir Equipamento])
        
        %% Bloco de Devolução
        UC7([Registrar Devolução])
        UC8([Preencher Checklist Técnico])
        UC9([Registrar Avaria / Defeito])
        
        %% Bloco de Gestão
        UC10([Cadastrar Novo Equipamento])
        UC11([Agendar Manutenção])
        UC12([Gerar Relatórios e Auditoria])
        
        %% Bloco de Automação
        UC13([Disparar Alertas Automáticos])
    end

    %% Atores da Interface Web e Robôs (Direita)
    Admin(["⚙️ Administrador (CCT)"])
    Sis(["🤖 Sistema (Automático)"])

    %% Conectando os Atores (LINHAS SÓLIDAS)
    Prof --- UC1
    Prof --- UC2
    Prof --- UC3
    Prof --- UC4
    
    %% O Atendente agora tem ligação VISUAL com todas as suas tarefas
    Atend --- UC1
    Atend --- UC7
    Atend --- UC8
    Atend --- UC9
    
    UC10 --- Admin
    UC11 --- Admin
    UC12 --- Admin
    UC13 --- Sis

    %% LIGAÇÕES SISTÊMICAS (Setas Pontilhadas)
    UC1a -.->|«extend»| UC1
    
    UC2 -.->|«include»| UC6
    UC3 -.->|«include»| UC5
    
    %% Setas secundárias
    UC3 -.->|«include»| UC6
    UC4 -.->|«include»| UC6
    UC4 -.->|«include»| UC5

    UC7 -.->|«include»| UC8
    UC9 -.->|«extend»| UC7
    UC11 -.->|«extend»| UC9
```
