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
