# Resumo-do-lab
Este repositório contém o resumo das lições aprendidas durante o desenvolvimento do lab na DIO

# Conceito de Computação em nuvem
A computação em nuvem é o fornecimento de serviços de computação pela Internet, habilitando inovações mais rápidas, recursos flexíveis e economias de escala.

## Tipos de computação em nuvem
1. Nuvem privada
2. Nuvem pública
3. Nuvem Híbrida

## CapEx e OpEx
Os CapEx são os custos iniciais de infraestruturas físicas que tendem a reduzir com o tempo Ex: A compra dos equipamentos como rack, switches, servidores e etc.

Os OpEx são os custos com produtos e serviços que são utilizados mediante o uso, logo o pagamento é variavél. 

## SLA
SLA é um Acordo de Nível de Serviço, um contrato formal entre um prestador de serviços e um cliente que define as expectativas e o padrão de qualidade para a entrega de um serviço, como tempo de atividade, tempo de resposta e prazos. 
No Azure podemos ter uma disponibilidade do recurso em:
99%
99,5%
99,99%
99,999%

e quanto mais alta a porcentagem maior a garantia que o serviço estará disponivel.

## Criar maquina virtual no portal Azure
Ao entrar no portal você clica no "+", criar um recurso, clica no menu computação > maquina virtual
Podemos achar a documentação de criação de nova maquina virtual no link: <a>https://learn.microsoft.com/pt-br/azure/virtual-machines/windows/quick-create-portal</a>

Ao clicar para criar uma maquina virtual, diversas opções de customização aparecem, lhe dando um controle completo dos recursos a serem utilizados.
Podemos definir a região onde estará hospedando o projeto, o que pode melhorar significativamente o tempo de resposta dos seus usuário, podendo ser escolhidos mais de um local, que melhora a disponibilidade e o tempo de resposta, porem, quanto mais recursos adicionamos maior o valor a ser pago.
Tambem temos a escolha do sistema operacional de diversos linux e windows.

Na criação de uma nova maquinas podemos escolher entre maquinas em branco e em maquinas com configurações predefinidas, que são maquinas que já estão prontas para uso, com memoria, processador e armazenamento já configurados e objetivos como maquina para teste, para desenvolvimento, para produção. Porem, se voce quer ter mais customização, cria uma maquina virtual zerada e configurar manualmente a regiao, as opções de disponibilidades, o conjunto de dimensionamento, tipo de segurança, a imagem que vai rodar, contagem de instancias, habilitar o escalonamento, definir o disco, as opções de rede, gerenciamento, monitoramento e etc...

### Conjunto de disponibilidade de VM's
Dentro do mesmo datacenter temos diversos rack, onde temos os nossos dominios de falha, que são as divisões dos racks e temos os dominios de atualização, que são maquinas no mesmo rack. Exemplo de termos 6 maquinas virtuais e, 3 racks diferentes, 2 em cada. O dominio de atualização funciona da sequinte forma, criando 2 grupos de 3 maquinas, uma em cada rack, porque, se precisarmos atualizar algum recurso, podemos atualizar um dominio, enquanto o outro esta operando e quando este atualizar invertemos e atualiazamos o outro. Enquanto o dominio de falha, nos previne se algo acontecer com o rack, ecxemplo de falhar a energia desse, ainda teriamos mais 2 rack com 2 maquinas em cada para manter o serviço funcionando.

## Criação de banco de dados no Azure
Para criar um banco de dados no portal do azure, clica no "+", criar um recurso, clica no menu banco de dados 
Aqui temos diversas opções de banco de dados como: Azure cosmos SQL, Azure SQL, SQL Server, Mysql, Postgres, SQL Database entre outros.

Exemplo ao criar um SQL Database, voce escolhe o nome e voce deve selecionar um servidor lógico, se não tiver criar, temos a opção de criar um nome lo link abaixo do campo, depois voce configura se usará um pool elástico, se será um banco de desenvolvimento ou de produção, configura a computação e o armazenamento e por fim o sistema de redundancia desejado. Lembrando que quanto mais recursos usamos, maiores são os custos.

## Datacenter
No link [https://datacenters.microsoft.com](https://datacenters.microsoft.com/) podemos obter todas as informações sobre os datacenters existentes e os que estão sendo projetados. Também podemos vizualizar o globo, uma visão extrordinaria de todos os datacenters expalhados pelo globo e suas ligações. Ao clicar em cada datacenter obtemos as informações dele como: A localização, qual sua área de replicamento, ano de criação, zonas de disponibilidade, produtos disponiveis, disaster recovery, entre outras.

O brasil conta com as regiões Brazil South (São Paulo) e Brazil Southeast (Rio de Janeiro), porém, a região Brazil Southeast não conta com todos os recursos e é usada para o recurso de disaster recovery nos casos em que a LGPD não permite que os dados estejam fora do Brasil.

## Grupo de recursos
Um grupo de recursos é uma coleção de recursos que compartilha o mesmo ciclo de vida, permissões e políticas.
Podemos definir niveis de acesso para os usuários para poder adicionar, editar ou excluir um recurso do grupo.

## Serviços de computação
1. Maquinas virtuais
2. Aplicativos como serviço
3. Containers e instâncias
4. Serviço de Kubernets do Azure (AKS)
5. Áreas de trabalho remotas

### Áreas de trabalho remotas
Criam um ambiente completo de virtualiazação da área de trabalho sem precisar executar outros servidores de gateway
### Containers e instâncias
Os containeres do Azure fornecem um ambiente leve e virtualizado que não exige o gerenciamento do sistema operacional e pode responder a alterações sob demanda. Compativel com o Docker.
Instancias de conteineres é uma oferta de Paas que executa um conteiner ou pod de conteineres no Azure.
Não interage com o sistema operacional.
### Serviço de Kubernets do Azure (AKS)
Um serviço de orquestração para conteineres com arquiteturas distribuidas e grandes volumes de containeres.
### Azure function 
Uma oferta de Paas que da suporte a operações de computação sem servidor.
O codigo baseado em eventos é executado quando chamado, sem exigir uma infraestrutura de servidor durante períodos inativos.

## Armazenamento
### Contas de armazenamento
Nome globalmente exclusivo. Como se fosse o cpf, tem que ter de 3 a 24 caracteres.
Fornecer acesso à internet em todo o mundo.
Deterninar os serviços de armazenamentos e as opções de redudância.
#### Configurar a redudancia de armazenamento
LRS (armazenamento com redudância local) - Datacenter individual na região primária. Durabilidade: 11 noves.
ZRS (armazenamento com redudância de zona) - Três zonas de disponibilidades na região primária. Durabilidade: 12 noves.
GRS (armazenamento com redudância geográfica) - Datacenter único no primário e região secundária. Durabilidade: 16 noves.
GZRS (armazenamento com redudância de zona geográfica) - Três zonas de disponibilidades na região primária e um único datacenters da região secundária. Durabilidade: 16 noves.
#### Storage account
1. Blob do Azure - otimizado para o armazenamento de quantidade massivas de dados não estruturados,como texto ou dados binários.
2. Disco do Azure - fornece discos para maquinas virtuais, aplicativos e outros serviços acessarem e utilizarem. Podemos adicionar discos a quente, sem precisar para nossas maquinas ou serviços.
3. Fila do Azure - serviço de armazenamento de mensagens que fornece armazenamento e recuperação para grandes quantidades de mensagens, cada uma com até kb.
4. Tabelas do Azure - fornece a opção de chave/atributo para o armazenamento de dados estruturados não relacionais com um designe sem esquema.

Pontos de extremidade públicos do serviço de armazenamentos:
https://<storage-account-name>.blob.core.windows.net
https://<storage-account-name>.dfs.core.windows.net
https://<storage-account-name>.file.core.windows.net
https://<storage-account-name>.queue.core.windows.net
https://<storage-account-name>.table.core.windows.net

Camadas de acesso de armazenamento do Azure
Influenciam nos custos
1. Frequente - Otimizada para armazenamento de dados acessados com freqência.
2. Esporádico - Otimizada para armazenamento de dados com pouca frequencia e armazenados pelo menos 30 dias.
3. Frio - Otimizado para o armazenamentos de dados acessados com pouca frequencia e armazenados por pelo menos 90 dias.
4. Arquivo morto - Otimizada para o armazenamento de dados acessados raramente e armazenados por pelo menos 180 dias com requisitos de latência fléxiveis.

#### Azure data box
Serviço de migração fisica de dados, até 80TB de dados. Proteje os dados criptografados em uma caixa robusta dutante o trânsito. 
Migre dados do Azure para conformidades ou necessidades regulatorias.
Migre dados para o Azure do locais remotos com conectividade limitada ou sem conectividade.

#### azcopy
utilitario de linha de comando
copiar blobs ou arquivos de ou para sua conta de armazenamento
sicronização em uma direção

#### Gerenciador de armazenamento  
Interface gráfica do usuário (de modo semelhante ao windows explore)
Compativel com o windows, macOs e linux.
Mais amigavél que o azcopy

#### Sicronização de arquivos
Sicroniza os arquivos do Azure e locais de forma bidirecional.
A camada de nuvem mantem os arquivos acessados com frenquencia no local, enquanto libera espaço.
caches, smb,nfs,ftps
