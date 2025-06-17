2º Problema – Locadora de Veículos 

Descrição do Problema
Uma locadora de veículos precisa de um sistema simples para controle de caixa que auxilie o balconista no dia a dia. Esse sistema deve permitir:

Definir o valor inicial em caixa.

Registrar locações com:

Placa e modelo do carro.

Quantidade de dias de locação.

Valor pago no ato (não é permitido pagar depois).

No final do expediente, gerar um relatório com:

Total de dinheiro recebido.

Valor atual no caixa.

Top 10 carros mais alugados (e quanto foi arrecadado por cada um).

️ Funcionamento do Programa
O programa é feito em C++ e funciona da seguinte forma:

Inicialização:

O usuário informa o valor inicial do caixa.

Define quantas locações deseja registrar (até 300).

Registro das Locações:

Para cada locação são registrados:

Placa do carro.

Modelo.

Dias de aluguel.

Valor pago.

Armazenamento:

As locações são armazenadas em um vetor.

É feito o controle dos modelos para contar o número de aluguéis por modelo e o valor arrecadado.

Relatório Final:

Mostra o total recebido e o valor final no caixa.

Exibe os 10 carros mais alugados com seus respectivos totais.

 Suposições Necessárias
O pagamento é sempre antecipado.

Um carro pode ser alugado mais de uma vez no mesmo dia.

Não é necessário salvar os dados em arquivos (tudo em memória).

O ranking dos carros é feito com base no modelo, não na placa.

Não é permitida mais de 300 locações por dia.

 Código Fonte
cpp
Copiar
Editar
#include <iostream>
#include <map>
#include <vector>
#include <algorithm>
#include <iomanip>

using namespace std;

struct Locacao {
    string placa;
    string modelo;
    int dias;
    float valor;
};

struct CarroInfo {
    int totalAlugueis = 0;
    float valorTotal = 0.0;
};

bool compararPorAluguel(pair<string, CarroInfo> a, pair<string, CarroInfo> b) {
    return a.second.totalAlugueis > b.second.totalAlugueis;
}

int main() {
    float caixaInicial, caixaAtual;
    int quantidade;
    vector<Locacao> locacoes;
    map<string, CarroInfo> carros;

    cout << "=== Controle de Caixa da Locadora ===\n";
    cout << "Informe o valor inicial no caixa: R$ ";
    cin >> caixaInicial;
    caixaAtual = caixaInicial;

    cout << "\nQuantas locações deseja registrar hoje? (máx 300): ";
    cin >> quantidade;
    if (quantidade > 300) {
        cout << "Quantidade excede o máximo permitido!\n";
        return 1;
    }

    for (int i = 0; i < quantidade; ++i) {
        Locacao l;
        cout << "\nLocação " << (i+1) << ":\n";
        cout << "Placa do carro: ";
        cin >> l.placa;
        cout << "Modelo do carro: ";
        cin.ignore();
        getline(cin, l.modelo);
        cout << "Dias de aluguel: ";
        cin >> l.dias;
        cout << "Valor pago (R$): ";
        cin >> l.valor;

        locacoes.push_back(l);
        caixaAtual += l.valor;

        carros[l.modelo].totalAlugueis++;
        carros[l.modelo].valorTotal += l.valor;
    }

    
    cout << "\n=== Relatório do Dia ===\n";
    cout << fixed << setprecision(2);
    cout << "Valor Inicial do Caixa: R$ " << caixaInicial << endl;
    cout << "Total Recebido no Dia: R$ " << (caixaAtual - caixaInicial) << endl;
    cout << "Valor Final no Caixa: R$ " << caixaAtual << endl;

    
    vector<pair<string, CarroInfo>> listaCarros(carros.begin(), carros.end());
    sort(listaCarros.begin(), listaCarros.end(), compararPorAluguel);

    cout << "\nTop 10 Carros Mais Alugados:\n";
    cout << left << setw(25) << "Modelo" << setw(10) << "Alugueis" << "Valor Recebido\n";
    cout << "----------------------------------------------------\n";

    for (size_t i = 0; i < min((size_t)10, listaCarros.size()); ++i) {
        cout << left << setw(25) << listaCarros[i].first
             << setw(10) << listaCarros[i].second.totalAlugueis
             << "R$ " << listaCarros[i].second.valorTotal << endl;
    }

    return 0;
}
 Exemplos de Execução
 Exemplo 1:
Entrada:

yaml
Copiar
Editar
Valor inicial do caixa: 1000
Quantidade de locações: 3

Locação 1: Placa ABC1234, Modelo: Gol, Dias: 2, Valor: 200
Locação 2: Placa DEF5678, Modelo: Onix, Dias: 3, Valor: 300
Locação 3: Placa XYZ9988, Modelo: Gol, Dias: 1, Valor: 150
Saída:

ruby
Copiar
Editar
Valor Inicial do Caixa: R$ 1000.00
Total Recebido no Dia: R$ 650.00
Valor Final no Caixa: R$ 1650.00

Top 10 Carros Mais Alugados:
Modelo                   Alugueis  Valor Recebido
----------------------------------------------------
Gol                      2         R$ 350.00
Onix                     1         R$ 300.00
️ Situações Onde o Programa Pode Falhar
Situação	Comportamento
Usuário insere mais de 300 locações	Exibe erro e termina
Entrada inválida (texto onde se espera número)	Pode causar falha (não tratado)
Modelos com nome idêntico porém em letras diferentes	São tratados como diferentes

 Dificuldades Encontradas e Soluções
Dificuldade	Solução
Entrada de nomes com espaços	Uso de getline() após cin.ignore()
Ordenar modelos por frequência	Conversão de map para vector + sort()
Limitar a 10 carros	Uso de min(10, lista.size())

 O Que Aprendi com o Trabalho
Organizar dados com struct, vector e map.

Formatar saída com iomanip.

Manipular strings e validar limites.

Práticas de ordenação personalizada com sort().
