### 2. Diagrama Visual (UML)

```mermaid
flowchart LR
    %% Definindo os Atores
    Professor(["👨‍🏫 Professor"])
    Atendente(["💁 Atendente"])
    Administrador(["⚙️ Administrador"])

    %% Definindo os limites do sistema (Plataforma GAC)
    subgraph Sistema [Plataforma GAC - Gestão de Ativos]
        direction TB
        UC1([Consultar Disponibilidade])
        UC2([Retirar Equipamento via QR/NFC])
        UC3([Assinar Termo Digital])
        UC4([Registrar Devolução])
        UC5([Preencher Checklist Técnico])
        UC6([Registrar Avaria / Defeito])
        UC7([Cadastrar Novo Equipamento])
        UC8([Gerar Relatórios Gerenciais])
    end

    %% Conectando Atores aos Casos de Uso principais
    Professor --- UC1
    Professor --- UC2
    Atendente --- UC4
    Administrador --- UC7
    Administrador --- UC8

    %% Relacionamentos Include (Obrigatório) - Seta vai do base para o incluído
    UC2 -. "<<include>>" .-> UC3
    UC4 -. "<<include>>" .-> UC5

    %% Relacionamento Extend (Opcional) - Seta vai do opcional para o base
    UC6 -. "<<extend>>" .-> UC4
