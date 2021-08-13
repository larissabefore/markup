# Front-end | Módulo de Compra - Transferencia de venda entre filiais

## Fluxo do processo de Transferencia de venda entre filiais

:warning: **Resumo:** As telas fazem parte do fluxo de transferencia de venda entre filiais. 

**Caso de uso**: Usuário deseja ver a listagem de todos os produtos/acessorios/simcards que foram transferidos entre as filiais,além ser possivel realizar o cadastro dos mesmos a visuaização de um resumo e ediçao.


:bulb: **Caminho sugestivo:** `Compra -> Estoque -> Transferencia `

### :pushpin: Descrição do Cadastro

- O usuario ao acessar o cadastro de transferencia será exibido uma tela com os seguintes campos :
  - Campo de comprovante fiscal,já virá preenchido via backend, não sendo possivel a edição ou valores nulos.
  - Campo de filial(origem/destino) devem ser obrigatorios, caso não sejam preenchidos o sistema deve emitir um feedbcak de validação ao usuario.
  - Campo data de transferência deverá ser preenchido com a data atual pelo sistema, não pode ser menor que a data atual e o usuario podera altera-lá.
  - Campo de hora referente a data de transferencia, deverá ser preenchido com o horario atual, podendo ser alterado pelo o usuario.
  - Campo data de saida deverá ser preenchido com a data atual pelo sistema, e o usuario podera altera-lá, nao pode ser menor que a data atual.
  - Campo de hora referente a data de saida, deverá ser preenchido com o horario atual, podendo ser alterado pelo o usuario.
  - Todos os campos do cadastro são obrigatorios.
  
- Ao clicar a primeira vez em adicionar itens, o sistema deve exibir um campo de select com o titulo “tipo de item”;
  - O select de tipo de item deve ser preenchido com as seguintes opções:
    -Acessorios
    -Produto tim
    -Produtos de terceiros
    -Simcards
   - Caso Acessorios seja selecionado os campos devem ser exibidos :
    - Valor: sem mascara de valor monetário. Ex: 5,00
    - Tipo de alíquota as opções do select virá atraves da api.
    - Código do acessório, devera ter limitação de 16 caracteres alfanumericos.
    - Quantidade: deverá ser maior que zero.
   - Caso produtos tim/ produtoa de terceiros /sim card sejam selecionados os campos devem ser exibidos :
    - Serial do produto : limitação de 20 caracteres alfanumericos.
    - Tipo de alíquota as opções do select virá atraves da api.
- Ao preencher todos os campos e clicar em adicionar itens deverá ser exibido na tela um bloco com os produtos selecionados
- Após adicionar pelo menos 1 item o botao de salvar ficará disponivel.
- será possivel adicionar mais itens ou clilcar no botão salvar.
- Ao clicar no botão salvar, será necessario validacao se os campos que sao obriatorios estao preenchidos corretamente, caso nao estejam será exibido uma mensagem de feedback ao usuario, caso estejam corretos o modal de sucesso deverá ser exibido e o usuario será redirecionado para a listagem de transferencia.

### :pushpin: Descrição da listagem

- O Usuário ao acessar a listagem,deverá vizualisar as 10 transferencias completa atuais e seus status, será possivel realizar filtros, editar e visualizar uma transferencia selecionada.
- Os filtros disponiveis são :
  - Campo de filial.
  - Campo data de transferência.
  - Campo data de saida.
  - Campo de nota fiscal, apenas numeros e maximo de 10 caracteres.
  - Campo de n° de transfrencia, apenas numeros, sem limitação de caracteres.
  - O usuario poderá clicar na opção de "Mostrar filtros avançados".
 - Os filtros avançados disponiveis são :
  - campo de Filial de origem
  - campo de Filial de destino
  - campo de Situação fiscal
  - Campo de Situação de mercadoria.
-O usuario poderá clicar no botão buscar, se pelo menos um campo estiver preenchido, o filtro será realizado e a listagem exibida, caso nenhum campo for preenchido um modal de alerta é exibido ao usuario, informando que os campos estao vazios.
-Botões de ação de transferencias:
  -Realizar transferencia: ao clicar nesse botão o usuario será redecireciona a tela de cadastro de transferencia
  -Receber transferencia: ao clicar nesse botao será feito uma filtragem exibindo somente os itens que não foram confirmados o recebimento
  -Ver lista de transferencia completa : ao clicar nesse botao será exibido a listagem completa.
- Exibição da listagem: a listagem é composta pelas seguintes colunas:  
  - Numero
  - Data/Hora
  - Filial origem
  - Filial destino
  - Usuario de envio
  - Usuario recebimento
  - Situação/mercadoria
  - Situação fiscal : será representado por icones de cancelado ou concluido , baseado na regra de negocio.
  - Envio : poderá ter botões de visualizar, receber, nota fiscal, e editar.Caso tenha dois opões disponiveis os botões ou icones serão exibidos, caso seja mais de duas opções deverá ser exibido um icone de ação com todas as opções listadas. 
  - Confirmar recebimento: sera representado por icones de recebido ou confirmar recebimento, ao clicar na acão de confirmar recebimento o usuario sera redirecionado para a tela de recebimento.
- Ações de listagem :
  - Visualizar: caso o usuario clique nessa opção será redirecionado para a tela de resumo de pedido. (0120 figma)
  - Editar: caso o usuario clique nessa opção será redirecionado para a tela de edição de pedido. (0121 figma)
  - Anexo de nota fiscal: deve seguir o fluxo atual no sistema.
  - Receber: o usuario sera redirecionado para a tela de recebimento, deve seguir o fluxo seguindo as regras de negocio que ainda etao em analise.
  
### :pushpin: Descrição do edição/visualização

- O usuario podera visualizar os detalhes de sua trasferencia e confirmar o recebimento da mesma.
 
- No bloco referente ao resumo de pedidos devera carregar informações para o usuario, são elas:
  - Filial de origem/filial de destino:
   - Nome da filial
   - Data e hora de transferencia
   - Comprovante fiscal
   - Valor do frete
   - Informação do contribuinte
  
  - Detalhes da transferencia
   - Status do pedido
   - Quantidade de produtos
   - Tipo de produtos
   - Botao confirmar recbimento
   - Botao salvar
   
- No bloco referente a listagem de produtos devera ser exibido para o usuario: 
 - Bloco com seriais dos produtos da transferencia
 - Campo de "Filtrar por", ao ser selecionado deve exibir apenas os itens escolhidos: todos, acessorio, produto tim, produtos de terceiros e sim card, deve ter a opção "todos" como default
 - Bloco com produtos deve poder ser expandido ou retraido, por padrao deve estar retraido, alguns campos podem ser modificados, ao ser alterado algum campo ja deve ser feita a requisição com a api para a modificação ser salva.
 - Botao de "confirmar recebimento" existira apenas na tela de visualização, sua ação ira confirmar o recebimento da transferencia de itens
 - Botao de "salvar" existira apenas na tela de edição, sua ação sera salvar as modificações feitas pelo o usuario

#### Versão mobile de edição/visualização
- Link versão mobile figma: https://www.figma.com/file/pGtyzO2u6O1zFWfYRspxE8/Venda-entre-filiais-DV-3015?node-id=3680%3A87

- Na versao mobile algumas modificações no layout e funcionabilidade foram necessarias para uma melhor experiencia do usuario, utilizando um layout adaptativo.
##### Funcionalidades que foram alteradas:
 - Detalhes de filial de origem/destino: Ao clicar no card de filial de origem/destino, deve ser aberto um modal mostrando as informações das mesmas. 
 - Lista de seriais: Ao clicar em "Lista de seriais", deve ser aberto um modal mostrando as informações das mesmas. 
 - Filtrar produtos: Ao clicar em "Filtrar produtos", deve ser aberto um modal mostrando as opções de filtros, incluindo a opção "Todos", para o usuario ter a opção de visualizar todos os itens. 
 - Detalhes de produtos, na lista de produtos: Ao clicar em um item da lista de produtos, deve ser aberto um modal mostrando as informações do mesmo. 

- sugestão: criar dois templates em VueJs, um para versao mobile e outro para a desktop, pois, o layout e funcionalidades mudaram muito, assim, sendo impossivel a implementação de um layout apenas responsivo. 

#### Itens adicionais

- Link de exemplo de json para resumo de transferencia: https://gist.github.com/hiroshinetobefore/e4f41f7fd0b177953b44f20c47e9e1e0
- Link do Figma: https://www.figma.com/file/pGtyzO2u6O1zFWfYRspxE8/Venda-entre-filiais-DV-3015?node-id=4101%3A3145


Quaisquer dúvidas, me chame no slack com as dúvidas referentes ao card.
