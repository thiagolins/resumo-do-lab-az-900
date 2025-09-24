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
