# Template de Atendimento Escalável

## Qual o propósito?

O template de atendimento escalável tem como objetivo de promover autonomia no controle e gerenciamento de horários de atendimento do seu chatbot sem a necessidade de realizar desenvolvimento dentro do fluxo!

Dessa forma, **todo gerenciamento** é realizado unicamente no menu de recursos do seu bot!

## Sumário  

- [Como configurar horário de atendimento](#como-configurar-horário-de-atendimento);
- [Como configurar os dias de funcionamento](#como-configurar-os-dias-de-funcionamento)
- [Como configurar os feriados:](#como-configurar-os-feriados);
- [Configurando o fuso-horário de atendimento](#configurando-o-fuso-horário-de-atendimento);
- [Detalhes Importantes](#detalhes-importantes)

## Como Funciona?

Primeiro você deve importar o `template de atendimento` para **seu** bot de atendimento utilizando as opções `Configuração > Versões > Carregar fluxo` como mostra na imagem abaixo;

![image](https://raw.githubusercontent.com/leisiamedeiros/BlipAttendanceTemplate/master/.github/images/importar-template.png)

Após a importação, o conteúdo do seu bot será **substituído** pelo conteúdo do bot do `template de atendimento` e você precisará publicar seu bot de atendimento para que a alteração seja replicada. Abaixo exemplo da importação;
 
![image](https://raw.githubusercontent.com/leisiamedeiros/BlipAttendanceTemplate/master/.github/images/publicar-fluxo.png)

Pronto! Todas as demais configurações serão realizadas **somente** na tela de recurso e você não precisa se preocupar com nenhum desenvolvimento. Abaixo exemplo de como acessar a tela de recursos;

![image](https://user-images.githubusercontent.com/44960191/112885419-1ddea200-90a7-11eb-8e4c-00c875a29d82.png)  

**Na tela de recursos, será possível de configurar:**

- Horário de atendimento;
    - horário de atendimento por equipe;
    - horário de atendimento por dia da semana;
- Dias de funcionamento;
- Feriados;
- Fuso-horário;

## Como configurar horário de atendimento

Em recurso, ao adicionar um novo recurso no botão `Adicionar novo` será solicitado 3 campos para preenchimento: `chave`, `tipo` e `conteúdo`. Para configurar o horário de atendimento, você deve criar o recurso para abertura e encerramento contendo os valores para horario de início e encerramento do horário da empresa, abaixo segue exemplo de horário de funcionamento das 10:00 às 22:00 horas e seus recursos cadastrados;

![image](https://raw.githubusercontent.com/leisiamedeiros/BlipAttendanceTemplate/master/.github/images/add-chave.png)  

**A configuração dos horários ficará no seguinte padrão:**

| **Chave**               | **Tipo** | **Conteudo** |
|-------------------------|----------|--------------|
| desk-HorarioAbertura    | Texto    |  10:00       |
| desk-HorarioFechamento  | Texto    |  22:00       |

Todos os campos `chave` referente a configuração de horário de atendimento <b>devem</b> ser cadastradas com o prefixo "desk-", além disso, devem ter um indicativo se o valor é vinculado ao horário de abertura ou fechamento, como no exemplo demostrado:

- Exemplo de variável para horário de abertura - desk-HorarioAbertura;
- Exemplo de variável para horário de fechamento - desk-HorarioFechamento;

### Configuração de horário de atendimento por equipe

Para configurar o horário de atendimento para equipes de atendimento, basta inserir o nome da equipe na chave do recurso, seguindo as mesmas regras apresentadas anteriormente, por exemplo:

Para uma equipe chamada `Treinamento`, poderíamos configurar as chaves da seguinte forma:

- Abertura - desk-HorarioAberturaTreinamento;
- Fechamento - desk-HorarioFechamentoTreinamento;
- Dias de Funcionamento - desk-DiasFuncionamentoTreinamento;

> *Note que o nome da equipe é inserido ao final da chave*.

### Configuração de horário de atendimento por dia da semana

Além de configurar o horário de atendimento por equipe, é possível configurar também um horário para um dia da semana **específico**, por exemplo, digamos que somente aos sábados a empresa terá um horário de funcionamento diferenciado das 8:00 às 12:00 horas. Neste caso, podemos configurar da seguinte forma - seguindo as mesmas regras apresentadas anteriormente:

- Abertura - desk-HorarioAberturaSabado;
- Fechamento - desk-HorarioFechamentoSabado;

> *Note que o nome do dia da semana é inserido ao final da chave*.

Além disso, todas as regras citadas são cumulativas, portanto, podemos também configurar horário de atendimento específico para dia da semana e equipe:
- Abertura - desk-HorarioAberturaTreinamentoQuinta
- Fechamento - desk-HorarioFechamentoTreinamentoQuinta

Caso seja necessário configurar **horários exclusivos** para outros dias da semana, seguimos o mesmo padrão para os demais dias.

## Como configurar os dias de funcionamento

A configuração dos **dias de atendimento** segue o mesmo padrão das configuração das chaves para horário de atendimento, portanto, é possível configurar chaves de atendimento para todas as equipes (padrão) ou para uma equipe específica, segue exemplo:

- Dias de funcionamento para equipes sem configuração específica (equipes padrão - Default) - **desk-DiasFuncionamento**
- Dias de funcionamento para equipe específica `Treinamento` - **desk-DiasFuncionamentoTreinamento** 

**A configuração dos dias de funcionamento seguirá o seguinte padrão:**

|**Chave**                  | **Tipo**  | **Conteúdo**  |
|-----------------------|-------|-----------|
|desk-DiasFuncionamento | Texto | 1,2,3,4,5,6 |

**Onde em conteúdo temos a relação:**
|0      |      1|    2|     3|     4|    5|     6|
|-------|-------|-----|------|------|-----|------|
|Domingo|Segunda|Terça|Quarta|Quinta|Sexta|Sábado|

**No exemplo acima, os dias de funcionamento de atendimento da empresa seguem de segunda à sabado.**

## Como configurar os feriados:

Para configurar feriados, podemos seguir o padrão já estabelecido para as chaves referentes ao horário de atendimento e dias de funcionamento. Portanto, é possível cadastrar feriado para todas as equipes de treinamento (padrão - Default), ou apenas para as equipes desejadas, ex:

- Feriado para todas as equipes - desk-Feriados;
- Feriado apenas para a equipe Treinamento - desk-FeriadosTreinamento;

**As datas deverão ser incluídas no seguinte padrão:**

| **Chave**    | **Valor**            |
|--------------|----------------------|
|desk-Feriados | 12/10/2022;25/12/2022|    

> *Cada data deve ser separada por ';' e não existem limites de datas cadastradas!*

## Configurando o fuso-horário de atendimento

Na maioria das vezes, é necessário criar um recurso com a chave **dateTimeOffset**, ela será responsável pela configuração do fuso-horário! 
Neste campo, deverá ser cadastrado a diferença de horas com relação ao horário de Greenwich, no horário padrão de Brasília, estamos 3 horas atrasadas com relação ao horário de Greenwich, portanto o valor cadastrado no conteúdo dessa chave será `-3`! Exemplo:

|**Chave**          | **Tipo**  | **Conteúdo** |
|---------------|-------|----------|
|dateTimeOffset | Texto | -3       |

---------------------------------------------------------------------

## Detalhes Importantes

- Ao cadastrar as chaves no recurso, evite usar caracteres especiais, como acentos ou 'ç';
- Para que a busca pela equipe funcione de forma correta, é necessário que o nome da equipe de atendimento que foi cadastrado na chave do recurso seja exatamente igual ao nome da equipe cadastrado no Atendimento do bot. Isso para os recursos específicos por equipe. 
    - Alem disso, dentro do bot deve ser criado esta chave no bloco em `Ações > AÇÕES DE SAÍDA > Adicionar acção de saída > Definir contato + Adicionar atributo extra` e no campo `Key` o nome deverá ser um dos seguintes valores: Equipe, Time, Atendente ou Fila e o campo `Value` será o nome da equipe;
    
    ![image](https://raw.githubusercontent.com/leisiamedeiros/BlipAttendanceTemplate/master/.github/images/config-equipe.png)  

- É necessário configurar as regras de atendimento para equipe criada, você pode conferir como configurar regra de atendimento nesse [link](https://help.blip.ai/hc/pt-br/articles/1500006317561-Como-definir-Regras-de-atendimento-com-uma-ou-m%C3%BAltiplas-condicionais);
- Para que o template funcione da forma esperada, é necessário que todos os dados estejam respeitando os seguintes formatos:

|Data       | Hora  |
|-----------|-------|
|DD/MM/AAAA | HH:MM |

