
# Cap 1 - Modelagem de Dados

## Explicação regras de negócio

Para o desenvolvimento do sistema de armazenamento e análise dos dados coletados pelos sensores, definimos que:
- A área de produção será dividida em setores, onde cada setor poderá cultivar uma determinada cultura e possuirá um sensor de cada tipo (umidade; fósforo e potássio; pH).
- Para cada setor é será necessário salvar as áreas, informação importante para determinar os valores de nutrientes/água aplicados por metro quadrado. 
- Cada cultura terá os valores ideais de pH, umidade e nutrientes, que serão utilizados para determinar se os valores medidos pelo sensor demandam alguma ação.
- Os sensores irão realizar as medições determinando a data e hora de cada medição, assim como os valores medidos.
- Todas ações realizadas em cada setor serão registradas, podendo ser: irrigação, aplicação de nutrientes e correção de pH.
- Para todas as ações realizadas, a data e hora deverão ser salvas.
- Poderão ser aplicados dois tipos de nutrientes: fósforo ou potássio.
- A correção de pH poderá ser de três tipos distintos, sendo as aplicações de: calcário, cal hidratada ou enxofre.

**-> Informações relevantes a serem analisadas:**<br>

- Quantidade de água gasta em um determinado período.
- Dados necessários: volume de água irrigado; data de cada aplicação.

- Quantidade de nutrientes aplicados em um determinado período:
- Dados necessários: quantidade de nutrientes aplicados; data de cada aplicação.

- Necessidade de aplicação de nutrientes:
- Dados necessários: valores mínimo e máximo ideais para o cultivo da cultura; valor medido do nutriente na plantação.

- Necessidade de irrigação:
- Dados necessário: valores mínimo e máximo ideais de umidade para o cultivo da cultura; valor medido de umidade na plantação.

- Necessidade de correção de pH:
- Dados necessários: valores mínimo e máximo ideais de pH para o cultivo da cultura; valor de pH medido na plantação

## Modelo Entidade Relacionamento

- Um setor deve ter 1 e somente 1 cultura
- Uma cultura pode ser plantada em nenhum ou em muitos setores
- Um setor  deve ter no mínimo 3 e no máximo 3 sensores
- Um sensor deve estar em no mínimo 1 e no máximo 1 setor
- Um sensor pode fazer nenhuma ou muitas medições
- Uma medição deve ser de 1 e no máximo 1 sensor
- Uma aplicação de nutrientes deve ser feita em 1 e no máximo 1 setor
- Um setor pode receber 1 e no máximo muitas aplicações de nutrientes
- Uma irrigação pode ser feita em 1 e no máximo 1 setor
- Um setor pode receber 1 e no máximo muitas irrigações
- Uma correção de pH deve ser feita em 1 e no máximo 1 setor
- Um setor pode receber 1 e no máximo muitas correções de pH

### Cardinalidades

- 1:1 entre Setores e Culturas
- 1:N entre Setores e Sensores
- 1:N entre Sensores e Medições
- 1:N entre Setores e Aplicações de nutrientes
- 1:N entre Setores e Irrigações
- 1:N entre Setores e Correções de pH

### Classificação de entidades

**Entidades fortes:**
- Setores
- Sensores
- Culturas

**Entidades fracas:**
- Medições
- Aplicações de nutrientes
- Irrigações
- Correções de pH

### Relação de atributos

#### Setores

- Id setor
- Id cultura
- Área do setor

#### Culturas

- Id cultura
- Nome da cultura
- Valor mínimo ideal de pH
- Valor máximo ideal de pH
- Valor mínimo ideal de fosforo
- Valor máximo ideal de fosforo
- Valor mínimo ideal de potássio
- Valor máximo ideal de potássio
- Valor mínimo ideal de umidade
- Valor máximo ideal de umidade

#### Sensores

- Id sensor
- Id setor
- Tipo do sensor

**-> Tipo do sensor**<br>
O tipo do sensor será definido por um campo VARCHAR, podendo ser:
- "umidade"
- "ph"
- "nutriente"

#### Medições

- Id medição
- Valor
- Data

#### Aplicações de nutrientes

- Id aplicação de nutrientes
- Id setor
- Tipo de aplicação
- Volume aplicação
- Data

**-> Tipo da aplicação**<br>
O tipo da aplicação será definido por um campo VARCHAR, podendo ser:
- "fosforo"
- "potassio"

#### Irrigações

- Id correção de pH
- Id setor
- Tipo de correção
- Volume de correção aplicada
- Data

#### Correções de pH

- Id irrigação
- Id setor
- Volume irrigação
- Data

**-> Tipo da correção**<br>
O tipo da correção será definido por um campo VARCHAR, podendo ser:
- "calcario"
- "cal hidratada"
- "enxofre"

<br>

**Modelo conceitual:**
![Modelo Conceitual vpd](https://github.com/user-attachments/assets/bfc8bfa3-c474-4d28-8bba-cb3e17a8b757)



