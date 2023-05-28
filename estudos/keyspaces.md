
# Keyspaces


## Resumo


Keyspaces permite que você execute cargas de trabalho Cassandra na Nuvem AWS.

É altamente escalável, altamente disponível no serviço de banco de dados totalmente gerenciado.

Cassandra é um open-source,  wide-column e NoSQL.

É um armazenamento de dados de valor-chave e base de chaves e 
É serverless, você só paga por o que usar e é auto escalável. 

Keyspaces suporta milhares de solicitações com throughput virtualmente ilimitado e armazenamento

Compatível com CQL (Cassabdra Query Language) API

Segurança compatível com IAM, VPC and KMS

Dados são criptografados por padrão, suporta criptografia em repouso e em trânsito.

Além disso, oferece backups contínuos com PITR(Point-in-time recovery) and todas as gravações são replicadas três vezes em multiplicas AZ's para durabilidade e disponibilidade. 

Oferece 99,99% de disponibilidade em cada região da AWS sem tempo de inatividade programado.

Monitoramento através do CloudWatch, DDL actions logged with CloudTrail

Casos de uso: metadados de dispositivos IoT, perfis de usuários, Dados de séries temporais  e dados transacionais (ex: e-commerce). 

## CQL ( Cassandra Query Language)

Use o CQL para interagir com o bando de dados Cassandra ( com Keyspaces)
Você pode rodar queries CQL utilizando:

 - CQL editor no console da AWS
 - cqlsh client (CQL Shell)
 - Cassandra client driver (programmatic access)


## Migrando do Cassanda para o Keyspaces

É um processo de migração muito fácil que consiste em um processo de dois passos: 
1. Exportar seu cluster de dados existente para um arquivo CSV
2. Importar o CSV usando cqlsh COPY command para o  Keyspaces


## Consistência de gravação e leitura no KeySpaces


Tem dois modos de consistência de leitura:

- LOCAL_ONE consistency - otimizada para perfomance e disponibilidade, retornando o primeiro valor de qualquer réplica de armazenamento. 
- LOCAL_QUORUM consistency - otimizada para correção de dados, exigindo pelo menos duas réplicas antes de retornar os dados para sua aplicação.

Em toda gravação use LOCAL_QUORUM para durabilidade.


## Preços do Keyspaces

Tem dois modos:

1. Sob demanda -  Usa RRUs and WRUs (read/write request units). Paga somente pelo atual leitura e gravação. Casos de uso: quando não há como prever o tráfego da aplicação. 
   
   1 RRU = one 4kb read with LOCAL_QUORUM consistency
   1 RRU = two 4kb reads with LOCAL_ONE consistency
   LOCAL_ONE custa metade do LOCAL_QUORUM
   1 WRU = one 1kb write with LOCAL_QUORUM
    
2. Provisionado - Usa RCUs and WCUs (unidades de capacidade de leitura e gravação), você especifica o número de leituras e gravações por segundo e isto é mais definitivo. Proporciona você otimizar os seus custos, ou seja, se você conhece o tráfego de sua aplicação e consegue prever seus limites de capacidade, você deve usar o modo provisionado.

   1 RCU = one 4kb read with LOCAL_QUORUM consistency
   1 RCU = two 4kb reads with LOCAL_ONE consistency
   LOCAL_ONE custa metade do LOCAL_QUORUM
   1 WCU = one 1kb write with LOCAL_QUORUM


   
Se sua consulta retornar várias funções, você será cobrado com base no tamanho agregado dos dados.
Por exemplo:  se sua query retornar por linhas e cada linha tem 2kb de dados (8kb de dados do total), você será cobrado por 2 RCUs usando LOCAL_QUORUM consistency e 1 RCU usando LOCAL_ONE consistency.

E assim como todo serviço da AWS, você será cobrado pelo armazenamento, backup e restauração, e transferência de dados.


--ver glue com keyspaces no youtube
glue crawler atende?


Em cada tabela do keyspaces tem uma partition key (chave da partição - pode ter mais de uma) e é opcional clusterizar por uma coluna (colunas de agrupamento são usadas para classificar os dados com uma partição)
E assim, você define o schema da sua tabela.

partition key
https://docs.aws.amazon.com/keyspaces/latest/devguide/bp-partition-key-design.html
https://docs.aws.amazon.com/keyspaces/latest/devguide/how-it-works.html
https://www.scylladb.com/glossary/cassandra-partition-key/#:~:text=The%20Cassandra%20partition%20key%27s%20primary,form%20a%20single%20partition%20key

https://docs.datastax.com/en/cql-oss/3.3/cql/cql_using/useCompositePartitionKeyConcept.html


clustering columns
https://docs.datastax.com/en/dse/5.1/cql/cql/cql_using/whereClustering.html
https://docs.datastax.com/en/dse/6.0/cql/cql/cql_using/useCompoundPrimaryKeyConcept.html
https://www.bmc.com/blogs/cassandra-clustering-columns-partition-composite-key/

https://auth.cloud.datastax.com/auth/realms/CloudUsers/protocol/saml/clients/absorb

https://auth.cloud.datastax.com/auth/realms/CloudUsers/protocol/saml/clients/absorb


https://explore.skillbuilder.aws/learn/course/10674/Build%2520Modern%2520Apps%2520with%2520Purpose-Built%2520Databases%2520%28Portuguese%29
https://explore.skillbuilder.aws/learn/course/internal/view/elearning/1642/moving-to-managed-databases-on-aws-portuguese


https://explore.skillbuilder.aws/learn/course/internal/view/elearning/5296/migrating-from-apache-cassandra-to-amazon-keyspaces-portuguese

https://explore.skillbuilder.aws/learn/course/internal/view/elearning/13688/getting-started-with-amazon-keyspaces

https://explore.skillbuilder.aws/learn/course/13585/Introduction%2520to%2520Building%2520with%2520AWS%2520Databases

https://itau.udemy.com/course/learn-cassandra-from-scratch/

https://itau.udemy.com/course/from-0-to-1-the-cassandra-distributed-database/

https://itau.udemy.com/course/everything-cassandra/

aws-data-analytics-specialty-studies