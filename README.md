# Architecting a data_warehouse

Le fichier **datawarehouse.sql** permet de reconstituer la base de données.

3 schémmas ont été créés afin de réaliser ce projet :
- **public** : qui contient les données source
- **staging** : qui sert à stocker les données avant transformation et chargement
- **core** : qui sert de data warehouse

Afin d'automatiser les traitements, un workflow ETL a été développé avec le logiciel **Pentaho**. 
- Les données sont dans un premier temps extraites des relations contenues dans le schéma **public** et chargées dans les tables du schéma **staging**.
- On y applique ensuite une suite de transformations. 
- On réalise dans un premier lieu un full load pour peupler le data warehouse représenté par le schéma **core**. 
- Par la suite, on va réaliser des delta load en se basant sur la colonne *transactional_date*. Les nouvelles données sont celles dont la date de transaction est supérieure à la date de transacrtion max présente dans le data warehouse.
