## 1. Nome do caso de uso: Retirar Equipamento via QR/NFC
**Objetivo:** Permitir a retirada de um ativo físico utilizando a leitura do identificador (QR Code ou tag NFC) pelo dispositivo móvel.
**Classificação:** Concreto
**Atores:** Professor (Primário), Atendente (Primário)

**Pré-condições:** 
* O usuário deve estar autenticado no sistema.
* O usuário não deve possuir pendências ou atrasos em devoluções anteriores.

**Fluxo Principal:**
* **P1.** O ator seleciona a opção "Escanear QR/NFC" no aplicativo.
* **P2.** O sistema ativa a câmera ou o sensor NFC do dispositivo.
* **P3.** O ator aproxima o celular do equipamento desejado.
* **P4.** O sistema reconhece o ativo e verifica a sua disponibilidade no inventário.
* **P4.1** O sistema inclui o caso de uso "Informar Sala de Destino".
* **P5.** O sistema exibe o termo de responsabilidade digital.
* **P5.1** O sistema inclui o caso de uso "Assinar Termo Digital".
* **P6.** O sistema registra a saída, vincula o ativo ao ator e altera o status do equipamento para "Em Uso".
* **P7.** O caso de uso é encerrado.

**Fluxos Alternativos:**
* Não se aplica.

**Fluxos de Exceção:**
* **E1. Ativo indisponível ou inexistente**
  * **E1.1** No passo **P4**, o sistema identifica que o ativo lido não existe na base ou já possui o status "Em Uso".
  * **E1.2** O sistema apresenta a mensagem de erro correspondente à indisponibilidade.
  * **E1.3** O caso de uso é encerrado.
* **E2. Usuário com pendências**
  * **E2.1** No passo **P1**, o sistema identifica que o ator possui devoluções em atraso.
  * **E2.2** O sistema apresenta a mensagem de bloqueio por pendência.
  * **E2.3** O caso de uso é encerrado.

**Pós-condições:** O ativo passa a constar na lista de "Meus Ativos em Uso" do ator e fica indisponível para novas retiradas.
**Requisitos não funcionais associados:** O tempo de resposta para a validação da leitura do QR Code/NFC não deve exceder 2 segundos.
**Pontos de Extensão:** Não aplicável.
**Frequência de utilização:** Alta (Múltiplas vezes ao dia, principalmente nos intervalos de aulas).

---

## 2. Nome do caso de uso: Registrar Devolução
**Objetivo:** Processar o recebimento do equipamento no CCT e encerrar o vínculo de empréstimo com o usuário.
**Classificação:** Concreto
**Atores:** Atendente (Primário), Administrador (Primário)

**Pré-condições:** 
* O ativo deve constar no sistema com o status "Em Uso".

**Fluxo Principal:**
* **P1.** O ator seleciona a opção "Registrar Devolução" e escaneia o QR Code/NFC do equipamento.
* **P2.** O sistema exibe os dados do empréstimo em aberto (Nome do Professor, Equipamento, Horário de Retirada).
* **P2.1** O sistema inclui o caso de uso "Preencher Checklist Técnico".
* **P3.** O ator aprova a devolução confirmando que os itens estão em conformidade. **[PE1]**
* **P4.** O sistema desvincula o professor responsável, registra o horário da entrega e altera o status do ativo para "Disponível".
* **P5.** O caso de uso é encerrado.

**Fluxos Alternativos:**
* Não se aplica.

**Fluxos de Exceção:**
* **E1. Empréstimo não encontrado**
  * **E1.1** No passo **P2**, o sistema não identifica um empréstimo em aberto para o equipamento lido.
  * **E1.2** O sistema exibe mensagem informando que o ativo já se encontra devolvido ou inválido.
  * **E1.3** O caso de uso é encerrado.

**Pós-condições:** O ciclo de empréstimo é encerrado no histórico do professor.
**Requisitos não funcionais associados:** A mudança de status do ativo para "Disponível" deve ser refletida nos dashboards em tempo real.
**Pontos de Extensão:** 
* **PE1. Registrar Avaria / Defeito:** No passo **P3**, se o checklist preenchido pelo ator apontar dados de danos, o sistema estende o fluxo para o caso de uso "Registrar Avaria / Defeito" (alterando o status final do ativo para "Em Manutenção").
**Frequência de utilização:** Alta (Múltiplas vezes ao dia).

---

## 3. Nome do caso de uso: Consultar Disponibilidade
**Objetivo:** Permitir ao usuário verificar a quantidade de equipamentos livres e prontos para uso no CCT.
**Classificação:** Concreto
**Atores:** Professor (Primário), Atendente (Primário)

**Pré-condições:** 
* O usuário deve estar autenticado no sistema.

**Fluxo Principal:**
* **P1.** O ator acessa o menu "Disponibilidade" no painel principal.
* **P2.** O sistema lista as categorias de equipamentos (Ex: Projetores, Chaves).
* **P3.** O ator seleciona a categoria desejada.
* **P4.** O sistema retorna a lista e a quantidade exata de itens com o status "Disponível". **[PE1]**
* **P5.** O caso de uso é encerrado.

**Fluxos Alternativos:**
* Não se aplica.

**Fluxos de Exceção:**
* Não se aplica (Uma busca sem resultados é tratada na extensão PE1).

**Pós-condições:** O sistema não sofre alterações de estado.
**Requisitos não funcionais associados:** Não aplicável.
**Pontos de Extensão:** 
* **PE1. Solicitar Alerta:** No passo **P4**, caso a quantidade de itens disponíveis retorne zero, o sistema exibe a opção de notificação, estendendo para o caso de uso "Solicitar Alerta" se o ator confirmar o interesse.
**Frequência de utilização:** Alta.

## 4. Nome do caso de uso: Autenticar Usuário / Login
**Objetivo:** Validar a identidade do usuário para conceder acesso às funcionalidades do sistema de acordo com o seu perfil.
**Classificação:** Concreto
**Atores:** Professor (Primário), Atendente (Primário), Administrador (Primário)

**Pré-condições:** 
* O usuário deve possuir cadastro ativo vinculado à Unifor.

**Fluxo Principal:**
* **P1.** O ator informa o e-mail institucional e a senha na tela inicial.
* **P2.** O sistema valida as credenciais na base de dados.
* **P3.** O sistema identifica o perfil de permissão (Docente, Atendente ou Admin) e exibe o Dashboard correspondente.
* **P4.** O caso de uso é encerrado.

**Fluxos de Exceção:**
* **E1. Credenciais inválidas**
  * **E1.1** No passo **P2**, o sistema não encontra o e-mail ou a senha está incorreta.
  * **E1.2** O sistema apresenta a mensagem de erro "Usuário ou senha incorretos".
  * **E1.3** O caso de uso é encerrado.

**Pós-condições:** O ator tem uma sessão ativa no sistema.

---

## 5. Nome do caso de uso: Reservar Equipamento
**Objetivo:** Permitir que o usuário garanta a disponibilidade de um ativo para uma data e horário futuros.
**Classificação:** Concreto
**Atores:** Professor (Primário)

**Pré-condições:** 
* O usuário deve estar autenticado.

**Fluxo Principal:**
* **P1.** O ator seleciona o ativo desejado e clica em "Reservar".
* **P2.** O ator informa a data, o horário de início e o horário previsto de devolução.
* **P2.1** O sistema inclui o caso de uso "Informar Sala de Destino".
* **P3.** O sistema valida se o ativo estará livre no período solicitado.
* **P4.** O sistema confirma a reserva e altera o status futuro do ativo.
* **P5.** O caso de uso é encerrado.

**Fluxos de Exceção:**
* **E1. Conflito de Horário**
  * **E1.1** No passo **P3**, o sistema detecta que já existe uma reserva para o mesmo período.
  * **E1.2** O sistema apresenta a mensagem "Equipamento indisponível para o horário selecionado".
  * **E1.3** O caso de uso retorna ao passo **P2**.

**Pós-condições:** O ativo é bloqueado para outros empréstimos durante o período da reserva.

---

## 6. Nome do caso de uso: Transferir Equipamento
**Objetivo:** Permitir que a custódia de um ativo em uso seja repassada diretamente de um professor para outro, sem precisar passar fisicamente pelo CCT.
**Classificação:** Concreto
**Atores:** Professor (Primário)

**Pré-condições:** 
* O Professor A (doador) deve estar com o status do ativo "Em Uso".
* O Professor B (receptor) deve estar autenticado e sem pendências.

**Fluxo Principal:**
* **P1.** O Professor A acessa a aba "Meus Ativos" e seleciona "Transferir Custódia".
* **P2.** O sistema gera um QR Code temporário na tela do Professor A.
* **P3.** O Professor B escaneia o QR Code usando o seu aplicativo.
* **P3.1** O sistema inclui o caso de uso "Informar Sala de Destino".
* **P3.2** O sistema inclui o caso de uso "Assinar Termo Digital".
* **P4.** O sistema encerra o empréstimo do Professor A e inicia o empréstimo no nome do Professor B.
* **P5.** O caso de uso é encerrado.

**Pós-condições:** O vínculo do ativo é atualizado no banco de dados para o novo responsável.

---

## 7. Nome do caso de uso: Informar Sala de Destino
**Objetivo:** Registrar o local físico (bloco e sala) onde o equipamento será utilizado.
**Classificação:** Abstrato
**Atores:** Professor (Secundário), Atendente (Secundário)

**Pré-condições:** 
* O caso de uso deve ter sido instanciado por outro (Retirar, Reservar ou Transferir Equipamento).

**Fluxo Principal:**
* **P1.** O sistema exibe o formulário solicitando o bloco e a sala.
* **P2.** O ator preenche os dados e seleciona "Confirmar".
* **P3.** O sistema vincula a localização geográfica à transação atual.
* **P4.** O sistema retorna ao caso de uso chamador.

**Pós-condições:** A localização de uso do ativo fica registrada para auditoria do CCT.

---

## 8. Nome do caso de uso: Assinar Termo Digital
**Objetivo:** Coletar a anuência digital do usuário sobre as regras de conservação e prazos do ativo.
**Classificação:** Abstrato
**Atores:** Professor (Secundário)

**Pré-condições:** 
* O caso de uso deve ter sido instanciado por outro (Retirar ou Transferir Equipamento).

**Fluxo Principal:**
* **P1.** O sistema exibe o Termo de Responsabilidade com os dados do usuário e do equipamento.
* **P2.** O ator clica na caixa de seleção "Li e aceito os termos".
* **P3.** O sistema armazena a concordância com registro de data e hora (timestamp).
* **P4.** O sistema retorna ao caso de uso chamador.

**Pós-condições:** O sistema gera um respaldo legal da posse do equipamento.

---

## 9. Nome do caso de uso: Preencher Checklist Técnico
**Objetivo:** Garantir a conferência padronizada dos itens e do estado de conservação do ativo no momento da devolução.
**Classificação:** Abstrato
**Atores:** Atendente (Secundário), Administrador (Secundário)

**Pré-condições:** 
* O caso de uso deve ter sido instanciado por outro (Registrar Devolução).

**Fluxo Principal:**
* **P1.** O sistema lista os itens obrigatórios do equipamento (ex: cabos HDMI, controle remoto, integridade da lente).
* **P2.** O ator marca o status de cada item (Conforme / Ausente / Danificado).
* **P3.** O sistema salva as respostas do checklist.
* **P4.** O sistema retorna ao caso de uso chamador.

**Pós-condições:** O inventário é atualizado com as condições físicas atuais do ativo.

---

## 10. Nome do caso de uso: Registrar Avaria / Defeito
**Objetivo:** Isolar um equipamento defeituoso e documentar a falha encontrada.
**Classificação:** Abstrato
**Atores:** Atendente (Secundário), Administrador (Secundário)

**Pré-condições:** 
* O caso de uso deve ter sido instanciado pela extensão do checklist técnico.

**Fluxo Principal:**
* **P1.** O sistema exibe um formulário de relato de danos com opção de anexo de foto.
* **P2.** O ator descreve o problema e anexa a imagem do dano.
* **P3.** O sistema altera o status do ativo permanentemente para "Em Manutenção" e emite um alerta para o Administrador.
* **P4.** O sistema retorna ao caso de uso chamador.

**Pós-condições:** O ativo é bloqueado, impedindo que seja alugado por futuros professores.

---

## 11. Nome do caso de uso: Solicitar Alerta
**Objetivo:** Permitir que o usuário entre numa fila de espera e seja notificado quando um item indisponível for devolvido ao CCT.
**Classificação:** Abstrato
**Atores:** Professor (Secundário)

**Pré-condições:** 
* O caso de uso deve ter sido instanciado pela extensão da consulta de disponibilidade (quando o resultado for zero).

**Fluxo Principal:**
* **P1.** O sistema exibe a opção "Avise-me quando chegar".
* **P2.** O ator confirma o interesse.
* **P3.** O sistema vincula o e-mail/push do ator à fila de devoluções daquela categoria de ativo.
* **P4.** O sistema retorna ao caso de uso chamador.

**Pós-condições:** Nenhuma alteração de status do ativo, apenas registro de intenção do usuário.

---

## 12. Nome do caso de uso: Cadastrar Novo Equipamento
**Objetivo:** Alimentar a base de dados do GAC com novos projetores, chaves ou acessórios adquiridos pelo CCT.
**Classificação:** Concreto
**Atores:** Administrador (Primário)

**Pré-condições:** 
* O Administrador deve estar logado no painel Web.

**Fluxo Principal:**
* **P1.** O ator seleciona "Adicionar Novo Ativo".
* **P2.** O ator insere o número de tombamento (patrimônio), marca, modelo e categoria.
* **P3.** O sistema gera a ID interna e pareia com a Tag NFC ou QR Code virgem fornecido pelo ator.
* **P4.** O sistema salva o item e o disponibiliza com status "Disponível".
* **P5.** O caso de uso é encerrado.

---

## 13. Nome do caso de uso: Agendar Manutenção
**Objetivo:** Registrar o envio de um equipamento para conserto ou revisão técnica.
**Classificação:** Concreto
**Atores:** Administrador (Primário)

**Pré-condições:** 
* O ativo deve constar com status "Em Manutenção" ou "Disponível".

**Fluxo Principal:**
* **P1.** O ator seleciona o ativo e aciona "Agendar Manutenção".
* **P2.** O ator informa a empresa terceirizada, defeito relatado e data prevista de retorno.
* **P3.** O sistema atualiza o histórico do equipamento e salva os dados da ordem de serviço.
* **P4.** O caso de uso é encerrado.

---

## 14. Nome do caso de uso: Gerar Relatórios e Auditoria
**Objetivo:** Consolidar os dados operacionais do sistema para gestão estratégica do CCT.
**Classificação:** Concreto
**Atores:** Administrador (Primário)

**Fluxo Principal:**
* **P1.** O ator acessa o painel de Relatórios.
* **P2.** O ator define os filtros (período de datas, tipo de ativo, histórico de professores com atraso).
* **P3.** O sistema processa os dados e exibe os gráficos e tabelas consolidados na tela.
* **P4.** O ator seleciona a opção "Exportar PDF/Excel".
* **P5.** O sistema gera o arquivo para download.
* **P6.** O caso de uso é encerrado.

---

## 15. Nome do caso de uso: Disparar Alertas Automáticos
**Objetivo:** Enviar notificações proativas para os usuários sobre prazos operacionais.
**Classificação:** Concreto
**Atores:** Sistema Automático (Primário)

**Pré-condições:** 
* Deve haver empréstimos em curso no banco de dados.

**Fluxo Principal:**
* **P1.** O sistema varre a base de dados periodicamente em busca de empréstimos próximos do vencimento ou já em atraso.
* **P2.** O sistema identifica os usuários nessas condições.
* **P3.** O sistema aciona o módulo de envio e dispara e-mails institucionais e notificações *Push* no aplicativo.
* **P4.** O sistema gera um log de notificação enviada.
* **P5.** O caso de uso é encerrado.

---

## 16. Nome do caso de uso: Solicitar Repasse a Colega
**Objetivo:** Permitir que um professor solicite diretamente pelo aplicativo um equipamento que está atualmente em uso por outro colega, agilizando a transferência sem intervenção do CCT.
**Classificação:** Abstrato (Estende a Consulta de Disponibilidade)
**Atores:** Professor (Secundário)

**Pré-condições:** 
* O caso de uso deve ter sido instanciado pela extensão da consulta de disponibilidade (quando o ator visualiza que um equipamento está em uso por outro professor).
* O professor solicitante não pode ter pendências no CCT.

**Fluxo Principal:**
* **P1.** O sistema exibe o equipamento indisponível no CCT, mas com status "Em uso pelo Prof. [Nome] na Sala [X]".
* **P2.** O ator clica no botão "Solicitar Repasse".
* **P3.** O sistema exibe uma tela de confirmação perguntando se deseja enviar uma notificação ao colega.
* **P4.** O ator confirma a solicitação.
* **P5.** O sistema dispara uma notificação push/e-mail para o professor que está com a posse do equipamento informando: *"O colega [Nome] está solicitando o repasse do seu projetor"*.
* **P6.** O sistema retorna ao caso de uso chamador.

**Pós-condições:** O professor que possui o equipamento é notificado para, caso aceite, iniciar o CDU "Transferir Equipamento".
