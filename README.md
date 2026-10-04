# FleetCheck – Build Systems Lab

This project is intentionally incomplete. Follow the worksheet in the order given.

Expected final application output:

```
FleetCheck 1.0
Vehicles loaded: 4
Vehicles requiring service: 2
Average mileage: 37000 km
```

Do not copy the solution POM. The objective is to observe how each build change alters the result.

Evidence 1: Copy one relevant [ERROR] line to your report/README. Then identify which import in App.java
caused it.

R: Package com.fasterxml.jackson.core.type does not exist

Question : Why is this a better failure than the one from Step 1?

R: No 1º erro, o projeto nem sequer conseguia gerar código executável
devido à falta da biblioteca Jackson no pom.xml (erro de compilação).
  No 2º erro, a compilação do código fonte foi concluída com sucesso.
O projeto avançou no pipeline e a falha ocorreu numa camada de validação
mais avançada (a fase de testes unitários automatizados), detetando um
defeito de comportamento (behavioral defect).

Evidence 4: Explain what the Shade plugin changed compared with the default JAR.

R: A diferença principal é que o default JAR só guarda o nosso próprio código compilado,
enquanto o Shade Plugin cria um "Fat JAR" (um ficheiro .jar completo e autónomo).
Sem o Shade Plugin (Default): O Maven gera um JAR "leve" que contém apenas a nossa aplicação. 
Se tentarmos executá-lo, ele vai falhar porque não traz consigo as bibliotecas externas (como o Jackson).
Com o Shade Plugin: O plugin pega em todas as dependências que o projeto precisa, 
desempacota-as e junta-as todas dentro do mesmo ficheiro .jar.

Question: Which hidden environmental assumption did the wrapper remove?

R: O wrapper removeu a necessidade de ter o Maven instalado previamente no computador.
Como o wrapper descarrega e executa automaticamente a versão certa do Maven (mvnw),
a compilação funciona sempre da mesma maneira em qualquer máquina.