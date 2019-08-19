# SPark
Qual o objetivo do comando cache em Spark?
O comando cache em Spark tem como objetivo alocar arquivos na memória.

O mesmo código implementado em Spark é normalmente mais rápido que a implementação equivalente em MapReduce. Por quê?
Porque o Spark armazena dados na memória enquanto o MapReduce armazena dados no disco

Qual é a função do SparkContext ?
Spark Context: o contexto é o objeto que conecta o Spark ao programa que está sendo desenvolvido. Ele pode ser acessado como uma variável em um programa que para utilizar os seus recursos.

Explique com suas palavras o que é Resilient Distributed Datasets (RDD)
Os conjuntos de dados distribuídos resilientes (RDD) são uma estrutura de dados fundamental do Spark. É uma coleção distribuída imutável de objetos. Cada conjunto de dados no RDD é dividido em partições lógicas, que podem ser calculadas em diferentes nós do cluster. Os RDDs podem conter qualquer tipo de objetos Python, Java ou Scala, incluindo classes definidas pelo usuário.

GroupByKey é menos eficiente que reduceByKey em grandes dataset. Por quê?
Porque o GroupByKey não usa nenhum parâmetro e agrupa tudo. Além disso, é uma sobrecarga para transferência de dados entre partições e já o ReduceBykey recebe apenas 1 parâmetro, que é uma função para mesclar.

** Explique o que o código Scala abaixo faz **
1. val textFile = sc . textFile ( "hdfs://..." )
2. val counts = textFile . flatMap ( line => line . split ( " " ))
3.           . map ( word => ( word , 1 ))
4.           . reduceByKey ( _ + _ )
5. counts . saveAsTextFile ( "hdfs://..." )
Linha 1 - Um arquivo-texto é lido;
Linha 2 - Cada linha é "quebrada" em uma sequência de palavras e as sequencias correspondentes a cada linha são transformadas em uma única coleção de palavras;
Linha 3 - Cada palavra é então transformada em um mapeamento de chave-valor, com chave igual à própria palavra e valor 1;
Linha 4 - Esses valores são agregados por chave, através da operação de soma;
Linha 5 - Por fim, o RDD com a contagem de cada palavra é salvo em um arquivo texto;
