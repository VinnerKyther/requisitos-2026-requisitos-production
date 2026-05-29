# Especificação de Caso de Uso 

**Nome do Caso de Uso:** UC03 - Retirar Equipamento via QR/NFC
**Ator Principal:** Professor
**Atores Secundários:** Sistema GAC
**Resumo:** Este caso de uso descreve os passos para que um professor consiga retirar um projetor ou chave utilizando seu smartphone para ler a etiqueta (NFC/QR Code) e assinando o termo digitalmente.

**Pré-condições:**
1. O professor deve estar logado no aplicativo mobile do GAC.
2. O equipamento (projetor/chave) deve constar com o status "Disponível" no inventário.

**Fluxo Principal (Caminho Feliz):**
1. O Professor abre o aplicativo e seleciona a opção "Retirar Equipamento".
2. O Professor aproxima o celular da tag NFC do equipamento (ou escaneia o QR Code).
3. O Sistema GAC reconhece o equipamento e exibe os dados do ativo na tela.
4. O Sistema solicita que o Professor informe a "Sala de Destino" e exibe o Termo de Responsabilidade.
5. O Professor preenche a sala, clica em "Aceitar Termo" e confirma a retirada.
6. O Sistema altera o status do equipamento para "Emprestado", vincula o ativo ao CPF do Professor e registra a data/hora da retirada.

**Fluxos Alternativos / Exceções:**
*   **Exceção 1 (Equipamento Indisponível):** No passo 3, se o sistema identificar que o QR Code pertence a um equipamento avariado ou já reservado, o sistema exibe uma mensagem de erro em vermelho e encerra o fluxo.
*   **Exceção 2 (Termo não aceito):** No passo 5, se o Professor cancelar ou não aceitar o termo de responsabilidade, o sistema não libera a retirada e o status do projetor continua como "Disponível".

**Pós-condições:**
O equipamento passa a ser de responsabilidade do Professor e o painel de gestão da coordenação é atualizado em tempo real.
