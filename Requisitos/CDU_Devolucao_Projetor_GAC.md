# Especificação de Caso de Uso

## 1. Identificação
* **Identificador:** CDU02
* **Nome do Caso de Uso:** Devolução de Projetor com Checklist
* **Atores:** Atendente do CCT (Ator Primário), Sistema GAC (Ator Secundário)

## 2. Descrição
Descreve o processo em que o atendente do CCT recebe o projetor de volta do professor, realiza a conferência física dos acessórios através de um checklist no sistema, e finaliza o empréstimo.

## 3. Pré-condições
* O Atendente deve estar autenticado no painel web ou mobile do GAC.
* O projetor deve estar com o status "Emprestado".

## 4. Fluxo Principal (Caminho Feliz)
1. O Atendente seleciona a opção "Registrar Devolução".
2. O Atendente escaneia a tag NFC/QR Code do projetor que está sendo devolvido.
3. O Sistema GAC exibe os dados do empréstimo (Nome do Professor e Horário).
4. O Sistema exibe o Checklist Técnico obrigatório (cabos, controle remoto, estado da lente).
5. O Atendente inspeciona fisicamente o projetor e marca todos os itens como "Conformes" no sistema.
6. O Atendente clica em "Confirmar Devolução".
7. O Sistema desvincula o equipamento do Professor e altera o status para "Disponível".

## 5. Fluxos de Exceção
* **6.1. Avaria Identificada:** No passo 5, se o Atendente marcar que falta um cabo ou o projetor está quebrado, o sistema exige uma justificativa em texto, notifica a coordenação e altera o status do projetor para "Em Manutenção" ao invés de "Disponível".

## 6. Pós-condições
* A responsabilidade do Professor sobre o ativo é encerrada.
* O projetor volta ao inventário e fica liberado para novas retiradas.

---
## 7. Checklist de Validação
- [x] O nome do caso de uso representa uma ação clara com verbo no infinitivo?
- [x] O(s) ator(es) principal(is) está(ão) bem definido(s)?
- [x] O fluxo principal descreve o caminho feliz completo de forma sequencial?
- [x] Os fluxos alternativos e de exceção foram mapeados cobrindo os desvios?
- [x] As pré-condições e pós-condições fazem sentido para o contexto?
