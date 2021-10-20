﻿# Trabalho 01: Lista básica de programação em C++


#  Introdução

Esse exercício tem por objetivos fazer você praticar sua habilidade de **interpretar especificações de problemas**, aliada a sua capacidade de **projetar** e **implementar algoritmos**.

Além disso, o desenvolvimento desse trabalho oferecer uma oportunidade prática para utilizar elementos básicos de programação em C++, como laços, condicionais simples e composto, tipos de dados básicos e heterogêneos, expressões lógicas, passagem de parâmetros, criação de funções, leitura de escrita de informações a partir da entrada e saída padrão, dentre outros.

Adicionalmente, você deverá ter contato com alguns elementos da STL (_Standard Template Library_) do C++, mais especificamente o uso de _vetor dinâmico_ e _estático_, bem como alguns algoritmos básicos de manipulação de dados, dependendo das necessidades dos algoritmos que você projetar.

# Suas Tarefas

Nesse exercício você deve implementar todos os itens solicitados na lista de exercício disponível [aqui](docs/lista_01.pdf).

Para facilitar a implementação de suas respostas, você vai encontrar nesse repositório o código de suporte organizado em várias pastas, uma para cada questão da lista. Esse código já está preparado para compilar cada projeto individualmente através do uso de `cmake` e contém indicações sobre o que você precisa alterar através de comentários como `// TODO` espalhados por alguns arquivos `.cpp` e `.h`. Para você usufruir dessa infraestrutura de compilação e testagem disponível, é importante que você **não altere nenhum arquivo além do que for indicado nesse documento**.

Em resumo, sua tarefa consiste em:
1. Implementar todos as questões requisitadas na lista, incluindo seu código nos locais apropriados em cada pasta.
2. Editar o arquivo [`autor.md`](autor.md) e adicionar suas informações pessoais na [Seção Identificação Pessoal](autor.md/#identificação-pessoal).
3. Marcar cada uma das questões que você conseguiu resolver, na [Seção Questões Finalizadas](autor.md/#questões-finalizadas) do arquivo [`autor.md`](autor.md).
4. Subir para o repositório (_commit_ + _push_) suas respostas, para que elas possam ser baixadas e corrigidas após o prazo final do exercício.

# Compilando e Executando

Nessa seção abordamos o procedimento necessário para compilar e executar o código inicial fornecido com o exercício.

## Tipos de Questões
Conforme explicado no [PDF da lista de exercício](docs/lista_01.pdf) existem duas categorias de exercícios: implementação de **programa** e implementação de **função**.

Para os exercícios que solicitam a implementação de um programa, você deve editar apenas o arquivo `src/main.cpp`. Se você desejar criar outros arquivos `.cpp` para modularizar melhor seu projeto você pode fazê-lo; nesse caso lembre-se de alterar o script do `cmake` correspondente de maneira a incluir o novo arquivo fonte na lista de dependências do target `${APP_NAME}` com o comando `target_sources( ${APP_NAME} PRIVATE "seu_arquivo.cpp" )`.

Para os exercícios que solicitam a implementação de uma função, você precisa apenas editar o arquivo `src/function.cpp`. Lá você vai encontrar o copo vazio da função que precisa ser desenvolvida.

## Dependências

Para você poder compilar e executar os testes preparados para o exercício é necessário os seguintes requisitos:
+ [GNU gcc](https://gcc.gnu.org/), [clang](https://clang.llvm.org/), ou outro: compilador C++.
+ [cmake](https://cmake.org/): para gerar os arquivos _Makefiles_, que gerenciam a compilação otimizada do projeto.
+ [Python](https://www.python.org/): para executar o script de teste de comparação de saída gerada/esperada.
+ [Catch2](https://github.com/catchorg/Catch2): biblioteca para viabilizar testes unitários. Mas não se preocupe que os arquivos necessários para usar essa biblioteca de testes já estão incluídos no projeto entregue e, portanto, você não precisa instalar nada.

## Instruções Categoria Implementação de Programa

Vamos considerar que desejamos compilar e testar o projeto `Intervalos`, que requer a criação de um programa. Cada pasta de projeto que requer um programa como resposta está organizado da seguinte forma:
```
+─intervalos          ---> Nome da posta do projeto
  ├─── CMakeLists.txt ---> Script de configuração do cmake.
  ├─── build          ---> Pasta onde os executáveis serão gerados. [será criada]
  ├─── data_expected  ---> Pasta que contém os arquivos de saída com as respostas corretas.
  ├─── data_in        ---> Pasta que contém os arquivos de entrada para os testes.
  └─── src            ---> Pasta que contém arquivo que você precisa editar.
       └─── main.cpp  ---> Arquivo que precisa ser alterado para conter sua resposta. [editar]
```

A partir da pasta que contém as subpastas de cada questão faça:

1. Edite o arquivo `intervalos/src/main.cpp` e implemente a solução do problema.
2. Entre na pasta do projeto, no caso `intervalos`:
```
cd intervalos
```
3. Execute o comando do `cmake` para gerar os arquivos intermediários. Esse comando cria a pasta `build` que conterá os arquivos _Makefile_ e onde o executável será gerado.
```
cmake -S . -B build
```
Possível saída:

<!-- <img src="./pics/cmake_prep.png" width="350"> -->
![cmake preparation](./pics/cmake_prep.png)

4. Execute o comando do `cmake` para **compilar** o projeto `intervalos` dentro da pasta `build`. Esse comando criará um executável dentro de `build` chamado (de forma genérica) de `program`.
```
cmake --build build
```
Possível saída:

<!-- <img src="./pics/cmake_build_int.png" width="550"> -->
![cmake building](./pics/cmake_build_int.png)


5. Se houver erro de compilação, corrija e volte ao passo anterior. Se a compilação for bem sucedida, prossiga com o comando abaixo para entrar na pasta `build` e rodar os testes.
```
cd build
make verify
```
6. Observe os resultados dos testes do passo anterior. Se algum teste falhar você deve corrigir o problema e compilar o projeto novamente, como descrito no passo 4. Se você estiver na pasta `build` e desejar compilar novamente, pode executar os comandos abaixo, ao invés de retornar ao passo 4 (que deve ser executado de fora do `build`)
```
make
make verify
```
Se os testes forem bem sucedidos, você deve encontrar uma saída como essa abaixo:

<!-- <img src="./pics/io_test.png" width="550"> -->
![IO testing](./pics/io_test.png)

## Instruções Categoria Implementação de Função

Vamos considerar que desejamos compilar e testar o projeto `Fibonacci`, que requer a criação de uma função. Essa pasta está organizada da seguinte forma:
```
+─fibonacci               ---> Nome da posta do projeto
  ├─── CMakeLists.txt     ---> Script de configuração do cmake.
  ├─── build              ---> Pasta onde os executáveis serão gerados. [será criada]
  ├─── tests              ---> Pasta que contém os arquivos de teste unitário.
  └─── src                ---> Pasta que contém arquivo que você precisa editar.
       ├─── function.h    ---> Arquivo cabeçalho com definição da assinatura da função. 
       └─── function.cpp  ---> Arquivo que precisa ser alterado para conter sua resposta. [editar]
```

1. Edite o arquivo `fibonacci/src/function.cpp` e implemente a solução do problema.
2. Entre na pasta do projeto, no caso `fibonacci`:
```
cd fibonacci
```
3. Execute o comando do `cmake` para gerar os arquivos intermediários. Esse comando cria a pasta `build` que conterá os arquivos _Makefile_ e onde o executável será gerado.
```
cmake -S . -B build
```
4. Execute o comando do `cmake` para **compilar** o projeto `fibonacci` dentro da pasta `build`. Esse comando criará dentro da pasta `build` uma biblioteca estática contendo a sua função, `libfunc.a`, e um executável para executar os testes unitários, `tests/all_tests`.
```
cmake --build build
```
Possível saída:

<!-- <img src="./pics/cmake_build_fib.png" width="550"> -->
![cmake build Fibonacci](./pics/cmake_build_fib.png)

5. Se houver erro de compilação, corrija e volte ao passo anterior. Se a compilação for bem sucedida, prossiga com o comando abaixo para entrar na pasta `build` e executar os testes.
```
cd build
make run_all_tests
```

6. Observe os resultados dos testes do passo anterior. Se algum teste falhar você deve corrigir o problema e compilar o projeto novamente, como descrito no passo 4. Se você estiver na pasta `build` e desejar compilar novamente, pode executar os comandos abaixo, ao invés de retornar ao passo 4 (que deve ser executado de fora do `build`)
```
make
make run_all_tests
```
Se os testes forem bem sucedidos, você deve encontrar uma saída como essa abaixo:

<!-- <img src="./pics/unit_test.png" width="550"> -->
![unit testing](./pics/unit_test.png)

# Submissão do Trabalho

A submissão do trabalho deve ser feita de 2 formas:
1. Crie um arquivo compactado com todas as pastas contidas no pasta principal `list_basics+c++` e envie esse arquivo via Tarefa Virtual do SIGAA. **Não esqueça de remover a pasta `build` com todos os executáveis antes de compactar!!!**
2. Registre (_commit_) todo o seu trabalho para o repositório do GitHub Classroom associado a esse [projeto]().

--------
&copy; DIMAp/UFRN 2021.
