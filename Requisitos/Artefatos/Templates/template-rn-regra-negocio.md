4. template-rn-regra-negocio.md
# Especificação de Regras de Negócio

| ID | Nome da Regra | Descrição e Condições |
| :--- | :--- | :--- |
| **RN01** | Limite de Empréstimo Simultâneo | Um professor não pode realizar a retirada de um segundo projetor se já possuir um item da mesma categoria sob sua responsabilidade (sem devolução) para o mesmo horário. |
| **RN02** | Bloqueio por Atraso ou Avaria Pendente | Professores que possuam devoluções pendentes acusando atraso sistêmico, ou com histórico de danos patrimoniais não resolvidos com o CCT, serão bloqueados automaticamente de realizar novas retiradas ágeis. |
| **RN03** | Indisponibilidade Automática por Defeito | Se, durante o preenchimento obrigatório do "Checklist Técnico" na devolução, o atendente assinalar a presença de avarias, o sistema deve alterar imediatamente o status daquele ativo para "Indisponível/Em Manutenção", impedindo novas reservas. |

---
## Checklist de Validação
- [x] A regra reflete uma política real da organização (CCT)?
- [x] A regra independe de tecnologia (ou seja, existiria e faria sentido mesmo se o controle fosse feito em planilhas de papel)?
- [x] A descrição está clara, objetiva e sem ambiguidades?
