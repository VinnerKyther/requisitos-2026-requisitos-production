# Backlog do Produto (Priorizado)
**Projeto:** GAC (Gestão de Ativos do CCT)

Este documento contém o backlog priorizado do sistema, listando as funcionalidades essenciais mapeadas durante a elicitação, organizadas da maior para a menor prioridade de desenvolvimento para garantir a entrega contínua de valor.

## 🔴 Prioridade Alta (Essencial para o sistema rodar)

**Épico 1: Cadastro e Manutenção do Inventário**
*   **[US01] Cadastrar Equipamento:** Como administrador do CCT, eu quero cadastrar novos projetores, chaves e acessórios no sistema para que eles fiquem disponíveis no inventário virtual [3].
*   **[US02] Consultar Disponibilidade:** Como professor, eu quero visualizar em tempo real a disponibilidade de chaves e projetores pelo celular para saber se posso utilizá-los na minha aula [2].

**Épico 2: Retirada Ágil via Mobile**
*   **[US03] Retirar via QR Code/NFC:** Como professor, eu quero utilizar meu celular para ler o QR Code ou NFC do equipamento, liberando sua retirada sem precisar assinar papéis no balcão [2, 3].
*   **[US04] Assinar Termo Digital:** Como professor, eu quero dar o aceite digital no termo de responsabilidade na tela do aplicativo para confirmar que estou com o equipamento sob meus cuidados [2].

---

## 🟡 Prioridade Média (Garante a segurança e a rastreabilidade)

**Épico 3: Devolução com Checklist Técnico**
*   **[US05] Registrar Devolução:** Como atendente do CCT, eu quero dar baixa no equipamento devolvido no painel para que ele volte a constar como "Disponível" no inventário [2, 3].
*   **[US06] Preencher Checklist Técnico:** Como atendente do CCT, eu quero preencher um checklist rápido durante a devolução para garantir a integridade dos cabos, controles e do projetor [3].
*   **[US07] Registrar Avaria/Defeito:** Como atendente do CCT, eu quero registrar eventuais danos físicos encontrados durante o checklist para enviar o equipamento à manutenção e evitar que o próximo professor pegue um item quebrado.

**Épico 4: Gestão e Auditoria Centralizada**
*   **[US08] Visualizar Painel de Gestão (Dashboard):** Como administrador, eu quero acessar uma interface web com a visão geral do inventário para monitorar quem está com cada equipamento em tempo real [2, 3].

---

## 🟢 Prioridade Baixa (Melhorias e Automações)

**Épico 5: Alertas, Notificações e Relatórios**
*   **[US09] Receber Alertas de Atraso:** Como professor, eu quero receber lembretes automáticos no celular avisando sobre o fim do prazo da aula para não esquecer de devolver a chave/projetor [2].
*   **[US10] Notificar Atrasos Críticos:** Como administrador, eu quero que o sistema dispare um alerta no painel web sempre que um item não for devolvido no prazo estipulado [2].
*   **[US11] Gerar Relatórios Analíticos:** Como coordenação do CCT, eu quero exportar relatórios com históricos de uso e avarias para tomar decisões estratégicas sobre compras de novos equipamentos [3, 4].
