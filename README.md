
<h1 align="center">Estudo para certificação AWS</h1>
<p align="center">
    <img src="images/aws.png" alt="aws" width="200"/>
</p>

---
# Cloud Computing
O que é Cloud Computing  é a entrega sob demanda de poder de computação, armazenamento de banco de dados, aplicativos e outros recursos.
- Só irá pagar o que for utilizado, quando não usar mais, irá parar de pagar.
- Proporciona exatamente o tamanho e tipo de recurso computacional que precisa.
- Pode acessar vários recursos quando precisar, instantaneamente.
- Tem uma interface simples para gerenciar todos seus recursos de server, storages, databases etc.
A ideia de usar o serviços de cloud computing é mudar de seus servidores locais em escritórios e garagens, para um cloud , que também utiliza datacenters.

## 5 caracteristicas de cloud computing:
- Autoatendimento sob demanda;
- Amplo acesso à rede;
- Multilocação e pool de recursos;
- Elasticidade e escalabilidade rápida;
- Paga somente o que usa;

## 6 vantagens do Cloud Computing:
- Calcular despesas capitais(CAPEX) com despesas oreacionais(OPEX);
- Beneficio de enormes economias de escala;
- Dimensionar automaticamente a capacidade de hardware para aplicação;
- Aumento de velocidade e agilidade;
- Sem pagamentos desnecessário para processamentos que não usamos;
- Criação de aplicação global.

## Tipos de Cloud Computing:
- Infraestructure as a Service(IaaS): Fornece blocos de construção para TI em nuvem. Fornece redes, computadores, data storage, Alta flexibilidade, Facil para migrar para TI tradicional (servidor local).
- Plataform as a Service(PaaS): Remove a necessidade de organizações de gerenciamento de infraestrutura. Desenvolvimento e gerenciamento de suas aplicações
- Sofware as a Service(SaaS): Produto completo que será gerencia e executado pelo provedor de serviço

## 3 Princípios básicos para precificação da AWS
- Para computação: Pago pelo tempo exato do computador ligado.
- Para Armazenamento: Pago pela quantidade exata de dados armazenados na nuvem.4
- Para transferência fora da Nuvem: Pago apenas quando dados saírem da AWS 

## AWS Cloud History
Foi lançada em 2002 internamente na Amazom.com. Em 2004 lançaram a primeira oferta publica chamada SQS. Em 2006 realçaram  com a disponibilidade de SQS, S3 e EC2. 2007 lançaram na Europa. 

## AWS Regions
Estão em todo o mundo e são alocados data centers nessas regiões, quando usamos algum serviço, na maioria das vezes serão vinculados a uma região especifica
Como escolher uma AWS region? Depende, pois vai depender da distância, podendo causar alta latência entra a comunicação do data center. Tambem há o fator de q algumas regiões não tem todos os serviços disponibilizados. Os preços variam de região para região, então teria q consultar a tabela de valores entre as regiões
AWS Avaliability Zone
São o que está acontecendo na região. Cada região terá varias Avaliability Zones(normalmente 3, min:2, max:6) Elas ficam separados para que cara uma seja isolada da outra para caso aconteça algum desastre, tenha outra para ser substituída. Elas são conectadas uma a aoutra com latência ultra-baixa. Juntas elas formam uma Região.


---
<h1 align="center">IAM – Identity and Acess Management</h1>

## Users, Goups and Policies
É criado User e Goups para possemos atribuir policies a eles, fazendo com que tenham acesso aos serviços que necessitam ter, e não a tudo como um ADM. Os User e Goups pode receber um JSON document chamado POLICIE.

É uma Boa pratica criar um usuário ADM para fazer a administração da AWS, e resguardar a conta Root por segurança

## IAM Policies
Json document há uma estrutura como os seguintes campos: **Numero de versão** , **Id** para identificação da policie,e **Statement** contendo mais informações como: **Sid** sendo um ID de instrução, **effect** sendo o efeito da policie. **Principals** consiste em quais contas, usuário ou funções receberão essa policie. **Action** contendo uma lista de chamadas a API q serão setadas de acondo com o valor do campo **effect**. E resource contem uma lista de recursos que as ações serão aplicadas.

As policies bom ser atribuídas a um grupo ou a um usuário. Também pode ser criado suas próprias Policies escrevendo um Json ou com interface visual.

## IAM MFA
É o sistema de proteção dos usuário e grupos contendo dois mecanismos de defesa. O primeiro é **Password Policy.** Nesse mecanismo pode ser configurado exigências na hora de cadastrar uma senha, como numero de caracteres, letras especiais etc. pode ser definido também um tempo de expiração das senhas para q sejam trocadas seguidamente. e também para não reutilizar senhas q já foram usadas.

O segundo mecanismo é o **MAF(Multi Factor Autentication).** O beneficio do MAF é que caso sua senha seja perdida/hackeada, não será comprometida pois para acessar, precisará dos números do MFA para fazer login.

**Dispositivos MAF da AWS:**
- **Virtual MFA** com Google Authenticator ou Authy;
- Universal 2nd Factor (U2F) Security Key. É um dispositivo Físico tipo USB;
- Hardware Key Fob MAF Device;
- AWS GovCloud;

## AWS Access Keys, CLI and SDK
Existem 3 jeitos de acessar a conta AWS;
- AWS Management Console (Password Policy + MFA);
- AWS CLI: Protegidas por chaves de acesso;
- AWS SDK: Protegidas por chave de acesso. Existe para Aplications, Mobile e IoT

Para gerar uma chave de acesso deve ser feito através da AWS Console

## Configurar AWS CLI

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-version.html

Após fazer a instalação do CLI no seu computador, é necessário configurar o o acesso do CLI com as chaves de acesso do usuario(IAM > users > youruser > Security credentials).

``` AWS CLI
**C:\Users\Patrick>** aws configure
**AWS Access Key ID [None]:** AKIA3BEXK6YIQICPK7HW
**AWS Secret Access Key [None]:** SOdsxnfd7Fqgomot4hXDTDLU/ZBUW/NyCdHZb6ip
**Default region name [None]:** sa-east-1
**Default output format [None]:** (enter)
```

Para testar o usuario adm configurado: 
``` AWS CLI
**C:\Users\Patrick>** aws iam list-users
```

## AWS Cloud Shell

Está disponível somente para algumas Regions

Todos os arquivos que forem criados em seu AWS Cloud Shell, mesmo após reiniciar o terminar ainda terá seus arquivos. É possível fazer Download e Upload de arquivos através do AWS Cloud Shell

## IAM Roles for AWS Services

É responsável por criar permissões aos serviços que o usuário esta usando, para q que este serviço possa fazer outra interações com a AWS

## IAM Security Tools

IAM Credential Report(Acount Level) - Pode ser criado um relatório de credenciais do IAM;
_IAM > Credential Report > Download_

IAM Access Advisor(User Level) – Mostrará as permissões de serviço concedidas a um usuário
_IAM > User > YourUser > Access Advison_

## Shared Responsibility Model for IAM
<img src="images/img1.png" alt="img1" width="800"/>

---
<h1 align="center">EC2 - Elastic Compute Cloud</h1>

## AWS Budget Setup
Para que o usuário IAM possa fazer alterações no Billings Dashboard deve-se logar no root > acount > e editar “Usuário do IAM e acesso de função às informações de faturamento”.

Esse serviço é responsável por toda a parte de custos da sua conta, com ele poderá criar alertas e alguns limites de gastos que você usa ou usará. Tambem poderá ver onde foi cobrado tal valor.

Na aba “Bills” poderá ver quais serviços eraram custos e em quais regiões ass como todos os detalhes do uso do serviço.
Para definir um Budget va em Budget > Create a Buget > Cost budget. Basta configurar o limite de gasto no mês definindo o valor. Na próxima aba deverá ciar thresholds para disparar algum alerta

## EC2 (Elastic Copute Cloud)

É uma das ofertas mais populares da AWS e é usada em todos os lugares.

EC2 é uma maeira de fazer "ifraestructure as a service". Não é apenas um serviço, ele é composto por muitas outras coisas de alto nível.

- Pode criar VMs o EC2;

- Armazenar dados em virtual drivers(EBS);

- Pode distribuir carga entre maquinas (Elastic Load Balancer - ELB);

- Pode escalar serviços usando um grupo de escalonamento automático (ASG)

## Configuração EC2

- Pode haver Windows, Linux e Mac;

- CPU, Memória RAM, Storage Space(EBS e EFS ou EC2 storage);

- Qual network deseja, Placa de rede, IP público;

- Regras de Firewall (security group);

- Boosttrap Script (EC2 User Data)

**Bootstrap (EC2 Data User)**

Bootstrapping significa os comando laçados quando a VM estiver iniciando. Esse comandos rodarão apenas uma vez quando essa maquina for criada, e nunca mais será rodado. Com o EC2 Data User script você pode: instalar softwares, instalar updates, baixar arquivos da internet para que a sua instância d VM seja inicializada e já configurada como deseja. Quanto mais Scripts colocar, mais demorado será para criar sua instância. TODOS os EC2 data user são rodados como Root.

## EC2 hands on

EC2 > instances > launch an Instance

Sempre usar a **t2.micro**

Key pair to login – é necessário se utilizar ua conexão SSH para acessar a instancia. Para gerar ua SSH Key pela AWS basta ir em **Create new key pair** nomear a chave,deixar como RSA. Para Mac, Linux ou widows 10 deixe como .pem. Se tiver Windows com versões infoeriores, use o .ppk.

Em Network Settings não precisa mudar nada. Terá um ip publico.

Em Storage (volumes) sempre é importante deixar habilitado a opção em advanced > Delete on termination > Yes. Para deletar a memoria quando a VM for termiada

Em Advanced details no ultimo box de texto você poderá escrever seu EC2 Data User, para executar loco que a maquia for criada. Um exemplo que será utilizado é a inicialização de um website simples.

``` AWS User Data
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemtl enabel httpd
echo "<h1>Hello Word from $(hostname -f)</h1>" > /var/www/html/index.html
```

Para interromper uma instância – Actions > Instance States > Stop

Para startar uma instância – Actions > Instance States > Start

Para Terminar uma instância – Actions > Instance States > Terminate

Quando dar um Stop em uma instância, o ip Publico pode alterar. Certifique-se sempre disto.

Nunca mudará o Private IP!

## EC2 Instance Types Basics

Existem diferentes tipos de EC2 para usar com diferentes casos, e com diferentes tipos de optimização. Para isso será dividido em 7 tipos de propósitos.

**General Purpose** - Bom para diversidade de cargas de trabalhos como servidores web, ou repositório de código. Tem uma equilíbrio entre compute, memória e Rede.

**Compute Optimized** – Ótimos para optimizar tarefas de computação intensiva. Bom para quando precisa de um CPU de alto nível. Uso para processos em lote, Transcode, Alta performance em web services, Alta performance em computação (HPC). Processamento de modelo de Machine learnig, ou server dedicado a jogos.

**Memory Optimized** – Terão um desempenho maior para o tipo de cargas de trabalho que processarão grandes conjuntos de dados na memória. Alta performance em Banco de dados, cache de web, memoria optimizada para BI e aplicativos que executam processamento em tempo real.

**Storage Optimized** – Ótimos quando necessita acessar um conjunto de dados o local storage.

Terão alta processamento transacional online de alta frequencia (OLTP), Banco de dados. Cache para banco de dados(ex: redis). Sistema de arquivos distribuídos

Os demais exemplos de Accelerated Computing, Instance Features e Measuring Instance Performance, bastam verificar em [https://aws.amazon.com/ec2/instance-types/?nc1=h\_ls](https://aws.amazon.com/ec2/instance-types/?nc1=h_ls)

## Security Groups &amp; Classic Ports Overview

