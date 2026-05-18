### Especificação de Casos de Uso (MCU) - Sistema GAC

#### Histórico de Versões
| Data | Versão | Descrição | Autor |
| ------ | ------ | ------ | ------ |
| 16/05/2026 | 1.0 | Criação da especificação textual de Casos de Uso | [RequisitosProductions] |

#### 1. Atores do Sistema
Os atores são os perfis de usuários que interagem diretamente com o sistema para realizar alguma ação:
*   **Professor do CCT:** Usuário final que utiliza o sistema (foco no Mobile) para consultar equipamentos e realizar a retirada.
*   **Atendente do CCT:** Operador do balcão responsável por entregar os equipamentos, checar o estado físico na devolução e dar baixa no sistema.
*   **Administrador / Coordenação:** Gestor com acesso à plataforma Web/Desktop para gerir o inventário e analisar métricas.

#### 2. Especificação dos Casos de Uso e Relacionamentos

##### UC01 - Retirar Equipamento (Leitura NFC/QR)
*   **Ator Principal:** Professor do CCT
*   **Descrição:** Permite que o professor utilize o aplicativo para escanear a etiqueta (QR Code ou NFC) colada no projetor ou na chave, iniciando o processo de locação rápida.
*   **Relacionamento:** Inclui (`<<include>>`) obrigatoriamente o **UC02**. O equipamento não é liberado sem essa inclusão.

##### UC02 - Assinar Termo de Responsabilidade
*   **Ator Principal:** Professor do CCT
*   **Descrição:** Ação gerada automaticamente durante a retirada, onde o professor fornece o aceite digital reconhecendo as normas de uso e o prazo de devolução do ativo.
*   **Relacionamento:** É incluído (`<<include>>`) pelo **UC01**.

##### UC03 - Registrar Devolução
*   **Ator Principal:** Atendente do CCT
*   **Descrição:** O atendente recebe o projetor ou a chave no balcão e acessa o sistema para confirmar que o ativo foi devolvido pelo professor.
*   **Relacionamento:** Inclui (`<<include>>`) obrigatoriamente o **UC04**.

##### UC04 - Preencher Checklist Técnico
*   **Ator Principal:** Atendente do CCT
*   **Descrição:** Durante a devolução, o atendente deve preencher um formulário rápido informando se os cabos e o controle estão presentes e se o equipamento sofreu alguma avaria.
*   **Relacionamento:** É incluído (`<<include>>`) pelo **UC03**.

##### UC05 - Consultar Disponibilidade
*   **Ator Principal:** Professor do CCT, Atendente do CCT
*   **Descrição:** Permite aos usuários visualizar em tempo real se há projetores ou chaves de laboratório disponíveis no balcão antes de se deslocarem até lá.
*   **Relacionamento:** Nenhum.

##### UC06 - Cadastrar Novo Ativo no Inventário
*   **Ator Principal:** Administrador
*   **Descrição:** Permite à gestão registrar a compra de um novo projetor ou a criação de uma nova chave, gerando no sistema o código que será impresso no QR Code ou na tag NFC.
*   **Relacionamento:** Nenhum.

##### UC07 - Gerar Relatórios e Dashboard
*   **Ator Principal:** Administrador / Coordenação
*   **Descrição:** Permite visualizar painéis analíticos com histórico de uso, os horários de pico e equipamentos que mais apresentam defeito.
*   **Relacionamento:** Nenhum.
