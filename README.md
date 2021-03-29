# Template de Atendimento Escalável

## Qual o propósito?

O template de Atendimento Escalável tem como objetivo de promover autonomia no controle e gerenciamento de horários de atendimento sem a necessidade de realizar publicação ou desenvolvimento dentro do fluxo!

## Como Funciona?

Todas as configurações de fila deverão ser realizadas na aba de Recursos! 
![image](https://user-images.githubusercontent.com/44960191/112885419-1ddea200-90a7-11eb-8e4c-00c875a29d82.png)


Na tela de recursos, será possível de configurar:

- Horário de atendimento;
- Dias de funcionamento;
- Feriados;
- Fuso-horário

## Horário de atendimento

Todas as variáveis referente a configuração de horário de atendimento <b>devem</b> ser cadastradas com o prefixo "desk-", além disso, devem ter um indicativo se o valor é vinculado ao horário de abertura ou fechamento, por ex:
- Exemplo de variável para horário de abertura - desk-HorarioAbertura;
- Exemplo de variável para horário de fechamento - desk-HorarioFechamento;

Palavras chaves Entedidas pelo bot:

| **Abertura** | Exemplo               |
|--------------|-----------------------|
|Inicio        | desk-InicioAtendimento|    
|Abertura      | desk-HorarioAbertura  |

| **Fechamento** | Exemplo                      |
|----------------|------------------------------|
|Fechamento      | desk-FechamentoFila          |    
|Fim             | desk-FimAtendimento          |
|Final           | desk-FinalHorarioAtendimento |

A configuração dos horários ficará no seguinte padrão:
|Chave             | Tipo  | Conteúdo|
|------------------|-------|---------|
|desk-AberturaFila | Texto | 08:00   |

### Configuração de horário de atendimento por equipe

Para configurar o horário de atendimento para filas, basta inserir o nome da equipe na variável, seguindo as mesmas regras apresentadas anteriormente, por exemplo:
Para uma fila chamada Treinamento, poderíamos configurar as variáveis da seguinte forma:

- Abertura - desk-HorarioAberturaTreinamento;
- Fechamento - desk-HorarioFechamentoTreinamento;
- Dias de Funcionamento - desk-DiasFuncionamentoTreinamento;

### Configuração de horário de atendimento por dia da semana

Além de configurar o horário de atendimento por equipe, é possível configurar também por dia da semana, por exemplo:
Caso precisamos ter um horário de atendimento diferente aos sábados, podemos configurar da seguinte forma:

- Abertura - desk-HorarioAberturaSabado;
- Fechamento - desk-HorarioFechamentoSabado;

Caso seja necessário configurar horários diferentes para outros dias da semana, seguimos o mesmo padrão:
- Abertura - desk-InicioAtendimentoQuinta
- Fechamento - desk-HorarioFechamentoQuinta

Além disso, todas as regras citadas são cumulativas, portanto, podemos também configurar horário de atendimento específico para dia da semana e equipe:
- Abertura - desk-InicioAtendimentoTreinamentoQuinta
- Fechamento - desk-HorarioFechamentoTreinamentoQuinta

## Configurando dias de funcionamento:

A configuração dos dias de atendimento segue o mesmo padrão das variáveis de horário de atendimento, portanto, é possível configurar variáveis de atendimento para todas as equipes (geral) ou para uma equipe específica, segue exemplo:

- Dias de funcionamento para equipes sem configuração específica - **desk-DiasFuncionamento**
- Dias de funcionamento para equipe Treinamento - **desk-DiasFuncionamentoTreinamento** 

A configuração dos dias de funcionamento seguirá o seguinte padrão:

|Chave                  | Tipo  | Conteúdo  |
|-----------------------|-------|-----------|
|desk-DiasFuncionamento | Texto | 1,2,3,4,5 |

Onde temos a relação:
|0      |      1|    2|     3|     4|    5|     6|
|-------|-------|-----|------|------|-----|------|
|Domingo|Segunda|Terça|Quarta|Quinta|Sexta|Sábado|

## Configurando feriados:

Para configurar feriados, podemos seguir o padrão já estabelecido para as variáveis referentes ao horário de atendimento e dias de funcionamento. Portanto, é possível cadastrar feriado para todas as filas sem configuração particular, ou apenas para as equipes desejadas, ex:

- Feriado apenas para a equipe Treinamento - desk-FeriadosTreinamento;
- Feriado para as demais equipes - desk-Feriados;

Palavras chaves Entedidas pelo bot como feriado:

| **Feriado**  | Exemplo                |
|--------------|------------------------|
|Feriado(s)    | desk-Feriados          |    
|Folga         | desk-FolgaTreinamento  |

As datas deverão ser incluídas no seguinte padrão:

| **Chave**    | **Valor**            |
|--------------|----------------------|
|desk-Feriados | 12/10/2022;25/12/2022|    

Cada data deve ser separada por ';'. Não existem limite de datas cadastradas!

## Configurando o fuso-horário de atendimento:

A variável de recurso **dateTimeOffset** será responsável pela configuração do fuso-horário! 
Neste campo, deverá ser cadastrado a diferença de horas com relação ao horário de Greenwich, no horário padrão de Brasília, estamos 3 horas atrasadas com relação ao horário de Greenwich, portanto o valor cadastrado será -3!

|Chave          | Tipo  | Conteúdo |
|---------------|-------|----------|
|dateTimeOffset | Texto | -3       |

---------------------------------------------------------------------

## Detalhes Importantes

- Para que a busca pela equipe do usuário funciona da forma correta, é necessário que o nome da fila cadastrado na chave do recurso, seja exatamente igual ao nome da equipe cadastrado no Atendimento do bot. Além disso, a equipe a qual o usuário será direcionada, deverá ser indica por uma variável de extras de contato, está chave deverá ter um dos seguintes nomes: Equipe, Time, Atendente ou Fila;
- Ao cadastrar as variáveis no recurso, evite usar caracteres especiais, como acentos ou 'ç';
- Para que o template funcione da forma esperada, é necessário que todos os dados estejam respeitando os seguintes formatos:

|Data       | Hora  |
|-----------|-------|
|DD/MM/AAAA | HH:MM |

