## 1. Introdução

### 1.1 Propósito
Este documento tem como objetivo especificar os requisitos de software para o sistema de Gestão de Ativos do CCT (GAC). Ele detalha as funcionalidades, o comportamento do sistema, os perfis de usuários envolvidos e as restrições e regras de negócio, servindo como base formal para a fase de prototipação e posterior desenvolvimento da plataforma.

### 1.2 Escopo do Produto
O GAC é uma plataforma digital projetada para apoiar e rastrear o ciclo de vida de ativos críticos (como projetores, chaves e acessórios) do Centro de Ciências Tecnológicas (CCT) da Unifor. O sistema substituirá o atual controle manual (baseado em anotações em papel e planilhas informais) por uma solução moderna integrada a identificadores físicos (NFC e/ou QR Code). O GAC garantirá a rastreabilidade total, identificando de forma segura quem retirou um ativo, quando deve ser devolvido e em qual estado de conservação foi entregue, mitigando perdas e erros de registro.

### 1.3 Definições, Acrônimos e Abreviações
*   **GAC:** Gestão de Ativos do CCT.
*   **CCT:** Centro de Ciências Tecnológicas.
*   **NFC (Near Field Communication):** Tecnologia de comunicação sem fio de curto alcance usada para identificação dos equipamentos por aproximação de smartphones.
*   **QR Code:** Código de barras bidimensional usado para escanear a etiqueta do ativo e identificá-lo no sistema.
*   **WIP (Work in Progress):** Trabalho em progresso, métrica utilizada pela equipe de desenvolvimento para limitar tarefas e melhorar o fluxo de entrega.

### 1.4 Visão Geral do Documento
Este documento está estruturado em três partes principais: A Seção 1 introduz o projeto; a Seção 2 apresenta uma descrição geral do sistema, o perfil dos usuários e suas principais funções; a Seção 3 detalha tecnicamente os requisitos funcionais, não funcionais e as regras de negócio para a construção do software.

---

## 2. Descrição Geral

### 2.1 Perspectiva do Produto
O GAC é um sistema independente composto por duas interfaces principais, divididas pelo contexto de uso:
1.  **Interface Mobile (Uso Rápido):** Focada em agilidade no balcão e nos corredores, otimizada para smartphones.
2.  **Interface Web / Desktop:** Focada na gestão, auditoria, configurações de sistema e acompanhamento de dashboards.

### 2.2 Funções do Produto (Ciclo de Vida Digital)
As macrofuncionalidades do sistema baseiam-se no ciclo de vida dos ativos:
*   **Retirada Ágil via Mobile:** Identificação do equipamento por leitura de NFC/QR Code e assinatura digital do termo de responsabilidade.
*   **Devolução com Checklist Técnico:** Registro rigoroso do recebimento do ativo com verificação do estado físico e dos acessórios.
*   **Gestão e Auditoria Centralizada:** Dashboard administrativo para controle em tempo real do inventário.
*   **Cadastro e Manutenção:** Entrada de novos equipamentos e controle de manutenções preventivas/corretivas.
*   **Alertas e Notificações:** Automação de lembretes sobre prazos e devoluções em atraso.

### 2.3 Características dos Usuários
*   **Professor (Ator Primário):** Usuário da interface mobile. Utiliza o sistema para consultar disponibilidade de equipamentos, reservar, transferir posses e realizar retiradas ágeis via leitura de QR/NFC, assinando o termo de aceite.
*   **Atendente do CCT:** Usuário da interface mobile e web. Focado no recebimento dos ativos, executa o checklist de integridade e reporta avarias no balcão.
*   **Administrador / Coordenação:** Usuário da interface web (Desktop). Gerencia os cadastros de itens, acessa relatórios estratégicos para tomada de decisão (compras) e encaminha ativos danificados para manutenção.

### 2.4 Restrições Gerais
*   A leitura de NFC dependerá da compatibilidade de hardware do smartphone do usuário. Caso o aparelho não possua a tecnologia, o sistema deverá fornecer leitura de QR Code como rota alternativa primária.

---

## 3. Requisitos Detalhados

### 3.1 Requisitos Funcionais (RF)

| ID | Descrição do Requisito Funcional |
| :--- | :--- |
| **RF01** | O sistema deve permitir que o professor consulte a disponibilidade em tempo real de projetores, chaves e acessórios via aplicativo mobile. |
| **RF02** | O sistema deve permitir que o professor realize a retirada do equipamento mediante a leitura de uma etiqueta NFC ou escaneamento de QR Code. |
| **RF03** | O sistema deve exigir e registrar o aceite digital (assinatura) do professor no termo de responsabilidade no momento da retirada ou transferência. |
| **RF04** | O sistema deve exigir que o professor informe a "Sala de Destino" onde o ativo será utilizado durante as ações de reserva, retirada ou transferência. |
| **RF05** | O sistema deve permitir a "Transferência Direta" (repasse) de um equipamento entre dois professores, atualizando a responsabilidade no banco de dados. |
| **RF06** | O sistema deve fornecer uma tela de "Checklist Técnico" (cabos, lente, controle) que o atendente deve preencher obrigatoriamente durante a devolução. |
| **RF07** | O sistema deve permitir que o atendente registre avarias (com fotos ou descrições) no momento do recebimento. |
| **RF08** | O sistema deve disparar notificações automáticas de lembrete de devolução e alertas de atraso para os professores e para o painel da administração. |
| **RF09** | O painel Web deve permitir ao administrador cadastrar novos itens (gerando códigos únicos) e agendar manutenções corretivas/preventivas. |
| **RF10** | O sistema deve gerar relatórios analíticos de histórico de uso, rastreabilidade (quem usou, quando e onde) e índice de defeitos. |

### 3.2 Requisitos Não Funcionais (RNF)

| ID | Descrição do Requisito Não Funcional | Categoria |
| :--- | :--- | :--- |
| **RNF01** | O tempo de resposta para validação da leitura do QR Code/NFC não deve exceder 2 segundos para garantir o "uso ágil". | Desempenho |
| **RNF02** | A interface mobile deve ser responsiva e projetada com foco em usabilidade (UX), permitindo a retirada com no máximo 3 cliques na tela. | Usabilidade |
| **RNF03** | O sistema deve garantir a proteção dos dados dos professores (LGPD), assegurando que o termo de responsabilidade tenha validade digital e seja armazenado com segurança. | Segurança |
| **RNF04** | A plataforma mobile deve operar nos sistemas operacionais Android (versão 8.0+) e iOS (versão 12+). | Compatibilidade |

### 3.3 Regras de Negócio (RN)

| ID | Regra de Negócio |
| :--- | :--- |
| **RN01** | **Limite de Empréstimo:** Um professor não pode alugar/retirar dois equipamentos do mesmo tipo (ex: dois projetores) para o mesmo horário de uso. |
| **RN02** | **Bloqueio por Atraso/Avaria:** Um professor com devoluções em atraso pendentes ou com histórico não resolvido de danos patrimoniais deve ser bloqueado de fazer novas retiradas até regularização com o CCT. |
| **RN03** | **Fluxo de Avaria:** Todo equipamento registrado com "Avaria" pelo atendente tem seu status alterado automaticamente para "Indisponível" e não pode ser reservado até que o administrador registre o fim da manutenção. |
