# Projeto: Estágio na Y.Afisha

*Depois de conseguir apresentar um desempenho brilhante durante o percurso Tripleten. Foi oferecida a você a oportunidade de realizar um programa de estágio no **Departamento de Análise da Y.Afisha**. No primeiro dia, o **departamento de marketing** lhe dará uma tarefa para ajudá-los a **otimizar o orçamento de custos de marketing**.*

*A sua frente estão disponíveis dados de janeiro de 2017 a dezembro de 2018 que consistem em 3 arquivos contendo:*
- **Logs de servidores**/registro de visita ao site Y.Afisha;
- Dados do **pedido**;
- Marketing **estatísticas de custos**.

*Ao completar esta tarefa, eles esperam que você aprenda:*
- Comportamento do usuário Y.Afisha;
- Análise de coorte;
- Receita gerada;
- Quando todos os custos de marketing forem compensados.

**Instruções do projeto**
1. ***Baixar dados e prepará-los para análise***
    - Armazene dados de visitas, pedidos e despesas em variáveis.
    - Otimize os dados que você possui para fins de análise.
    - Certifique-se de que cada uma de suas colunas seja apresentada no tipo de dados correto.
    - Caminho de arquivo:
        - /datasets/visits_log_us.csv
        - /datasets/orders_log_us.csv
        - /datasets/costs_us.csv

2. ***Compile relatórios e calcule métricas:***
    - **Produtos**
        - Quantas pessoas **usam** o produto **todos os dias**, **semana** e **mês**?
        - Qual é o número de **sessões por dia**? (Um usuário pode ter mais de uma sessão).
        - Qual é a **duração** de **cada sessão**?
        - Com que frequência os **usuários voltam** a usar o produto?

   - **Vendas**
        - **Quando** as pessoas **começam** a fazer compras?
            - **Nota Adicional**: Na **análise de KPI**, geralmente estamos interessados ​​em saber o tempo que **decorre** do momento em que o **cadastro** é feito até a **conversão** ocorrer ou quando um usuário autorizado muda para um cliente. Por exemplo, se o primeiro cadastro e compra ocorreram no mesmo dia, esse usuário poderia ser incluído na categoria h0 Conversão. Caso a primeira compra ocorra no dia seguinte, a categoria também será h1 Conversões. Você pode usar qualquer abordagem que permita comparar conversões de diferentes coortes, para que possa determinar qual coorte ou canal de marketing é mais eficaz.
        - Quantos **pedidos** eles fazem **durante um período**?
        - Qual é o **tamanho médio de compra**?
        - Quanto dinheiro eles contribuem? (**LTV**)

    - **Marketing**
        - Quanto **dinheiro é gasto**? Geral/por fonte/ao longo do tempo
        - Quanto custa o **custo de aquisição de clientes** (CAC) de cada fonte?
        - Quão rentável é o investimento? (**ROI**)

     *Crie um **gráfico** que mostre **como essas métricas diferem** para **dispositivos diferentes** e **origens de anúncios**, bem como como elas **mudaram ao longo do tempo**.*

3. ***Escrever a conclusão:*** *diga aos especialistas de marketing quanto dinheiro investir e **onde deve ser investido**.*
   - Quais **fontes/plataformas** você **recomendaria**?
   - Dê razões para apoiar a sua escolha:
       - Em quais **métricas** você se concentra?
       - **Por que**?
       - Que **conclusões** você tira depois de encontrar os valores dessas métricas?

**Dicionário de dados**
**A tabela de visitas (logs do servidor com dados de acesso ao site):**
- `Uid` — Identificador exclusivo do usuário
- `Device` — Dispositivo do usuário
- `Start Ts` — Data e hora de início da sessão
- `End Ts` — Data e hora de término da sessão
- `Source Id` — O ID da fonte de publicidade, a fonte com a qual o usuário chega ao site

**A tabela de pedidos (dados do pedido):**
- `Uid` — Identificador exclusivo do usuário que faz um pedido
- `Buy Ts` - Data e hora do pedido
- `Revenue` — receita de Y.Afisha com pedido

**A tabela de custos (dados sobre despesas de marketing):**
- `source_id` — Identificador da origem do anúncio
- `dt` — Data
- `costs` — Despesas desta origem de anúncios neste dia

**Conclusão**
**Visão geral do dataframe df_visits:**
- *O dataframe contém cinco colunas `device`, `end_ts`, `source_id`, `start_ts` e `user_id` com 50415 linhas cada uma do tipo object, int64, object ou uint64. Alguns nomes de colunas foram alterados e o tipo de dados das colunas `end_ts` e `start_ts` foi alterado de objeto para data e hora. O dataframe não mostra nenhuma diferença significativa entre a média e a mediana, e nenhum dado duplicado ou ausente.*

**Visão geral do dataframe df_orders:**
- *O dataframe contém três colunas, `user_id`, `revenue` e `orders_ts`, com 50415 linhas cada. As colunas foram alteradas de `buy ts` para `orders_ts`, e o tipo de dados de `orders_ts` foi alterado de object para datetime. E nenhum dado duplicado ou ausente.*

**Visão geral do dataframe df_costs:**
- *O dataframe contém três colunas, `source_id`, `dt` e `costs`, com 2.542 linhas cada. As colunas foram alteradas de `dt` para `date`, o tipo de dados de `date` foi alterado de objeto para datetime e não há dados duplicados ou ausentes.*

*Na **análise do produto**, respondemos à pergunta calculando as seguintes métricas.*
- **Usuário ativo**
    - Diariamente: 907 usuários
    - Semanalmente: 5.825 usuários
    - Mensalmente: 23.228 usuários
- **Sessão por dia**: 987 sessões
- **Duração da sessão**:
    - Média: 10 minutos
    - Modo: 60 segundos
- **Fator pegajoso**:
    - Semanal: 15,59%
    - Mensal: 3,91%

Na **análise de vendas**, respondemos à pergunta calculando as seguintes métricas.

- **Prazo de entrega** - Tempo decorrido desde o início da primeira sessão até a decisão final de compra do produto
    - Média: 4 horas e 44 minutos
    - Mediana: 20 minutos
    - Máx.: 24 horas
- **Análise de coorte**
    - Contagem de pedidos: a queda significativa após o primeiro mês para cada coorte mostra que a maioria dos usuários não está fazendo compras repetidas.
    - Receita média por usuário: Esta análise mostra que o comprador que decidiu repetir a compra fez um pedido em volume maior do que o primeiro pedido.
    - Valor vitalício: cada grupo começa com um LTV quase semelhante, experimenta queda na receita média por comprador no mês seguinte e continua aumentando cumulativamente em valor.

***Após realizar análises de produtos, vendas e marketing. Recomendamos que o departamento de marketing:***
- *Invista **mais** dinheiro em **fontes de anúncios** que tenham **baixo custo de aquisição de clientes**, como fontes de anúncios 2, 3 e 4*;
- *Começar a investir em **fontes de anúncios com alto número de visitantes** que não foram investidas (fontes de anúncios 9 e 10)*;
- *Invista **menos** em fontes de anúncios com **alto custo de aquisição de clientes**, como a fonte de anúncios 6*.
