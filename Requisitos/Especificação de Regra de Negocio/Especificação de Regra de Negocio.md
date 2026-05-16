## Regras de Negócio (RN) - Sistema GAC

#### Histórico de Versões
| Data | Versão | Descrição | Autor |
| ------ | ------ | ------ | ------ |
| 07/05/2026 | 1.0 | Criação das Regras de Negócio do GAC | [] |

#### 1. Objetivo
Este documento lista as Regras de Negócio (RN) do sistema GAC. Elas representam as políticas, normas e condições restritivas da Unifor/CCT que o sistema deve obrigatoriamente respeitar e aplicar durante o fluxo de empréstimo e devolução de ativos.

#### 2. Lista de Regras de Negócio

| ID | Nome da Regra | Descrição e Condições |
| :--- | :--- | :--- |
| **RN01** | **Obrigatoriedade do Aceite Digital** | Nenhum ativo (projetor, chave ou acessório) pode ter seu status alterado para "Emprestado" sem que o sistema registre o "aceite digital" do termo de responsabilidade pelo professor solicitante via aplicativo. |
| **RN02** | **Identificação Física do Ativo** | A liberação de um equipamento no sistema só será concluída após a leitura e validação bem-sucedida do identificador físico colado no aparelho (NFC ou QR Code). |
| **RN03** | **Obrigatoriedade do Checklist Técnico** | A devolução de um equipamento só será finalizada pelo atendente após o preenchimento completo do "Checklist Técnico", validando rigorosamente a presença dos acessórios (ex: cabos, controles) e o estado físico do patrimônio. |
| **RN04** | **Restrição de Equipamentos em Manutenção** | Equipamentos cujo status no inventário esteja marcado como "Em Manutenção" ou "Inativo" ficam imediatamente bloqueados para novos empréstimos ou reservas até que o administrador atualize o status. |
| **RN05** | **Bloqueio por Pendência** | Se um professor possuir um ativo não devolvido cujo prazo já expirou (em atraso), o sistema deverá bloquear temporariamente a retirada de novos equipamentos até que a pendência seja resolvida. |
| **RN06** | **Disparo de Alertas de Atraso** | O sistema deve enviar notificações automáticas de cobrança para o professor e alertas de atraso para o painel (Dashboard) dos atendentes assim que o horário limite de devolução for ultrapassado. |
| **RN07** | **Registro de Avarias** | Caso o atendente aponte uma avaria ou falta de acessório no Checklist Técnico durante a devolução (RN03), o equipamento deve automaticamente ter seu status alterado para "Em Manutenção/Aguardando Revisão", e a coordenação deve ser notificada. |
