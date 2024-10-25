# Resumo dos Seminários de SQL

Analize e estudo dos Seminários produzidos na aula passada, que que ajudam a ter um maior comtrole e compreenção do conteudo apresentado na sala de aula.

## Operadores de Agregação:

Uma transação é um conjunto de operações executadas como uma única unidade de trabalho, seguindo os princípios ACID:

Atomicidade: Todas as operações são executadas ou nenhuma é. 

Consistência: A transação leva o banco de dados de um estado válido a outro.

Isolamento: Transações são isoladas, evitando interferências entre si.

Durabilidade: Alterações confirmadas permanecem mesmo após falhas.

Início da Transação: É iniciada com um comando como START TRANSACTION;.

Execução das Operações: Operações como inserções e atualizações são realizadas, mas não são permanentes até a confirmação.

Controle de Erros: Se ocorrer um erro, pode-se usar ROLLBACK para reverter as alterações.
 #### Um exemplo de verificação de erro é:

sql

IF @@ERROR = 0 

    COMMIT; 

ELSE 

    ROLLBACK;

COMMIT: Confirma a transação, tornando as alterações permanentes.

Isolamento e Durabilidade: O nível de isolamento determina a interação entre transações, enquanto a durabilidade garante que alterações confirmadas persistam, mesmo em falhas.

## Funções de Agregação

### O que são?

Funções de agregação são ferramentas em bancos de dados que resumem e calculam informações em conjuntos de dados, operando em grupos de linhas e retornando um único valor.

Principais Funções:
COUNT(*): Conta o total de linhas.

SUM(coluna): Soma os valores de uma coluna numérica.

AVG(coluna): Calcula a média dos valores.

MIN(coluna): Identifica o menor valor.

MAX(coluna): Identifica o maior valor.

Cenários de Aplicação
Vendas por Produto: Identificar produtos que geram mais vendas.
Desempenho de Clientes: Avaliar as compras de cada cliente.
Desempenho por Região: Analisar vendas por região.
Métricas Financeiras por Departamento: Calcular receitas e despesas.
Análise de Tendências: Identificar padrões ao longo do tempo.
Cláusula GROUP BY
A cláusula GROUP BY agrupa linhas de uma tabela por valores comuns, permitindo o uso de funções de agregação.

Funcionamento:
Especificação dos Grupos: Indica colunas para formar grupos.
Aplicação de Funções: Cálculos são feitos para cada grupo.
Combinação com Outras Cláusulas: Pode ser usada com WHERE e HAVING para filtrar dados.
Combinação de GROUP BY e HAVING
Filtrar Grupos: Permite aplicar condições específicas.
Análises Profundas: Foca em grupos que atendem a critérios específicos.
Relatórios Personalizados: Exibe apenas dados relevantes.



## Indexação e Performance
### Definição:
Índices são estruturas auxiliares em bancos de dados que melhoram a velocidade de recuperação de registros, tornando as consultas mais eficientes, especialmente em sistemas com grandes volumes de dados.

Estruturas de Índice
Árvore B e B+: Estruturas que permitem operações de busca, inserção e remoção em tempo logarítmico. Na árvore B+, todos os dados estão nas folhas. 

### Funcionamento dos Índices:
Hashing: Utiliza funções hash para mapeamento rápido, mas não é eficaz para consultas de intervalo.
### Tipos de Índices:
#### Índice Único: 
Garante que os valores sejam únicos.
#### Índice Bitmap:
 Ideal para colunas com poucos valores distintos, mas com altos custos de manutenção.
#### Full-Text Index: 
Para buscas de texto completo.
Benefícios da Indexação
#### Desempenho Rápido:
 Reduz o tempo de consulta e melhora a eficiência em operações de junção.
#### Otimização de Agregações e Ordenações:

 Melhora o desempenho em operações com ORDER BY e GROUP BY.
#### Cache de Resultados:

 Consultas indexadas são frequentemente armazenadas em cache, acelerando execuções repetidas.

Custos e Impactos Negativos
#### Espaço Adicional:
 Índices consomem mais espaço no banco de dados.
#### Performance de Escrita:
 Inserções e atualizações podem ser mais lentas devido à necessidade de atualização dos índices.

#### Fragmentação:
  Índices podem se fragmentar, exigindo manutenção para manter a performance

### Quando Usar Índices:

#### Filtros e Junções:
 Índices devem ser criados em colunas frequentemente consultadas e usadas em JOINs.
#### Operações de Ordenação e Agregação:
 Melhoram o desempenho em consultas que envolvem essas operações.
### Melhores Práticas

#### Seleção de Colunas:
 Indexar colunas comumente usadas em consultas.
#### Monitoramento:
 Usar ferramentas como EXPLAIN para analisar a eficácia dos índices.
#### Cuidado com Excesso:
 Evitar índices em excesso, pois podem prejudicar a performance geral do sistema.

 ### Joins em SQL:

#### Conceito: 
Joins são operações que combinam dados de duas ou mais tabelas, baseando-se em uma condição comum, geralmente com chaves primárias e estrangeiras. São úteis para consultas com dados relacionados distribuídos em diferentes tabelas.

#### Motivos para Usar Joins:

#### Normalização de Dados: 
Em bancos de dados normalizados, os dados são divididos entre tabelas para evitar redundância, e joins ajudam a integrar essas informações.
Complexidade da Consulta: Joins permitem consultas lógicas com múltiplas tabelas.
Análises Mais Ricas: Possibilitam cálculos complexos e análises que usam dados de várias tabelas.
### Tipos de Joins:

#### INNER JOIN:
 Retorna apenas as linhas onde há correspondência entre as tabelas.
#### LEFT JOIN:
 Retorna todas as linhas da tabela à esquerda e as correspondentes da direita; onde não há correspondência, os valores da direita são NULL.

#### RIGHT JOIN:
 Retorna todas as linhas da tabela à direita e as correspondentes da esquerda; valores inexistentes da esquerda aparecem como NULL.
#### FULL OUTER JOIN:
 Combina os resultados de LEFT e RIGHT JOIN, retornando todas as linhas de ambas as tabelas; valores sem correspondência aparecem como NULL.

### Operadores Lógicos em SQL

#### O que são:
 Ferramentas usadas em consultas de dados para manipular, filtrar e definir condições. Permitem execução de operações complexas, auxiliando na construção de consultas e filtragem de dados com critérios específicos.

#### Como Funcionam: 
Operadores lógicos conectam expressões condicionais (como =, >, <) para formar condições que podem ser verdadeiras ou falsas. Os operadores principais em SQL incluem:

#### AND: Retorna verdadeiro apenas se todas as condições forem verdadeiras.
#### OR: Retorna verdadeiro se ao menos uma condição for verdadeira.
#### NOT: Inverte o valor de verdade de uma condição.
#### IN: Verifica se um valor está em uma lista específica.
#### NOT IN: Verifica se um valor não está em uma lista.
#### BETWEEN: Filtra resultados dentro de um intervalo específico.
#### LIKE: Busca padrões em colunas de texto, ideal para buscas parciais.
#### IS NULL: Verifica se um valor é nulo, ou seja, inexistente ou desconhecido.


### Subconsultas em SQL

#### O que são: 
Subconsultas são consultas SQL aninhadas dentro de uma consulta principal, usadas para recuperar dados específicos, filtrados ou agregados.

### Aplicações:

#### Filtragem de Dados:
 Para filtrar com base em critérios complexos. Exemplo: selecionar funcionários com salário acima da média.
#### Cálculos Agregados:
 Para realizar cálculos com base em dados de outras tabelas. 
 #### Exemplo:
  identificar clientes que gastaram mais que a média.
#### Verificações de Existência:
 Para verificar a existência de registros em outras tabelas, como produtos vendidos em estoque.
#### Atualizações Condicionais:
 Para atualizar registros com condições envolvendo dados de outras tabelas.
### Vantagens:

Simplifica consultas complexas.
Elimina a necessidade de tabelas temporárias.
Oferece flexibilidade na manipulação de dados.
### Desvantagens:

Subconsultas correlacionadas podem ser mais lentas, pois são processadas para cada linha da consulta principal.
Em consultas grandes, podem reduzir o desempenho.

**Funções Agregadas em SQL: SUM, AVG, COUNT, MIN e MAX**

**Introdução:** Funções agregadas são ferramentas que resumem e analisam dados, simplificando a análise de grandes conjuntos de informações e ajudando na tomada de decisões estratégicas.

**Funções Agregadas Principais:**
1. **SUM:** Calcula a soma de valores numéricos. Exemplo: total de vendas, quantidade vendida.
2. **AVG:** Calcula a média aritmética de valores. Exemplo: média de vendas por mês ou idade de clientes.
3. **COUNT:** Conta o número de registros. Pode ser uma contagem total (`COUNT(*)`) ou condicional (`COUNT(coluna)`).
4. **MIN:** Encontra o menor valor em um conjunto de dados. Exemplo: menor preço ou idade.
5. **MAX:** Encontra o maior valor em um conjunto de dados. Exemplo: maior valor de venda ou temperatura.

**Aplicações Práticas:**  
- **Análise de Vendas:** Total de vendas por região, média por pedido, quantidade de produtos vendidos.
- **Comportamento do Cliente:** Contagem de clientes por faixa etária, média de compras por cliente.
- **Análise Financeira:** Cálculo de lucro total, média de custo, número de transações.

**Resumo das Funções:**
- **SUM:** Soma valores numéricos.
- **AVG:** Calcula a média.
- **COUNT:** Conta registros.
- **MIN e MAX:** Identificam valores mínimos e máximos, úteis para encontrar outliers e limites de dados.




