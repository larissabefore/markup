# Front-end | Módulo de Compra - Transferencia de venda entre filiais

## Fluxo do processo de Transferência de venda entre filiais

:warning: **Resumo:** As telas fazem parte do fluxo de transferência de venda entre filiais. 

**Caso de uso**Usuário deseja ver a listagem de todos os produtos/acessórios/sim cards que foram transferidos entre as filiais,além ser possível realizar o cadastro dos mesmos a visualização de um resumo e edição.


:bulb: **Caminho sugestivo:** `Compra -> Estoque -> Transferência `

### :pushpin: Descrição do Cadastro

- O usuário ao acessar o cadastro de transferência será exibido uma tela com os seguintes campos :
  - Campo de comprovante fiscal,já virá preenchido via backend, não sendo possível a edição ou valores nulos.
  - Campo de filial(origem/destino) devem ser obrigatórios, caso não sejam preenchidos o sistema deve emitir um feedback de validação ao usuário.
  - Campo data de transferência deverá ser preenchido com a data atual pelo sistema, não pode ser menor que a data atual e o usuário poderá alterá-la.
  - Campo de hora referente a data de transferência, deverá ser preenchido com o horário atual, podendo ser alterado pelo o usuário.
  - Campo data de saída deverá ser preenchido com a data atual pelo sistema, e o usuário poderá alterá-la, não pode ser menor que a data atual.
  - Campo de hora referente a data de saída, deverá ser preenchido com o horário atual, podendo ser alterado pelo o usuário.
  - Todos os campos do cadastro são obrigatórios.
  
- Ao clicar a primeira vez em adicionar itens, o sistema deve exibir um campo de select com o título “tipo de item”;
  - O select de tipo de item deve ser preenchido com as seguintes opções:
    -Acessórios
    -Produto tim
    -Produtos de terceiros
    -Simcards
   - Caso Acessórios seja selecionado os campos devem ser exibidos :
    - Valor: sem máscara de valor monetário. Ex: 5,00
    - Tipo de alíquota as opções do select virá através da api.
    - Código do acessório, deverá ter limitação de 16 caracteres alfanuméricos.
    - Quantidade: deverá ser maior que zero.
   - Caso produtos tim/ produtos de terceiros /sim card sejam selecionados os campos devem ser exibidos :
    - Serial do produto : limitação de 20 caracteres alfanuméricos.
    - Tipo de alíquota, as opções do select virá através da api.
- Ao preencher todos os campos e clicar em adicionar itens deverá ser exibido na tela um bloco com os produtos selecionados
- Após adicionar pelo menos 1 item o botão de salvar ficará disponível.
- será possível adicionar mais itens ou clicar no botão salvar.
- Ao clicar no botão salvar, será necessário validar se os campos que são obrigatórios estão preenchidos corretamente, caso não estejam será exibido uma mensagem de feedback ao usuário, caso estejam corretos o modal de sucesso deverá ser exibido e o usuário será redirecionado para a listagem de transferência.

### :pushpin: Descrição da listagem

- O Usuário ao acessar a listagem,deverá visualizar as 10 transferências completas atuais e seus status, será possível realizar filtros, editar e visualizar uma transferência selecionada.
- Os filtros disponíveis são :
  - Campo de filial.
  - Campo data de transferência.
  - Campo data de saída.
  - Campo de nota fiscal, apenas números e máximo de 10 caracteres.
  - Campo de n° de transferência, apenas números, sem limitação de caracteres.
  - O usuário poderá clicar na opção de "Mostrar filtros avançados".
 - Os filtros avançados disponíveis são :
  - campo de Filial de origem
  - campo de Filial de destino
  - campo de Situação fiscal
  - Campo de Situação de mercadoria.
-O usuário poderá clicar no botão buscar, se pelo menos um campo estiver preenchido, o filtro será realizado e a listagem exibida, caso nenhum campo for preenchido um modal de alerta é exibido ao usuário, informando que os campos estão vazios.
-Botões de ação de transferências:
  -Realizar transferência: ao clicar nesse botão o usuário será redirecionado a tela de cadastro de transferência
  -Receber transferência: ao clicar nesse botão será feito uma filtragem exibindo somente os itens que não foram confirmados o recebimento
  -Ver lista de transferência completa : ao clicar nesse botão será exibido a listagem completa.
- Exibição da listagem: a listagem é composta pelas seguintes colunas:  
  - Número
  - Data/Hora
  - Filial origem
  - Filial destino
  - Usuário de envio
  - Usuário recebimento
  - Situação/mercadoria
  - Situação fiscal : será representado por ícones de cancelamento ou concluído , baseado na regra de negócio.
  - Envio : poderá ter botões de visualizar, receber, nota fiscal, e editar.Caso tenha dois opções disponíveis os botões ou ícones serão exibidos, caso seja mais de duas opções deverá ser exibido um ícone de ação com todas as opções listadas. 
  - Confirmar recebimento: será representado por ícones de recebido ou confirmar recebimento, ao clicar na ação de confirmar recebimento o usuário será redirecionado para a tela de recebimento.
- Ações de listagem :
  - Visualizar: caso o usuário clique nessa opção será redirecionado para a tela de resumo de pedido. (0120 figma)
  - Editar: caso o usuário clique nessa opção será redirecionado para a tela de edição de pedido. (0121 figma)
  - Anexo de nota fiscal: deve seguir o fluxo atual no sistema.
  - Receber: o usuário será redirecionado para a tela de recebimento, deve seguir o fluxo seguindo as regras de negócio que ainda estão em análise.
  
### :pushpin: Descrição do edição/visualização

- O usuário poderá visualizar os detalhes de sua transferência e confirmar o recebimento da mesma.
 
- No bloco referente ao resumo de pedidos deverá carregar informações para o usuário, são elas:
  - Filial de origem/filial de destino:
   - Nome da filial
   - Data e hora de transferencia
   - Comprovante fiscal
   - Valor do frete
   - Informação do contribuinte
  
  - Detalhes da transferência
   - Status do pedido
   - Quantidade de produtos
   - Tipo de produtos
   - Botão confirmar recebimento
   - Botão salvar
   
- No bloco referente a listagem de produtos deverá ser exibido para o usuário: 
 - Bloco com seriais dos produtos da transferência
 - Campo de "Filtrar por", ao ser selecionado deve exibir apenas os itens escolhidos: todos, acessorio, produto tim, produtos de terceiros e sim card, deve ter a opção "todos" como default
 - Bloco com produtos deve poder ser expandido ou retraído, por padrão deve estar retraído, alguns campos podem ser modificados, ao ser alterado algum campo já deve ser feita a requisição com a api para a modificação ser salva.
 - Botão de "confirmar recebimento" existirá apenas na tela de visualização, sua ação irá confirmar o recebimento da transferência de itens
 - Botão de "salvar" existirá apenas na tela de edição, sua ação será salvar as modificações feitas pelo o usuário

#### Versão mobile de edição/visualização
- Link versão mobile figma: https://www.figma.com/file/pGtyzO2u6O1zFWfYRspxE8/Venda-entre-filiais-DV-3015?node-id=3680%3A87

- Na versão mobile algumas modificações no layout e funcionalidade foram necessárias para uma melhor experiência do usuário, utilizando um layout adaptativo.
##### Funcionalidades que foram alteradas:
 - Detalhes de filial de origem/destino: Ao clicar no card de filial de origem/destino, deve ser aberto um modal mostrando as informações das mesmas. 
 - Lista de seriais: Ao clicar em "Lista de seriais", deve ser aberto um modal mostrando as informações das mesmas. 
 - Filtrar produtos: Ao clicar em "Filtrar produtos", deve ser aberto um modal mostrando as opções de filtros, incluindo a opção "Todos", para o usuário ter a opção de visualizar todos os itens. 
 - Detalhes de produtos, na lista de produtos: Ao clicar em um item da lista de produtos, deve ser aberto um modal mostrando as informações do mesmo. 

- sugestão: criar dois templates em Vue Js, um para versão mobile e outro para a desktop, pois, o layout e funcionalidades mudaram muito, assim, sendo impossível a implementação de um layout apenas responsivo. 

#### Itens adicionais

- Link de exemplo de json para resumo de transferencia: https://gist.github.com/hiroshinetobefore/e4f41f7fd0b177953b44f20c47e9e1e0
- Link do Figma: https://www.figma.com/file/pGtyzO2u6O1zFWfYRspxE8/Venda-entre-filiais-DV-3015?node-id=4101%3A3145


Quaisquer dúvidas, me chame no slack com as dúvidas referentes ao card.
