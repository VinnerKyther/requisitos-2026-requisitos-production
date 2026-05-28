# Revisão de Consistência (Requisitos x UML)

Este documento comprova o alinhamento e a consistência entre a Especificação de Requisitos (SRS) e a Modelagem Visual (Diagrama de Casos de Uso) do sistema GAC, garantindo que todas as regras de negócio elicitadas possuem representação sistêmica.

## Matriz de Rastreabilidade

| ID Requisito (SRS) | Descrição do Requisito | Caso de Uso Correspondente (UML) | Status de Alinhamento |
| :--- | :--- | :--- | :--- |
| **RF01** | Consultar disponibilidade em tempo real | `UC1 (Consultar Disponibilidade)` | ✅ Consistente |
| **RF02** | Retirada via etiqueta NFC ou QR Code | `UC3 (Retirar via QR/NFC)` | ✅ Consistente |
| **RF03** | Assinatura de termo de responsabilidade | `UC5 (Assinar Termo Digital)` | ✅ Consistente |
| **RF04** | Informar a "Sala de Destino" | `UC6 (Informar Sala de Destino)` | ✅ Consistente |
| **RF05** | Transferência Direta entre professores | `UC4 (Transferir Equipamento)` | ✅ Consistente |
| **-** | O Atendente precisa registrar a volta do item | `UC7 (Registrar Devolução)` | ✅ Consistente |
| **RF06** | Checklist Técnico obrigatório na devolução | `UC8 (Preencher Checklist Técnico)` | ✅ Consistente |
| **RF07** | Registro de avarias com fotos/descrições | `UC9 (Registrar Avaria / Defeito)` | ✅ Consistente |
| **RF08** | Alertas e notificações automáticas | `UC13 (Disparar Alertas Automáticos)` e `UC1a (Solicitar Alerta)` | ✅ Consistente |
| **RF09** | Cadastrar itens e agendar manutenções | `UC10 (Cadastrar Novo Equipamento)` e `UC11 (Agendar Manutenção)` | ✅ Consistente |
| **RF10** | Relatórios analíticos e rastreabilidade | `UC12 (Gerar Relatórios e Auditoria)` | ✅ Consistente |

**Conclusão da Revisão:** 
Após a análise de consistência, atesta-se que 100% das funcionalidades descritas na especificação textual (IEEE 830) estão fielmente representadas na modelagem estrutural do Diagrama de Casos de Uso, respeitando os atores definidos (Professor, Atendente, Administrador e Sistema).
