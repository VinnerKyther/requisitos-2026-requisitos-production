# Especificação de Caso de Uso

## 1. Identificação
* **Identificador:** CDU01
* **Nome do Caso de Uso:** Retirada de Projetor via Mobile
* **Atores:** Professor (Ator Primário), Sistema GAC (Ator Secundário)

## 2. Descrição
Este caso de uso descreve os passos para que um professor realize a retirada ágil de um projetor ou chave do CCT, utilizando seu smartphone para ler a etiqueta (NFC/QR Code) do equipamento e assinando o termo de responsabilidade digitalmente.

## 3. Pré-condições
* O Professor deve estar autenticado no aplicativo mobile do GAC.
* O projetor deve constar no inventário com o status "Disponível".

## 4. Fluxo Principal (Caminho Feliz)
1. O Professor abre o aplicativo e seleciona a opção "Retirar Equipamento".
2. O Professor aproxima o celular da tag NFC do projetor (ou escaneia o QR Code).
3. O Sistema GAC reconhece o patrimônio e exibe os dados do projetor na tela.
4. O Sistema solicita que o Professor informe a "Sala de Destino".
5. O Professor preenche a sala e clica em avançar.
6. O Sistema exibe o Termo de Responsabilidade Digital.
7. O Professor clica em "Aceitar Termo e Retirar".
8. O Sistema altera o status do projetor para "Emprestado", vincula ao CPF do Professor e registra a data/hora.

## 5. Fluxos Alternativos
* **5.1. Leitura Manual:** Se a câmera/NFC falhar no passo 2, o sistema permite que o professor digite o código de patrimônio do projetor manualmente.

## 6. Fluxos de Exceção
* **6.1. Equipamento Indisponível:** No passo 3, se o sistema identificar que o projetor está "Avariado" ou "Emprestado", o fluxo é cancelado e uma mensagem de erro é exibida.
* **6.2. Termo Recusado:** No passo 7, se o professor não aceitar o termo, a retirada é cancelada.

## 7. Pós-condições
* O projetor passa a ser de responsabilidade do Professor.
* O painel de gestão do CCT é atualizado em tempo real.

---
## 8. Checklist de Validação
- [x] O nome do caso de uso representa uma ação clara com verbo no infinitivo?
- [x] O(s) ator(es) principal(is) está(ão) bem definido(s)?
- [x] O fluxo principal descreve o caminho feliz completo de forma sequencial?
- [x] Os fluxos alternativos e de exceção foram mapeados cobrindo os desvios?
- [x] As pré-condições e pós-condições fazem sentido para o contexto?

--------------------------------------------------------------------------------
