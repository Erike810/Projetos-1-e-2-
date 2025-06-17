Problema 1 – Probabilidade (Lançamento de dois dados)

Verifica quantas vezes saiu (6,6).

Calcula a frequência de ocorrência.

Código C++:
cpp
Copiar
Editar
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

void simularDados(int vezes) {
    srand(time(0));
    int cont = 0;

    for (int i = 0; i < vezes; i++) {
        int dado1 = rand() % 6 + 1;
        int dado2 = rand() % 6 + 1;
        if (dado1 == 6 && dado2 == 6) {
            cont++;
        }
    }

    cout << "Número de vezes que saiu (6,6): " << cont << endl;
    cout << "Probabilidade aproximada: " << (double)cont / vezes << endl;
}

int main() {
    int n;
    cout << "Digite o número de vezes que deseja lançar os dados: ";
    cin >> n;
    simularDados(n);
    return 0;
}
 Exemplo de execução:
yaml
Copiar
Editar
Digite o número de vezes que deseja lançar os dados: 36000
Número de vezes que saiu (6,6): 973
Probabilidade aproximada: 0.027027
 Problema 2 – Adivinhe o número
 Lógica:
 O computador sorteia um número.

 O usuário tenta adivinhar, com dicas de "maior" ou "menor".

 Código C++:
cpp
Copiar
Editar
#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

void jogoAdivinhacao() {
    char jogarNovamente;

    do {
        srand(time(0));
        int segredo = rand() % 100 + 1;
        int palpite, tentativas = 0;

        cout << "Pensei em um número entre 1 e 100. Adivinhe qual é!" << endl;

        do {
            cout << "Palpite: ";
            cin >> palpite;
            tentativas++;

            if (palpite < segredo)
                cout << "O número é maior. Tente novamente.\n";
            else if (palpite > segredo)
                cout << "O número é menor. Tente novamente.\n";
            else {
                if (tentativas == 1)
                    cout << "Isso! Seu sortudo, acertou de primeira!\n";
                else
                    cout << "Isso! Você acertou com " << tentativas << " tentativas!\n";
            }

        } while (palpite != segredo);

        cout << "Quer jogar de novo (s/n)? ";
        cin >> jogarNovamente;

    } while (jogarNovamente == 's' || jogarNovamente == 'S');

    cout << "Ok, até a próxima!\n";
}

int main() {
    jogoAdivinhacao();
    return 0;
}
 Ponto Extra – Inverso: o computador adivinha
cpp
Copiar
Editar
#include <iostream>

using namespace std;

void computadorAdivinha() {
    int baixo = 1, alto = 100, resposta, tentativas = 0;
    char op;

    cout << "Pense em um número de 1 a 100, e eu vou tentar adivinhar!" << endl;

    while (baixo <= alto) {
        int palpite = (baixo + alto) / 2;
        tentativas++;
        cout << "É " << palpite << "? (s = sim, m = menor, M = maior): ";
        cin >> op;

        if (op == 's') {
            cout << "Acertei com " << tentativas << " tentativas!\n";
            break;
        } else if (op == 'm') {
            alto = palpite - 1;
        } else if (op == 'M') {
            baixo = palpite + 1;
        }
    }
}
 Problema 3 – Eleição de representante
 Código C++:
cpp
Copiar
Editar
#include <iostream>
#include <vector>
#include <map>
using namespace std;

int main() {
    int n;
    cout << "Digite o número de alunos: ";
    cin >> n;

    vector<int> votos(n);
    map<int, int> contagem;

    cout << "Digite os " << n << " votos dos alunos:\n";
    for (int i = 0; i < n; i++) {
        cin >> votos[i];
        contagem[votos[i]]++;
    }

    int representante = 0, vice = 0;
    int votosRep = 0, votosVice = 0;

    for (auto &par : contagem) {
        if (par.second > votosRep) {
            votosVice = votosRep;
            vice = representante;
            votosRep = par.second;
            representante = par.first;
        } else if (par.second > votosVice) {
            votosVice = par.second;
            vice = par.first;
        }
    }

    cout << "Representante da turma será o aluno " << representante << ", que obteve " << votosRep << " votos.\n";
    cout << "Vice-representante será o aluno " << vice << ", que obteve " << votosVice << " votos.\n";

    return 0;
}
 Problema 4 – Diário da professora
 Código C++:
cpp
Copiar
Editar
#include <iostream>
#include <vector>
#include <string>

using namespace std;

struct Aluno {
    string nome;
    vector<int> notas;
    int total;
    string situacao;
};

int main() {
    int n;
    cout << "Quantos alunos tem a turma? ";
    cin >> n;

    vector<Aluno> turma(n);

    cout << "Escreva os nomes dos alunos:\n";
    cin.ignore();
    for (int i = 0; i < n; i++) {
        getline(cin, turma[i].nome);
    }

    for (int i = 0; i < n; i++) {
        int soma = 0;
        int nota;
        cout << "Escreva as 5 notas do aluno " << turma[i].nome << ": ";
        for (int j = 0; j < 5; j++) {
            cin >> nota;
            soma += nota;
            turma[i].notas.push_back(nota);
        }
        turma[i].total = soma;
        if (soma >= 60)
            turma[i].situacao = "Aprovado";
        else if (soma < 40)
            turma[i].situacao = "Reprovado";
        else
            turma[i].situacao = "Recuperação";
    }

    cout << "\nDiário:\n";
    cout << "Nome\t\tTotal\tSituação\n";
    for (int i = 0; i < n; i++) {
        cout << turma[i].nome << "\t" << turma[i].total << "\t" << turma[i].situacao << endl;
    }

    return 0; 
    
}


Introdução
Neste trabalho, desenvolvi a solução para quatro problemas propostos em sala de aula utilizando a linguagem de programação C++. A ideia principal foi praticar a lógica de programação, estruturas de controle, uso de vetores, funções e manipulação de entradas e saídas. Cada problema trouxe desafios diferentes e contribuiu muito para meu aprendizado na disciplina.

 Problema 1 – Probabilidade com Dados
 Descrição
Simular o lançamento de dois dados e verificar quantas vezes aparece o resultado (6,6), que tem uma chance teórica de 1 em 36 (aproximadamente 2,77%).

️ Funcionamento
Usei a função rand() para simular os lançamentos dos dados. Em cada tentativa, dois números aleatórios de 1 a 6 são gerados e contados se ambos forem 6.

 Suposições
A função rand() distribui os números aleatoriamente (uso de srand() com time(0) para aleatoriedade).

Quanto mais lançamentos, mais próximo da teoria o resultado se aproxima.

 Código
(Ver código do Problema 1 acima)

 Exemplos de Execução
Entrada: 36000
Saída esperada: Em torno de 1000 vezes o resultado (6,6), com probabilidade ~0.027.

 Problema 2 – Jogo da Adivinhação
 Descrição
O computador sorteia um número de 1 a 100 e o jogador tenta adivinhar. O programa indica se o número é maior ou menor que o palpite, até o acerto.

 Funcionamento
O número aleatório é gerado com rand(). Cada tentativa é contada e comparada com o número secreto. Ao acertar, o jogo pergunta se o usuário deseja jogar novamente.

 Suposições
Entradas do usuário são válidas (entre 1 e 100).

O jogo repete enquanto o usuário quiser.

 Código
(Ver código do Problema 2 acima)

 Exemplos de Execução
makefile
Copiar
Editar
Pensei em um número entre 1 e 100. Adivinhe qual é!  
Palpite: 50  
O número é menor.  
Palpite: 25  
O número é maior.  
Palpite: 33  
Isso! Você acertou com 3 tentativas!
 Ponto Extra – Computador Adivinha
 Descrição
Dessa vez, o jogador pensa no número e o computador tenta adivinhar, usando uma estratégia de busca binária.

 Funcionamento
O computador testa o número médio entre o intervalo atual e ajusta esse intervalo conforme a resposta do usuário (maior, menor ou acertou).

 Suposições
O usuário responde corretamente com "s", "m" ou "M".

 Código
(Ver código do ponto extra acima)

️ Problema 3 – Eleição de Representante
 Descrição
Dado o voto de cada aluno (números de 1 a N), o programa identifica o aluno mais votado (representante) e o segundo mais votado (vice).

 Funcionamento
Usei um vetor para armazenar os votos e um map para contar quantos votos cada aluno recebeu. Em seguida, encontrei os dois alunos com mais votos.

 Suposições
Todos os votos são válidos e dentro do intervalo [1, N].

 Código
(Ver código do Problema 3 acima)

 Exemplo
Entrada:

makefile
Copiar
Editar
15 alunos  
Votos: 3 7 8 10 10 2 3 10 14 7 3 1 3 6 14
Saída:

makefile
Copiar
Editar
Representante: aluno 3 (4 votos)  
Vice: aluno 10 (3 votos)
 
 
 Problema 4 – Diário da Professora
 Descrição
Cada aluno fez 5 provas valendo 20 pontos. O programa soma as notas e determina a situação do aluno: aprovado (>=60), recuperação (40 a 59), ou reprovado (<40).

️ Funcionamento
Foi criado um vetor de estruturas para armazenar nome, notas, soma e situação. Para cada aluno, li as 5 notas e calculei a soma, depois apliquei a regra de classificação.

 Suposições
Notas são inteiras e de 0 a 20.

Máximo de 50 alunos.

 Código
(Ver código do Problema 4 acima)

 Exemplo de Saída
python-repl
Copiar
Editar
Nome        Total   Situação
Alexandre   85      Aprovado
Bernardo    60      Aprovado
Carlos      75      Aprovado
Daniel      30      Reprovado
Estevao     59      Recuperação
...
 Dificuldades Encontradas
Ajustar a função rand() para gerar números realmente aleatórios (resolvido com srand(time(0))).

Lidar com a contagem de votos usando map, que eu não tinha usado antes.

Formatando a saída dos nomes/alunos de forma alinhada.

Validação de entradas para evitar erros com valores fora do esperado.

 O que aprendi com o trabalho
Esse trabalho me ajudou a consolidar muitos conceitos da linguagem C++, como:

Estruturas de repetição e condição (for, if, while)

Vetores e suas manipulações

Uso de structs e map

Funções e modularização do código

Aleatoriedade com rand() e srand()

Entrada e saída com cin e cout

Mais do que aprender comandos, pude pensar logicamente em como resolver problemas reais, o que é essencial para qualquer programador iniciante.

 Conclusão
Concluir este trabalho me deu mais segurança para escrever programas completos em C++. Enfrentei dificuldades, mas consegui solucioná-las com pesquisa, testes e atenção à lógica. Com certeza saio desse exercício mais preparado para os próximos desafios da disciplina.

