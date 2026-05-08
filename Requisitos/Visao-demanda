 **GAC (Gestão de Ativos do CCT)** da Unifor, englobando o controle de projetores, chaves e acessórios:

***

### Visão da Demanda (VD)

#### Histórico de Versões
| Data | Versão | Descrição | Autor |
| ------ | ------ | ------ | ------ |
| 07/05/2026 | 1.0 | Criação do documento de visão para o GAC | Alunos do Projeto de Extensão |

#### 1. Objetivo
Especificar e definir o escopo do sistema GAC (Gestão de Ativos do CCT), criando uma plataforma digital integrada a identificadores físicos (NFC e/ou QR Code) para apoiar o ciclo de vida dos ativos da Unifor.

#### 2. Proposta de Valor
A solução GAC substituirá os controles manuais, comunicações informais e conferências pouco padronizadas por um processo 100% digital. O sistema eliminará a perda de informações, garantindo rastreabilidade clara de quem retirou o item, quando deve ser devolvido e em qual estado, além de fornecer visibilidade em tempo real da disponibilidade do inventário.

#### 3. Descrição da Demanda
O sistema apoiará o CCT (Centro de Ciências Tecnológicas) na **gestão dos seus ativos (projetores, chaves e acessórios):**
* retirada ágil de equipamentos via aplicativo mobile (NFC/QR Code);
* assinatura digital de termos de responsabilidade;
* devolução atrelada a um checklist técnico para garantir a integridade;
* gestão e auditoria centralizada do inventário;
* agendamento de manutenções preventivas;
* envio de alertas e notificações automáticas de prazos;
* e geração de relatórios analíticos estratégicos.

Todo o processo será dividido entre interfaces mobile para uso rápido no dia a dia e web/desktop para atividades administrativas.

#### 4. Partes Interessadas
| Nome | Papel | Responsabilidades | Representante |
| ------ | ------ | ------ | ------ |
| Direção e Coordenação | Cliente | Analisar relatórios estratégicos e gerir os ativos do CCT | Direção/Coordenação |
| Professores do CCT | Usuário final | Consultar disponibilidade, retirar equipamentos e assinar termos | Professores |
| Atendentes do CCT | Stakeholder | Operar checklist de devolução e gerenciar o balcão | Atendentes |
| Sistemas de TI | Stakeholder Indireto | Apoio e suporte tecnológico | NTI Unifor |
| Equipe de Alunos | Desenvolvimento | Elicitar requisitos, modelar fluxos e desenvolver protótipos | Grupo de Extensão |

#### 5. Personas
##### 5.1. Professor do CCT
* **Descrição:** Docente da instituição que precisa de projetores e chaves para realizar suas aulas.
* **Objetivo:** Consultar a disponibilidade de forma instantânea e realizar a retirada rápida do material via aplicativo, assumindo a responsabilidade.

##### 5.2. Atendente do CCT
* **Descrição:** Colaborador que gerencia a entrega e o recebimento de ativos físicos no balcão de atendimento.
* **Objetivo:** Realizar a conferência rigorosa de acessórios e do estado físico dos itens retornados através do checklist técnico.

##### 5.3. Administrador / Coordenador
* **Descrição:** Liderança responsável pelo patrimônio do Centro de Ciências Tecnológicas.
* **Objetivo:** Auditar históricos de uso, cadastrar novos equipamentos, agendar manutenções preventivas e analisar os relatórios estratégicos gerados pelo sistema.

#### 6. Necessidades e Funcionalidades

##### Necessidade 1: Retirada de Equipamentos e Chaves
###### F1.1 Identificação por NFC/QR Code
* **Descrição:** Permite identificar o equipamento e o professor de forma ágil no aplicativo.
* **Incluída**
* **Atores:** Professor, Atendente
* **Frequência:** Alta
* **Valor:** Alto

###### F1.2 Aceite digital de termo de responsabilidade
* **Descrição:** Permite ao professor assinar digitalmente que está assumindo o item.
* **Incluída**
* **Atores:** Professor
* **Frequência:** Alta
* **Valor:** Alto

##### Necessidade 2: Devolução e Controle de Qualidade
###### F2.1 Devolução com checklist técnico
* **Descrição:** Aplicação de conferência rigorosa de acessórios e estado físico do patrimônio na devolução.
* **Incluída**
* **Atores:** Atendente
* **Frequência:** Alta
* **Valor:** Alto

##### Necessidade 3: Gestão do Inventário
###### F3.1 Cadastro de novos equipamentos
* **Descrição:** Permite registrar projetores, chaves e acessórios no sistema de gestão.
* **Incluída**
* **Atores:** Administrador
* **Frequência:** Média
* **Valor:** Alto

###### F3.2 Agendamento de manutenção
* **Descrição:** Permite marcar manutenções preventivas para o inventário.
* **Incluída**
* **Atores:** Administrador
* **Frequência:** Média
* **Valor:** Médio

##### Necessidade 4: Monitoramento e Auditoria
###### F4.1 Dashboard de Visibilidade em Tempo Real
* **Descrição:** Permite acompanhar instantaneamente a disponibilidade de projetores e chaves.
* **Incluída**
* **Atores:** Todos
* **Frequência:** Alta
* **Valor:** Alto

###### F4.2 Auditoria Centralizada
* **Descrição:** Interface para geração de históricos de uso e atualização automática de status.
* **Incluída**
* **Atores:** Administrador
* **Frequência:** Alta
* **Valor:** Alto

##### Necessidade 5: Comunicação e Alertas
###### F5.1 Alertas e notificações automáticas
* **Descrição:** O sistema envia lembretes para usuários e gestores sobre prazos e eventos.
* **Incluída**
* **Atores:** Sistema
* **Frequência:** Alta
* **Valor:** Alto

##### Necessidade 6: Relatórios
###### F6.1 Relatórios Analíticos
* **Descrição:** Geração de painéis e relatórios estratégicos de uso.
* **Incluída**
* **Atores:** Direção / Coordenação
* **Frequência:** Mensal
* **Valor:** Alto

#### 7. Arquitetura da Demanda
##### Descrição da Arquitetura
O sistema será composto por duas interfaces principais e um serviço de backend integrado com identificadores físicos:

###### 1. Frontend Mobile (Uso Rápido)
* Focado em consulta de disponibilidade, identificação via NFC/QR Code e retirada ágil.
* Usuários principais: Professores e Atendentes.

###### 2. Frontend Web/Desktop (Gestão)
* Focado no cadastro, auditoria centralizada, devolução por checklist técnico e relatórios.
* Usuários principais: Administradores e Coordenação.

###### 3. Backend e Identificação Física
* Motor lógico do sistema contendo módulos de gestão, autenticação e disparo de alertas.
* Integração baseada na leitura física de etiquetas NFC e/ou QR Code coladas nos projetores e chaves.

#### Checklist de Validação do Documento de Visão
[x] O objetivo está claro e alinhado ao problema/necessidade?
[x] A proposta de valor é mensurável e relevante?
[x] Todas as partes interessadas estão listadas com papéis definidos?
[x] Existem pelo menos duas personas descritas?
[x] Todas as necessidades e funcionalidades estão relacionadas a atores?
[x] Há indicação de valor e frequência para cada funcionalidade?
[x] A arquitetura está ilustrada (mesmo que de forma simples)?
[x] O documento está escrito em linguagem clara e objetiva?
