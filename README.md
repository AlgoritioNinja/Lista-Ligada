# Explicação do Código em C: Lista Ligada

Este código demonstra como implementar uma **lista ligada** simples em C, incluindo a criação de nós, conexão entre eles, exibição da lista e liberação da memória alocada.

---

## Código

```c
#include <stdio.h>
#include <stdlib.h>

// Estrutura de um nó da lista ligada
typedef struct Node {
    int dado;
    struct Node* proximo;
} Node;

// Função para criar um novo nó
Node* criarNo(int valor) {
    Node* novoNo = (Node*)malloc(sizeof(Node));
    novoNo->dado = valor;
    novoNo->proximo = NULL;
    return novoNo;
}

// Função para imprimir a lista
void imprimirLista(Node* cabeca) {
    Node* atual = cabeca;
    printf("Elementos da lista ligada: ");
    while (atual != NULL) {
        printf("%d -> ", atual->dado);
        atual = atual->proximo;
    }
    printf("NULL\n");
}

int main() {
    // Criando nós e formando a lista
    Node* primeiro = criarNo(10);
    Node* segundo = criarNo(20);
    Node* terceiro = criarNo(30);

    // Conectando os nós
    primeiro->proximo = segundo;
    segundo->proximo = terceiro;

    // Imprimindo a lista
    imprimirLista(primeiro);

    // Liberando a memória alocada
    free(primeiro);
    free(segundo);
    free(terceiro);

    return 0;
}
