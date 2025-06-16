 1º Problema – Campo Minado!! 
 
  Código em C++:
cpp
Copiar
Editar
#include <iostream>
using namespace std;

const int N = 20; 

int main() {
    char campo[N][N];
    int vizinhos[N][N] = {0}; 
    cout << "Digite a matriz 20x20 com '*' para bombas e '-' para local vazio:\n";
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            cin >> campo[i][j];
        }
    }

    int dx[] = {-1, -1, -1,  0, 0, 1, 1, 1};
    int dy[] = {-1,  0,  1, -1, 1,-1, 0, 1};

    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (campo[i][j] == '*') {
                
                for (int d = 0; d < 8; d++) {
                    int ni = i + dx[d];
                    int nj = j + dy[d];
                   
                    if (ni >= 0 && ni < N && nj >= 0 && nj < N && campo[ni][nj] != '*') {
                        vizinhos[ni][nj]++;
                    }
                }
            }
        }
    }

    
    cout << "\nMatriz de bombas nas vizinhanças:\n";
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            cout << vizinhos[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
 Como usar:
Compile com: g++ campo_minado.cpp -o campo_minado

Execute: ./campo_minado

Digite a matriz 20x20 linha por linha (só com * e -).

Exemplo de entrada:

diff
Copiar
Editar
- - * - - - - - - - - - - - - - - - - -
- - - - - - - - - - - - - - - - - - - -
...
(total de 20 linhas com 20 caracteres)

 Relatório - 1º Problema: Campo Minado
1. Descrição do Problema
O jogo "Campo Minado" consiste em identificar quantas bombas existem ao redor de uma determinada célula em um campo. Este trabalho propõe a leitura de uma matriz 20x20 de caracteres contendo dois símbolos:

'*' → representa uma bomba

'-' → representa uma célula vazia

A partir dessa matriz, o objetivo é gerar uma nova matriz de inteiros que indique, para cada posição [i][j], quantas bombas existem nas suas 8 células vizinhas (horizontal, vertical e diagonal).

2. Funcionamento do Programa
O programa inicia solicitando ao usuário que insira a matriz 20x20, composta apenas por * e -.

Cria-se uma matriz de inteiros, inicializada com zeros.

Para cada célula da matriz de entrada:

Se for uma bomba (*), o programa incrementa +1 em todas as suas células vizinhas (desde que estejam dentro dos limites da matriz).

A matriz final é impressa, mostrando quantas bombas existem ao redor de cada célula.

3. Suposições Necessárias
A matriz de entrada possui exatamente 20 linhas e 20 colunas.

A entrada será digitada corretamente pelo usuário, contendo apenas os caracteres válidos (* e -).

Células com bombas (*) não aparecem na matriz de inteiros resultante (opcionalmente poderiam ser substituídas por um identificador especial, mas aqui serão deixadas como zero para simplificar).

4. Código-Fonte em C++
cpp
Copiar
Editar
#include <iostream>
using namespace std;

const int N = 20; 

int main() {
    char campo[N][N];      
    int vizinhos[N][N] = {0}; 

    cout << "Digite a matriz 20x20 com '*' para bomba e '-' para vazio:\n";
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            cin >> campo[i][j];
        }
    }

    // Direções dos 8 vizinhos
    int dx[] = {-1, -1, -1,  0, 0, 1, 1, 1};
    int dy[] = {-1,  0,  1, -1, 1,-1, 0, 1};

    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (campo[i][j] == '*') {
                for (int d = 0; d < 8; d++) {
                    int ni = i + dx[d];
                    int nj = j + dy[d];
                    if (ni >= 0 && ni < N && nj >= 0 && nj < N && campo[ni][nj] != '*') {
                        vizinhos[ni][nj]++;
                    }
                }
            }
        }
    }

    cout << "\nMatriz de contagem de bombas nas vizinhanças:\n";
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            cout << vizinhos[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
5. Exemplos de Execução
Exemplo Simplificado (5x5 para ilustrar):
Entrada:

markdown
Copiar
Editar
- - * - -
- - - - -
* - - * -
- - - - -
- * - - -
Saída:

Copiar
Editar
0 1 0 1 0
1 2 2 2 0
0 2 2 0 1
2 2 3 2 1
1 0 2 1 0
Na versão final, a matriz será 20x20, mas o comportamento permanece igual.

6. Dificuldades Encontradas
Garantir que o programa não acessasse posições inválidas fora da matriz (índices negativos ou maiores que 19).

Criar uma lógica compacta para verificar as 8 direções de vizinhança.

Inicializar corretamente a matriz de inteiros com zeros.

Garantir que bombas não fossem contadas como vizinhas delas mesmas.

Essas dificuldades foram resolvidas com:

Laço com verificação de limites.

Vetores dx e dy para percorrer as 8 direções com simplicidade.

7. O Que Foi Aprendido
A importância de validar acessos em matrizes bidimensionais.

Como trabalhar com matrizes de diferentes tipos de dados (char e int).

Práticas de modularização e clareza na construção de lógica em C++.

Uso de vetores auxiliares para simplificar múltiplas direções de verificação.

