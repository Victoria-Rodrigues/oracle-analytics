# Criar e preparar seu conjunto de dados para suas análises

## Introdução

A etapa de preparação de conjunto de dados é fundamental para garantir a qualidade e a confiabilidade das análises de dados. Nessa fase, os dados brutos são coletados, limpos e organizados, eliminando inconsistências, duplicidades e valores ausentes. Além disso, são realizadas a padronização de formatos, a transformação de variáveis e a seleção de atributos relevantes para o objetivo da análise. Com um conjunto de dados bem preparado, é possível obter resultados mais assertivos e insights valiosos durante as etapas seguintes do processo analítico.

*Tempo estimado de laboratorio:* 15 minutos

### Objetivos

* Selecionar as tabelas que serão utilizadas
* Fazer o Join entre as tabelas
* Realizar o enriquecimento dos dados
* Salvar o Conjunto de Dados

## Opcional: Trocar o idioma do Analytics Cloud

1. No canto superior direito, clique no seu profile  

![acessar_perfil](./images/acessar_perfil.png)

Altere o idioma para português e salve as alterações:

![alterar_idioma](./images/alterar_idioma.png)

![alterar_idioma](./images/alterar_idioma2.png)

Após salvar as alterações, faça o login novamente no Oracle Analytics Cloud.

## Tarefa 1: Selecionar os dados para o conjunto de dados

1. Clique no botão **Criar** na parte superior direita e em seguida selecione **Conjunto de dados**.

![criar_conjunto_dados](./images/criar_conjunto_dados.png)

2. Selecione a conexão criada por você anteriormente:

![Selecionar a conexão ADW](./images/select_adw.png)

3. Expanda a lista de Esquemas do Autonomous Data Warehouse (ADW), localize o Esquema **ADMIN** e localize as três tabelas: **CLIENTE**, **VENDAS** e **PEDIDOS**. Arraste e solte as tabelas para o conjunto de dados, conforme ilustrado na imagem.

![Adicionar dados no dataset](./images/add_tabelas_dataset.png)

4. Realiza o join entre as tabelas **VENDAS** e **CLIENTES**, utilizando a coluna em comum **ID_CLIENTE**, conforme ilustrado abaixo:

![join_vendas_cliente](./images/join_vendas_cliente.png)

5. Realize o join entre as tabelas **VENDAS** e **PEDIDOS**, utilizando a coluna em comum **ID_PEDIDO**, conforme ilustrado abaixo:

![join_vendas_pedidos](./images/join_vendas_pedidos.png)


6. Clique com o botão direto do mouse na tabela **VENDAS** dentro do **Diagrama de Junção** e selecione a opção **Preservar Granularidade**.

![preservar_granularidade_vendas](./images/preservar_granularidade_vendas.png)

7. Após isso você verá um simbolo de check na lateral da caixa que representa a tabela **VENDAS**, indicando que a granularidade da tabela está preservada.

![preservar_granularidade_check](./images/preservar_granularidade_check.png)

8. Salve o conjunto de dados no disque na barra superior, confome indicado na imagem:

![salva_dataset](./images/salva_dataset.png)

9. Defina um nome para o conjunto de dados criados, por exemplo, **DS_Workshop** e clique em **OK**. Aguarde o conjunto de dados ser salvo para continuar.

![nome_dataset](./images/nome_dataset.png)


## Tarefa 2: Preparar conjunto de dados

1. Vamos começar enriquecendo os dados da tabela CLIENTES. Acessar da tabela CLIENTES na barra inferior da tela:

![enriquecer_dados_cliente](./images/enriquecer_dados_cliente.png)


2. Clique na coluna **CIDADE**. Na lateral do canto direito selecione a opção **Enriquecer CIDADE com Province**:

![enriquecer_cidade](./images/enriquecer_cidade.png)

3. Na coluna **CIDADE_Province** clique nos três pontos e selecione a opção **Renomear...**, e altere para **ESTADO**.

![add_estado](./images/add_estado.png)

![renome_estado](./images/renome_estado.png)

4. Clique novamente na coluna **CIDADE** e selecione as opções **Enriquecer CIDADE com Lat** e **Enriquecer CIDADE com Lon**

![enriq_lat_log](./images/enriq_lat_log.png)

5. Com as duas novas colunas adicionadas, altere o nome utilizando os três pontinhos na lateral da coluna e selecione **Renomear**. **CIDADE_Lon** para **LONGITUDE** e **CIDADE_Lat** para **LATITUDE**.

![add_lat_log](./images/add_lat_log.png)

![tabelas_renomeadas](./images/tabelas_renomeadas.png)

6. Clique no três pontinhos das novas colunas (LATITUDE e LONGITUDE) e selecione **Detalhes do Local…**

![detalhe_lat_log](./images/detalhe_lat_log.png)

7. Defina o Location Details adequado para as colunas de Longitude e Latitude e clique em **OK**.

![ajuste_lat_log](./images/ajuste_lat_log.png)

8. Valide se as novas colunas estão identificadas como localizações.

![colunas_localizacao](./images/colunas_localizacao.png)


9. Clique novamente na coluna **CIDADE** e vamos enriquecer os dados com a população, selecione a opção **Enriquecer CIDADE com Population**. Renomei a coluna para **POPULACAO**.

![enriq_populacao](./images/enriq_populacao.png)

10. Resultado final esperado na tabela **CLIENTES** com adição de quatro novas colunas através do enriquecimento de dados do Analitycs.

![enriq_dados_clientes](./images/enriq_dados_clientes.png)

11. Salve o conjunto de dados no disque na barra superior.


## Tarefa 3: Preparar conjunto de dados

1. Agora criaremos um campo que será originado a partir de uma regra escrita na camada de preparação do OAC. Na aba de **VENDAS**, selecione a coluna **LUCRO**, clique nos três pontos e selecione **Criar**. Isso fará com que criemos uma nova coluna a partir da coluna Lucro.

![criar_coluna_prejuizo](image-1.png)

2. Nomeie a nova coluna como **LUCRO/PREJUIZO** e escreva o código abaixo:

        <copy>
CASE WHEN LUCRO >= 0 THEN 'Lucro' ELSE 'Prejuízo' END
    </copy>
<!-- Separador -->

3. Não se esqueça de mapear a coluna **Lucro** (apenas o texto não irá se referenciar a ela). Clique em **Adicionar Etapa** para salvar esse passo. Reproduza o processo no GIF abaixo para garantir que o processo será um sucesso.

![enriq_dados_clientes](./images/criar_coluna_calculo.gif)

4. Seleciona a coluna **VALOR**, clique na área inferior esquerda no # e dentro do Formato do Número, selecione Moeda.

![moeda](image-2.png)

5. Escolha a opção que representa o real **(BRL/R$)**.

![alt text](image-3.png)

6. Realize o mesmo processo para as colunas **LUCRO**, **DESCONTO** e **PRECO_BRUTO**.

![alt text](image-4.png)

7. Selecione a coluna DESCONTO e desça até a Agregação. Selecione Média. Agora a agregação dessa coluna foi alterada.

![alt text](image-5.png)

8. Salve mais uma vez o projeto para não perder seu progresso.

## Conclusão

Nesta sessão você aprendeu criar um Conjunto de Dados no Oracle Analytics Cloud usando mais de uma tabela e aprendeu a utilizar o "Diagrama de Junção".

## Autoria

- **Autores** - Victória Rodrigues
- **Última atualização** - Fevereiro/2026