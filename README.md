# Template de Atendimento Escalável

## Qual o propósito?

O template de atendimento escalável tem como objetivo de promover autonomia no controle e gerenciamento de horários de atendimento do seu chatbot sem a necessidade de realizar desenvolvimento dentro do fluxo!

Dessa forma, **todo gerenciamento** é realizado unicamente no menu de recursos do seu bot!

## Sumário  

- [Como funciona?](#como-funciona)
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

![image](https://user-images.githubusercontent.com/44960191/114769721-f3484680-9d40-11eb-9c4b-c674f15aec8a.png)  

**Na tela de recursos, será possível de configurar:**

- Horário de atendimento;
    - horário de atendimento por equipe;
    - horário de atendimento por dia da semana;
- Dias de funcionamento;
- Feriados;
- Fuso-horário;

## Como configurar horário de atendimento

Em recurso, ao adicionar um novo recurso no botão `Adicionar novo` será solicitado 3 campos para preenchimento: `chave`, `tipo` e `conteúdo`. 

![image](https://user-images.githubusercontent.com/44960191/114771096-8f268200-9d42-11eb-934a-778ee95826ef.png)

Para configurar o horário de atendimento será necessário criar uma configuração para abertura e uma configuração para fechamento contendo os valores para horario de início e fechamento, respectivamente. Veja abaixo:

![image](https://user-images.githubusercontent.com/44960191/114769840-196de680-9d41-11eb-8d0e-7f0bac46a5a0.png)  


## Como funciona a Chave de configuração de horário de atendimento?

![image](https://user-images.githubusercontent.com/44960191/114775700-f98df100-9d47-11eb-81f9-2543e563d5e0.png)

A chave é composta por 4 partes que permitem ao bot entender como proceder com o horário de atendimento:

- Prefixo;
- Time ou fila;
- Dia da semana;
- Abertura ou fechamento;

![image](https://user-images.githubusercontent.com/44960191/114776015-5b4e5b00-9d48-11eb-978c-ae4de3ed9bd3.png)

- Você pode usar Todos para se referir aos times ou filas de atendimento;

- Você pode usar Todos para se referir aos dias da semana também, incluindo sábado e domingo;

- Se quiser definir um horário base para todos os times e todos os dias basta configurar:
    - `desk-todos-todos-abertura`;
    - `desk-todos-todos-fechamento`; 

**A configuração dos horários ficará no seguinte padrão:**



| **Chave**               | **Tipo** | **Conteudo** |
|-------------------------|----------|--------------|
| desk-todos-todos-abertura    | Texto    |  10:00       |
| desk-todos-todos-fechamento  | Texto    |  22:00       |

![image](https://user-images.githubusercontent.com/44960191/114784721-0283c000-9d52-11eb-9b27-46f52ae99580.png)

- Configuração de abertura para todas as equipes - desk-todos-todos-abertura;
- Configuração de abertura apenas para a equipe Treinamento - desk-Treinamento-todos-abertura;

## Como configurar os dias de funcionamento

![image](https://user-images.githubusercontent.com/44960191/114786494-948cc800-9d54-11eb-9602-c85703c58dd0.png)

- Para configurar os dias, basta indicar o time/fila e, no lugar do dia da semana, indicar "dias"
- Você pode usar Todos para se referir aos times ou filas de atendimento;
- Não precisa colocar abertura/fechamento.
- Ao invés de informar hora, precisa informar os dias de funcionamento, onde temos a seguinte relação:

|0      |      1|    2|     3|     4|    5|     6|
|-------|-------|-----|------|------|-----|------|
|Domingo|Segunda|Terça|Quarta|Quinta|Sexta|Sábado|

A configuração dos **dias de atendimento** segue o mesmo padrão das configuração das chaves para horário de atendimento, portanto, é possível configurar chaves de atendimento para todas as equipes (padrão) ou para uma equipe específica.

|**Chave**                  | **Tipo**  | **Conteúdo**  |
|-----------------------|-------|-----------|
|desk-todos-dias | Texto | 1,2,3,4,5,6 |

**No exemplo acima, a empresa funciona de segunda à sábado**

- Configuração de dias de funcionamento para todas as equipes - desk-todos-dias;
- Configuração de abertura apenas para a equipe Treinamento - desk-Treinamento-dias;

## Como configurar os feriados:

![image](https://user-images.githubusercontent.com/44960191/114787036-7b384b80-9d55-11eb-8e78-5ced808a9133.png)

- Para configurar Feriados, basta indicar o time/fila e, no lugar do dia da semana, indicar "feriados"
- Não precisa colocar abertura/fechamento.
- Ao invés de informar hora, precisa informar a data no formato "dd/mm/aaaa"
- Caso tenha mais de um feriado, pode-se colocar todas as datas separadas por ponto-e-vírgula (;). O bot irá conferir a lista de datas informada.


- Feriado para todas as equipes - desk-todos-feriados;
- Feriado apenas para a equipe Treinamento - desk-treinamento-feriados;

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

