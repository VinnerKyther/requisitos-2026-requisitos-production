### Diagrama de Casos de Uso (MCU) - Sistema GAC

#### 1. Objetivo
Apresentar a modelagem funcional do sistema GAC sob a perspectiva do usuário, mapeando os atores, suas ações e os relacionamentos obrigatórios (`<<include>>`) e opcionais (`<<extend>>`).

#### 2. Diagrama Visual (UML)

```mermaid
flowchart LR
    %% Definição dos Atores (Bonecos)
    Prof(("🧑‍🏫 Professor\n(Ator)"))
    Atend(("👨‍💼 Atendente\n(Ator)"))
    Admin(("⚙️ Administrador\n(Ator)"))

    %% Fronteira do Sistema GAC
    subgraph Sistema GAC [Plataforma GAC - Gestão de Ativos]
        direction TB
        UC1([Consultar Disponibilidade])
        UC2([Retirar Equipamento via QR/NFC])
        UC3([Assinar Termo Digital])
        
        UC4([Registrar Devolução])
        UC5([Preencher Checklist Técnico])
        UC5_1([Registrar Avaria / Defeito])
        
        UC6([Cadastrar Novo Equipamento])
        UC7([Gerar Relatórios Gerenciais])
    end

    %% Relacionamentos do Professor
    Prof ===> UC1
    Prof ===> UC2
    %% Include: Assinar o termo é OBRIGATÓRIO para retirar
    UC2 -. "<<include>>" .-> UC3

    %% Relacionamentos do Atendente
    Atend ===> UC1
    Atend ===> UC4
    %% Include: Preencher o checklist é OBRIGATÓRIO na devolução
    UC4 -. "<<include>>" .-> UC5
    %% Extend: Registrar avaria é OPCIONAL (só se estiver quebrado)
    UC5_1 -. "<<extend>>" .-> UC5

    %% Relacionamentos do Administrador
    Admin ===> UC6
    Admin ===> UC7
