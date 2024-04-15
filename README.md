# Tutorial de Normalização de Array em C++

Este tutorial detalha o processo de normalização de um array em C++, onde os elementos são transformados em seus índices de classificação no array ordenado.

## Código Fonte

O código a seguir demonstra como normalizar um array de inteiros:

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    int array[] = {1,2,3,5,4};
    int n = sizeof(array) / sizeof(array[0]);
    int temp[n];
    
    memcpy(temp, array, n * sizeof(int));
    
    sort(temp, temp+n);
    
    unordered_map<int, int> mapa;
    
    int valor = 0;
    for(int i = 0; i < n; i++){
        mapa[temp[i]] = valor++;
    }
    for(int i = 0; i < n; i++){
        array[i] = mapa[array[i]];
        cout << array[i] << ' ';
    }
    cout << endl;

    return 0;
}
```

## Explicação Detalhada

### Preparação do Ambiente

- **Inclusão de Bibliotecas**: O código começa com a inclusão da biblioteca `<bits/stdc++.h>`, que engloba várias bibliotecas padrões do C++.
- **Namespace**: Utilizamos `using namespace std;` para evitar a necessidade de prefixar as funções da STL com `std::`.

### Função `main`

A função `main` é o ponto de entrada do programa, onde definimos o array a ser normalizado e realizamos os seguintes passos:

1. **Declaração e Inicialização do Array**: Definimos um array `array` com os elementos `{1,2,3,5,4}`.

2. **Cálculo do Tamanho do Array**: Calculamos o tamanho `n` do array dividindo o tamanho total do array pelo tamanho de um elemento.

3. **Criação de Array Temporário**: Criamos um array `temp` e copiamos os elementos de `array` para ele usando `memcpy`.

4. **Ordenação do Array Temporário**: Ordenamos o array `temp` em ordem crescente com a função `sort`.

5. **Criação do Mapa de Normalização**: Inicializamos um `unordered_map` chamado `mapa` e atribuímos a cada elemento único do array `temp` um índice inteiro começando de 0.

6. **Normalização do Array Original**: Atualizamos o array `array` substituindo cada um de seus elementos pelo índice correspondente no `mapa`.

7. **Exibição do Array Normalizado**: Imprimimos o array normalizado.

### Processo de Normalização

- **Ordenação do Array Temporário**: O array `temp` é ordenado para determinar a classificação dos elementos.
- **Criação do Mapa**: Baseado na posição de cada elemento no array `temp`, criamos um mapa:
  - `10` é o primeiro elemento, então `mapa[10] = 0`.
  - `11` é o segundo elemento, então `mapa[11] = 1`.
  - `12` é o terceiro elemento, então `mapa[12] = 2`.
  - `15` é o quarto elemento, então `mapa[15] = 3`.
  - `20` é o quinto elemento, então `mapa[20] = 4`.
  - `50` é o sexto elemento, então `mapa[50] = 5`.

- **Atualização do Array Original**: Usamos o mapa para atualizar o array `array`:
  - `array[0]` era `10`, agora é `mapa[10]` que é `0`.
  - `array[1]` era `20`, agora é `mapa[20]` que é `4`.
  - `array[2]` era `15`, agora é `mapa[15]` que é `3`.
  - `array[3]` era `12`, agora é `mapa[12]` que é `2`.
  - `array[4]` era `11`, agora é `mapa[11]` que é `1`.
  - `array[5]` era `50`, agora é `mapa[50]` que é `5`.

### Saída Esperada

Após a execução do código, a saída esperada é:

```
0 1 2 4 3
```

## Conclusão

Este tutorial demonstrou como normalizar um array em C++, uma técnica útil em muitos contextos de programação, como algoritmos de compressão de dados e estruturas de dados avançadas.
```
