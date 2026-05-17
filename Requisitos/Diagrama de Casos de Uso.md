### Diagrama de Casos de Uso (MCU) - Sistema GAC

#### 1. Objetivo
Apresentar a modelagem funcional do sistema GAC sob a perspectiva do usuário, mapeando os atores, suas ações e os relacionamentos de inclusão obrigatória.

#### 2. Diagrama Visual (UML)

```mermaid
flowchart LR
    %% Definição dos Atores (Bonecos)
    Prof(("🧑‍🏫 Professor\n(Ator)"))
    Atend(("👨‍💼 Atendente do CCT\n(Ator)"))
    Admin(("⚙️ Administrador\n(Ator)"))

    %% Fronteira do Sistema GAC
    subgraph Sistema GAC [Plataforma GAC - Gestão de Ativos]
        direction TB
        UC1([Consultar Disponibilidade])
        UC2([Retirar Equipamento via QR/NFC])
        UC3([Assinar Termo Digital])
        UC4([Registrar Devolução])
        UC5([Preencher Checklist Técnico])
        UC6([Cadastrar Novo Equipamento])
        UC7([Gerar Relatórios Gerenciais])
    end

    %% Relacionamentos do Professor
    Prof ===> UC1
    Prof ===> UC2
    UC2 -. "<<include>>\n(Obriga)" .-> UC3

    %% Relacionamentos do Atendente
    Atend ===> UC1
    Atend ===> UC4
    UC4 -. "<<include>>\n(Obriga)" .-> UC5

    %% Relacionamentos do Administrador
    Admin ===> UC6
    Admin ===> UC7

***
