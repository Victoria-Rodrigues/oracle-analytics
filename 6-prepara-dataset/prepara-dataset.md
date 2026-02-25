#  Preparar um Conjunto de dados

## Introdução

Após a conexão com o banco e seleção das tabelas, neste lab você vai aprender a preparar seu Conjunto de Dados (Dataset) no Oracle Analytics Cloud, trazendo dados externos, enriquecendo a análise e realizando transformações preliminares à criação dos gráficos e visualizações

*Tempo estimado para o Lab:* 45 Minutos

### Objetivos

* Complementar os dados com arquivos externos
* Configurar localizações geográficas nos dados
* Ajustar colunas para nossas análises
* Criar novos campos a partir de cálculos

## Tarefa 1: Trazer um arquivo .xlsx externo

1. Faça o download do arquivo excel necessário para esse laboratório através [Download](https://objectstorage.us-ashburn-1.oraclecloud.com/p/FJncZNPkxolcQm8cSIBG3_BAK_XkDnnGBS3ok7ifwDUPBtbYn7C4BTtyu_JpptuW/n/idy4hyfbs31o/b/Bucket-Fast-Track/o/Tabla_Clientes.xlsx)


2. Clique no botão **Create** na parte superior direita e em seguida selecione **Dataset**.

![Botón Crear y luego Conexión](./images/select_dataset_labdos.png)

3. Selecione a icone de seta pra cima para fazer upload do arquivo  **Clientes.xlsx**.

![Arrastrar archivo de Excel](./images/excel-file.png)

5. O Analytics carregará e processará seu arquivo, trazendo um preview de quais as colunas presentes nele. Neste passo não é necessário realizar alterações. Clique em **OK**.

![Guardar progreso](./images/load-excel.png)

6. **Salve** seu progresso através do ícone do disquete e dê um nome para seu novo conjunto de dados e salve na pasta **Projetos**.

![Salva disquete](./images/save-file.png)

![Renombrar archivo](./images/save-file-1.png)

7. Após salva o novo dataset retorne a pagina inicial do OAC e abra o conjunto de dados **DATASET_WORKSHOP**. Ele pode ser encontrado em **Menu ⮕  Data ⮕  Datasets**.

![Comprueba tu conjunto de datos en la lista](./images/check_connection_adweli_labdos.png)

8. Clique no botão '+' (que está localizado no lado direito da tela, próximo às fontes de dados), e selecione **Add Data...**

![Agregar datos](./images/add_data.png)

9. Selecione o dataset **DATASET_CLIENTE** e clique em **Add to workbook**:

![Agregar datos](./images/add_data1.png)

10. Agora já temos os dados do excel disponíveis em nosso projeto, mas a barra horizontal entre os conjuntos de dados indica que não há nenhuma junção entre os dados do banco e os do excel, o que nos impede de cruzá-los. 

![Agregar datos](./images/oac-dois-dataset.png)


12. Para resolver isso, navegue até a aba **Data**. Leve o seu mouse até a região entre as duas fontes de dados e você verá uma linha tracejada conectando os dois, com o valor 0. Clique nessa conexão.

![Agregar datos](./images/oac-dois-dataset-2.png)


10. Selecione  **Add Another Match** (Adicionar Outra Correspondência).

![Añadir Correo](./images/correspondencia.png)

11. Relacione os dois arquivos através da chave comum entre eles (**ID Cliente** & **ID_CLIENTE**). Após fazê-lo, clique no botão **OK**.

![Únete por ID](./images/join-cliente.png)

12. Você deverá ver que agora o numeral 1 surgiu entre as bases. Isso indica que elas estão unidas através de um Join que leva em consideração uma coluna em cada base.

![Unirse Realizado](./images/join-realized.png)

13. Volte para a aba **Visualize** e valide se a barra horizontal entre os conjuntos de dados desapareceu. Se isso aconteceu, essa tarefa está pronta. Salve o painel no icone do disquete. Sugestão de nome: **PAINEL WORKSHOP**. Utilize a pasta Projeto para salvar o painel.

![Cambiar pestaña de vista](./images/tab-visualize.png)

![Cambiar pestaña de vista](./images/pasta-projeto.png)

## Tarefa 2: Ajustar dados do Dataset para visualização de Mapas

Em nossa segunda tarefa realizaremos a configuração das colunas que referenciam localizações geográficas para que tragam informações mais detalhadas e possam ser utilizadas na construção dos nossos mapas posteriormente.


1. Navegue até a aba **Data** e selecione o botão para **Editar** o dataset **Clientes**, que acabamos de carregar.


![Editar Cliente](./images/data-edit-cliente.png)


2. Todas as colunas estão corretamente identificadas como **Atributos**, portanto não será necessária qualquer alteração nesse aspecto. Selecione e coluna **Cidade** e note que do lado direito há uma série de sugestões de melhorias para ela. Clique na opção **Enrich Cidade with Province** (Enriquecer Cidade com Province).


![Enriquecer Ciudad](./images/enriquecer-cidade.png)

3. O Analytics irá se utilizar de suas bibliotecas internas para trazer o estado de cada uma das cidades indicadas, criando uma nova coluna chamada **Cidade_Province**.

![Ciudad y Estado](./images/city-province.png)

4. Na coluna **Cidade_Province** clique nos **três pontos** e selecione a opção **Rename...** e

![Ciudad y Estado](./images/clique-rename.png)

5. Dê o nome **Estado** para essa coluna e salve essa alteração. Também é possível renomear uma coluna realizando um duplo-clique no nome dela e escrevendo o novo nome desejado para ela.

![Cambiar nombre de ciudad](./images/rename-city.png)

6. Selecione mais uma vez a coluna **Cidade** e agora clique nas recomendações **Enrich Cidade with Lat** e **Enrich Cidade with Lon** (Enriquecer Cidade com Lat e Long). Renomeie-as para Latitude e Longitude.

![Renombrar Estado](./images/state-edit.png)

7. Clique no **três pontos** nas novas colunas (Latitude e Longitude) e selecione **Location Details** (Detalhes do Local…)

![Enriquecer con Latitud y Longitud](./images/lat-long.png)

8. Defina o **Location Details** adequado para as colunas de Longitude e Latitude e clique em **OK**

![Detalles de ubicación](./images/local-detalhe.png)

9. Valide se as novas colunas estão identificadas como localizações.

![Tipo de ubicación](./images/local-type.png)


10. Selecione mais uma vez a coluna Cidade e agora clique na recomendação **Enrich Cidade with Population** (Enriquecer Cidade com Population).

![Columnas de ubicación](./images/populacao.png)


11. Valide que a coluna População da Cidade foi criada e salve o Dataset no disquete.

![Enriquecer Ciudad con Población](./images/enriq-cidade.png)

## Tarefa 3: Realizando alterações nas colunas

Ahora haremos algunos ajustes más que simplificarán la forma en que vamos a interactuar con los datos al crear nuestro tablero.

1. En la pestaña **Datos**, haga clic en el botón para editar los datos de conexión de la base de datos.

![Cambiar a la pestaña Datos](./images/data-tab-2.png)


2. Realizaremos una agrupación utilizando la interfaz de Analytics. Cambie la pestaña inferior a la tabla **VENTAS**, seleccione la columna **EMBALAJE DEL PRODUCTO**, haga clic en los tres puntos y elija la opción **Grupo**.

![Preparación de datos - Grupo](./images/group.png)

6. Crea dos categorías:
   - Empaque Grande: tendrá en su interior los valores Big Box, Jumbo Box y Jumbo Value;
   - Empaque Pequeño: contendrá los valores Caja Mediana, Caja Pequeña, Paquete Pequeño y Bolsa Empaque.
   Después de crear los grupos, asegúrese de nombrar **Tipos de empaque** para la nueva columna que se creará y haga clic en **Agregar paso**.

![Tipos de Empaques](./images/tipos-embalagem.png)

7. Para el próximo cambio, crearemos un campo que se originará a partir de una regla escrita en la capa de preparación del OAC. Todavía en la pestaña VENTAS, seleccione la columna GANANCIAS, haga clic en los tres puntos y seleccione **Crear**. Esto hará que creemos una nueva columna a partir de la columna Beneficio.

![Crear Columna de Utilidad](./images/criar-coluna-lucro.png)

8. Nombre la nueva columna **Ganancias/Pérdidas** y escriba el código a continuación:
```
CASO CUANDO GANANCIA >= 0 ENTONCES 'Ganancia' DE LO CONTRARIO 'Pérdida' FIN
```
No olvide asignar la columna Beneficio (solo el texto no se referirá a ella).
Haga clic en **Agregar paso** para guardar este paso. Reproduzca el proceso en el GIF a continuación para asegurarse de que el proceso sea un éxito.

![Creando cálculo OAC](./images/assign.png)


¡Felicitaciones, ha terminado este laboratorio!
Puede **pasar al siguiente laboratorio**.

## Conclusión

En esta sesión aprendiste a preparar un Dataset en Oracle Analytics Cloud, realizando una serie de transformaciones de datos y complementándolas con información externa disponible en un archivo excel.

## Autoría

- **Autores** - Thais Henrique, Isabela Alvarez, Breno Comin, Isabelle Dias e Guilherme Galhardo
- **Traducción** - Eliana Romero
- **Última actualización por/fecha** - Eliana Romero, Agosto/2023