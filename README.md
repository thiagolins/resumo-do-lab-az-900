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
Nome globalmente exclusivo. Como se fosse o cpf, tem que ter de 3 a 24 caracteres, letras minusculas e numeros.
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

## Segurança e identidade
### Microsoft entra ID
O mocrosoft entra id é o serviço de gerenciamento de identidades e acesso baseado em nuvem do azure.
1. Autenticação
2. Login Unico (sso)
3. Gerenciamento de aplicativos
4. Negocios para negocios (B2B)
5. Gerenciamento de dispositivos.

Subistituto do microsoft active director(AD)
Pode migrar do AD local
Usuarios, grupos,  External Ids, Roles e administratiors
Usuarios matem Audits logs, Sign-in logs e podem ser sicronizados do AD on premisses, se os usuarios forem deletados são excluidos permanentemente com 30 dias e podem ser restaurados antes disso.
A sicronização funciona do local para nuvem, e todo usuario criado no AD local é criado automaticamente na nuvem, mas os usuarios criados na nuvem não são sincronizados para o local, aquilo criado no ambiente de nuvem permanece la.
Permite o self-service password reset.
Permite o contive em grupo atravez de csv
Se não tiver um dominio cadastrado o dominio de usuario vai ficar com onmicrosoft.com
Para criar regras personalizadas precisamos da licença Microsoft entra ID p1 ou p2.
A sicronização do AD local para o Entra ID é atravez do Microsoft Entra Connect
#### autenticação x autorização
##### autenticação
1. identifica a pessoa
2. solicita credenciais de acesso legítimo
3. base para princípios de identidade e controle de acesso seguros.
##### autorização
1. determina o nivel de acesso de uma pessoa ou serviço autenticado.
2. define quais dados eles podem acessar e os que podem ficar com eles.

por segurança a ideia é que as pessoas sempre tenham o menos nivel de acesso possivél.

##### autenticação multifator (MFA)
Fornece segurança adicional para as identidades, exigindo dois ou mais elementos para autenticação completa.
Algo que você sabe <-> algo que você possue <-> algo que você é
usuario e senha <-> chaves, tokens, cartões,celular <-> reconhecimento facial,biometrico

##### B2B
Utiliza o microsoft entra external id para fazer as itengrações com parceiros como o facebook, google, etc.
Trazer a pessoa de outra empresa para acessar o nosso ambiente para fazer uma validação.

##### B2C
Azure AD B2C - Utilizar a autenticação que eu já tenho em outro provedor para me autencicar em outro serviço, ex: autencicar em determinado site com o meu login do google.

#### acesso condicional
1. associação de usuario/grupo
2. local do ip
3. dispositivo
4. aplicativo
5. detectação de risco
utiliza essas informações para ajudar na segurança para criar regras de acesso.
Permitir se o range do ip é da mesma localidade, se o dispositivo já esta cadastrado entre outro.
A ideia é bloquear os niveis de acesso até a devida autenticação e autorização

#### Controle de acesso baseado em função
gerenciamento de acesso de granularidade fina.
divida as tarefas dentro da equipe e conceda somente a quantidade de acesso de que os usuarios precisam para trabalhar
habilite o acesso ao portal azure e o controle de acesso aos recursos.
um controle mais rigoroso aos grupos de recursos ou grupo de asuarios, aplicativos, etc. 
garantir que cada usuario so possa fazer o minimo para executar o seu trabalho.
modelo de confiança zero, pensar no pior cenario, não confiar nada a ninguem e ir liberando conforme a real necessidade de uso.
proteção completa
segurança fisica -> identidade e acesso -> perimetro -> rede -> computação -> aplicativo -> dados

### Microsof Defender for cloud
Alem de fazer a varredura de segurança no Azure, pode ser conectado tambem a outros serviços de nuvem como a AWS e o GCP 
Promove recomendações de segurança atravez de pontuações.
Contem o modulo de Devops security, para inspecionar os codigos nos github, gitlab e enviar alertas.

### Marcar ou Tags
1. Fornecem metadados aos recursos do azure.
2. Organizam os recursos em uma taxonomia de maneira lógica.
3. Contituem em um par chave-valor.
4. Muito úteis para reunir informações de cobrança.

### Calculadora de custo total de propriedade (TCO)
azure.microsoft.com/pt-br/pricing/calculator
Fornece uma estimativa dos custos associados às configurações selecionadas de produtos e serviços.
1. Definir carga de trabalho
     - Servidores
     - Banco de dados
     - Armazenamento
     - Redes
3. Ajustar suposições
     - Cobertura do software assurance (fornece beneficio hibrido do azure), levar suas licenças windows ou sql server para economizar com a aquisição de novas licenças.
5. Exibir relatório

#### Cost management
Ajuda com analise de preços, criação de alerta dos gastos e recomendações de como economizar com recursos sub utilizados.

### Gerenciamento e governança
#### Governança e Conformidade
1. descrever a finalidade do Azure policy
     - O Azure policy ajuda a impor padrões organizacionais e a avaliar a conformidade em escala
     - Ele forneçe governança e consistência de recursos com conformidade regulatória, segurança, custo e gerenciamento.
     - Avalia e identifica os recursos do Azure que não atendem as suas politicas.
     - Fornece definições de políticas e iniciativas integradas, em categorias como armazenamento, rede, computação, central de segurança e monitoramento.
     - tipos de policy: non-compliant (A policy criada não afeta os recursos já existentes), remediation(cria algum cenario para informar os recursos que não cumprem a policy,ex: por uma tag) e compliant (nesse estado todos os recursos estão seguindo a policy)
2. descrever a finalidade dos bloqueios de recursos
   - proteja os recursos do azure de exclusão ou modificação acidental.
   - gerenciar bloqueios na assinatura, grupo de recursos ou níveis de recursos individuais do portal do azure.
   - bloqueios são herdados.
     
|tipos de bloqueios|ler|Atualizar|Excluir|
|Excluir|Sim|Sim|Não|
|Readonly|Sim|Não|Não|
     
4. descrever a finalidade do portal de confiança do serviço
5. descrever a finalidade do microsoft purview


