# Atividade-Avaliativa-3

Nome Aluno: Eutelina Cristina Ramos Machado
Matrícula: 1230115563
e-mail: 14799768735@veigadealmeida.edu.br / eutelinacrm@gmail.com

Instruções
Objetivo: Desenvolver um programa em linguagem C que seja capaz de ler uma série de números reais do teclado, realizar contagens e cálculos estatísticos baseados em critérios específicos e, em seguida, apresentar os resultados.

O Trabalho deve ser feito sozinho ou em pares. em caso de pares o NOME COMPLETO, Matricula e e-mail dos dois autores,  deve ser colocado no início do código em um comentário.

Descrição:

O programa deve ler números reais do teclado continuamente. 
A leitura deve ser encerrada quando o usuário inserir dois pontos seguidos (`..').
O programa deve contar quantos números estão abaixo de 5, quantos estão no intervalo entre 5 e 15 (inclusive) e quantos estão acima de 15.
A cada 20 números lidos, o programa deve imprimir as seguintes estatísticas:
Total de leituras abaixo de 5.
Total de leituras no intervalo de 5 a 15.
Total de leituras acima de 15.
Média dos números no intervalo de 5 a 15.
Percentual de números no intervalo de 5 a 15 em relação ao total de números lidos.
Critérios de Avaliação:

Corretude (50%): O programa deve funcionar conforme especificado, lendo números, encerrando a leitura corretamente e calculando as estatísticas pedidas.

Estilo de Código (20%): O código deve ser bem organizado e comentado, facilitando a compreensão. Variáveis devem ter nomes significativos e o código deve seguir as convenções padrões de escrita em C.

Tratamento de Erros (20%): O programa deve ser capaz de lidar com entradas inválidas sem encerrar inesperadamente. Deve avisar o usuário em caso de entradas não numéricas (exceto o ponto para encerrar) e solicitar uma nova entrada.

Documentação e Comentários (10%): O código deve ser acompanhado de um cabeçalho contendo o nome do autor, data, e uma breve descrição do programa. Comentários relevantes devem ser incluídos para explicar trechos de código complexos ou decisões importantes.

Entrega:

O trabalho deve ser entregue até a data especificada.
O código-fonte deve ser submetido em um arquivo com extensão .c.
Incluir um arquivo README com instruções para compilar e executar o programa, bem como quaisquer observações ou suposições feitas durante o desenvolvimento (este arquivo também deve incluir o nome dos participantes.
Em caso de compressão para entregar os arquivos deve usar o formato zip.

Ressolução:
#include <stdio.h>
#include <math.h>

int main() {
    // Declaração de variávies responsáveis pelo laço
    double n;        // Variável para alteração do tipo
    char entrada[3], opcao; // Para armazenar a entrada do usuário
    int sair = 1;   // Variável para validar o laço

    //Declaração de variáveis para a contagem de dados de entrada
    int menor = 0, entre = 0, maior = 0;
    int total = 0, total2 = 0;
    double soma = 0, somaTotal = 0, media =0, mediaTotal = 0, percentual = 0, desvioPadrao = 0;

    while (sair == 1) {
        printf("Digite um número (ou '..' para encerrar): ");
        scanf("%s", entrada);

        // Verifica se a entrada é '..' para encerrar a leitura
        if (entrada[0] == '.' && entrada[1] == '.') {
            sair = 0;
        }

        // Converte a entrada para double
        sscanf(entrada, "%lf", &n);
        
        // Conta os números de acordo com os critérios
        if (n < 5) {
            menor++;        //Armazena todos os números menores que 5
        } else if (n >= 5 && n <= 15) {
            entre++;        // Armazena todos os números entre o 5 e o 15
            soma += n;      // Variável que soma os números entre 5 e 15 que é utilizada no calculo da média
            total2++;       //Contem o total de elementos entre os números 5 e 15
        } else {
            maior++;        // Armazena os números maiores que 15
        }

        // Atualiza o total e a soma geral
        total++;
        somaTotal += n;

        // A cada 20 números, imprime as estatísticas
        if (total % 20 == 0) {
            printf("\nEstatísticas a cada 20 números:\n");
            printf("Total de leituras abaixo de 5: %d\n", menor);
            printf("Total de leituras entre 5 e 15: %d\n", entre);
            printf("Total de leituras acima de 15: %d\n", maior);

            //Calcula a média e o percentual dos elemententos entre 5 e 15
            if (total2 > 0) {
                media = soma / total2; 
                printf("Média dos números entre 5 e 15: %.2lf\n", media);

                percentual= total2 / total * 100;
                printf("Percentual entre 5 e 15 em relação ao total: %.2lf", percentual);
            }
            printf("\n");
        }
        
        printf("Deseja realizar cálculos estatísticos? (S/N): ");
        scanf(" %c", &opcao);  // O espaço antes de %c ignora espaços em branco
        
        //Questiona se o usuário deseja ver os calculos estatísticos
        if ((opcao == 'S') || (opcao == 's')){
            // Calcula a média e o desvio padrão
            mediaTotal = somaTotal / total;
            desvioPadrao = sqrt(somaTotal / total);
            printf("Média geral: %.2lf\n", mediaTotal);
            printf("Desvio Padrão geral: %.2lf\n", desvioPadrao);
        }else if ((opcao == 'N') || (opcao = 'n'))  
            printf("Cálculos estatísticos não serão realizados.\n");
            else
                printf("Opção inválida. Tente novamente.\n");
    }

    printf("Programa encerrado.\n");

    return 0;
}
