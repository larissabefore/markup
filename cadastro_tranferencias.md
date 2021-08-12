# Front-end | Módulo de Compra - Transferencia de venda entre filiais

## Fluxo do processo de Transferencia de venda entre filiais

:warning: **Resumo:** As telas fazem parte do fluxo de transferencia de venda entre filiais. 

**Caso de uso**: Usuário deseja ver a listagem de todos os produtos/acessorios/simcards que foram transferidos entre as filiais,além ser possivel realizar o cadastro dos mesmos a visuaização de um resumo e ediçao.


:bulb: **Caminho sugestivo:** `Compra -> Estoque -> Transferencia `

### :pushpin: Descrição

- O Usuário acessa a listagem, para que possa realizar a auditoria de todos os tipos de venda de aparelho e/ou serviço da TIM (mesmo as que não são enviadas documentação para a TIM) - Troca de chip não será contemplado neste escopo. Porém, se no serviço tiver um novo chip vinculado, o ICCID do chip será retornado nesta consulta.das vendas realizadas.
- O Usuário seleciona um dos botões de status para realizar a filtragem tanto por status da linha quanto por status de conciliação.
- O Usuário pode selecionar mais de um status para compor o filtro que deseja.
- O Usuário pode desselecionar o status clicando novamente no bloco referente ao status.
- O Sistema deve apresentar uma busca composta de Status + Filtros.
- 0 Usuário preenche os campos de busca que deseja filtrar
- 0 Sistema deve apresentar realizar a composição dos filtros, de forma complementar por status e demais campos preenchidos.
- 0 Usuário pode clicar no botão de ações de cada item da lista.
- Após o usuário realizar o filtro e selecionar os registros que deseja atualizar, ele poderá selecionar um ou mais destes campos para atualizar de uma vez só.
- O usuário poderá realizar uma atualização massiva através de importação
- Cada item listado deverá ter um botão de ações que terá duas opções: Detalhamento da venda (próximo item) e editar a venda. Esta última opção chama a funcionalidade de edição de venda existente. A edição de venda deverá respeitar todas as regras já pré existentes, inclusive de permissão para tal
- O usuário deverá também ter a possibilidade de editar apenas um registro por vez. Os campos que **podem ser alterados** são: **status da linha, status do serviço, fidelização de plano e fidelização de aparelho, status da conciliação**.
---
##### Filtros
- O retorno dos filtros também devem influenciar o totalizador dos indicadores de status coloridos.
- Os filtros serão: 
- Status da linha
- Status da Conciliação
- Motivo de envio (um ou todos)
- Número da linha
- Número da venda
- CPF/CNPJ
- Filial (selecionar uma ou todas)
- Período de venda
- Vendedor (um ou todos).
---
##### Dados que podem ser atualizados em lote são:
- Status da linha
- Status do serviço
- Fidelização de plano
- Fidelização de aparelho
- Status de conciliação

---
##### Importação massiva :
- O usuário poderá realizar uma atualização massiva através de importação
- O mesmo relatório que é exportado nesta funcionalidade servirá de modelo para a importação das informações que podem ser atualizadas na base.

---
##### Os status de conciliação:
- Pendente de análise
- Em análise
- Conciliado
- Não conciliado

---
##### Exportação:
- Deverá estar disponível a exportação do resultado da pesquisa.
- Os campos retornados devem ser todos os especificados abaixo:
- Filial
- Data da venda
- Número da linha
- Vendedor
- Tipo de produto (ex.: Serviço, Chip, Aparelho) - todas as classificações do mapa de vendas
- Tipo de serviço (ex.: Ativação, Migração, Upgrade, Troca de aparelho, Troca de Simcard, Venda avulsa de aparelho) - todas as classificações do mapa de vendas
- Status da linha - Pode ser alterado
- Status do serviço - pode ser alterado- Status da documentação
- Fidelização plano - Pode ser alterado
- Fidelização aparelho  - Pode ser alterado
- IMEI
- ICCID
- Plano contratado
- CPF do cliente
- Nome do cliente
- Status da conciliação (pode ser alterado)
- Motivo de envio
- Número da venda
- Valor do desconto da operadora
- Observação


#### :rocket: Condições adicionais para a tela

- Possuir hover nos itens da lista
- Validações correspondentes.
- Versão mobile deve manter a consistência de espaçamento, deixando os itens em forma de blocos.
- Quantidade mínima de itens na tela 20 itens.
- Possuir paginação
- Menu de ações deve direcionar o usuário para outras partes do sistema referente ao menu clicado.
- Versão mobile sem scroll lateral, deixando os itens em forma de blocos.

#### Itens adicionais

Adicionar Google Analytics ao módulo, para gerarmos dados/informações de uso e realizarmos acompanhamento de sucesso do mesmo.
Adicionar captura/tracking de comportamento e eventos do Google Analytics no módulo.


Quaisquer dúvidas, me chame no slack com as dúvidas referentes ao card.
