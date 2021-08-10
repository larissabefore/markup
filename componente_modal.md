
## Front-end | Componentização de modal



## O novo componente poderá ser reutilizado no processo de novos módulos e refatoração de antigos.Teremos ganhos na reutilização de trechos de código, no isolamento de contexto, na legibilidade do código, e na padronização do projeto.

:bulb: **Sugestão de consulta:** Arquivo `ModalComunicados.vue`

:warning: **Resumo:** Esse modal faz parte do fluxo de transferencia, onde são realizadas os cadastros e listagem de transferencia.

**Pré-condição:** Atualmente contemplará apenas o módulo de transferencia.


---
### :pushpin: Descrição
- Sistema apresenta a visualização da mensagem de feedback em forma de modal para o usuario após ser realizada uma transferencia, trazendo a visualização de forma adaptativa ao conteúdo inserido
- Modal deve ser responsivo.
- Modal deve apresentar informações como scroll.
- Usuário deve poder clicar no botão concluir para fechar o modal.
- Usuário deve poder clicar no botão repetir para voltar a tela onde estava.


#####  #### Itens para o componente
- As seguintes opções deverão ser passadas como props no componente pois serão mutáveis.
- Receber título por parâmetro.
- Receber mensagem descritiva por parêmetro.
- Receber uma condicao para exibir com ou sem icone.
- Adicionar versão quando para sucesso e erro usando icones.
- Adicionar condição para 1 ou 2 botoes de ação.
- o componente deve adicionar uma lente ao site para dar foco ao modal, assim, escurecendo e impedindo o usuario de clicar em outras funcionalidades.



#### :rocket: Condições adicionais para a tela

- Permitir fechar modal ao pressionar tecla ESC
- Versão mobile deve manter a consistência de espaçamento, deixando os itens em forma de blocos.


#### :art:  Link do Figma com as telas

[Link do figma](https://www.figma.com/file/pGtyzO2u6O1zFWfYRspxE8/Venda-entre-filiais?node-id=3008%3A1662)

Quaisquer dúvidas, estou a disposição.
