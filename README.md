# Propagação de Epidemias em Redes Complexas

Este projeto simula a propagação de epidemias em redes complexas usando os modelos **SI**, **SIR** e **SIS**. O objetivo é analisar como diferentes topologias de rede influenciam a disseminação de uma epidemia e comparar estratégias de imunização em redes com hubs.

O projeto foi desenvolvido em **Python**

## Redes2

* redes **ER** (*Erdős-Rényi*);
* redes **BA** (*Barabási-Albert*);
* redes **WS** (*Watts-Strogatz*) com diferentes valores de `p`;
* redes **BA não-lineares** com diferentes valores de `alpha`;
* estratégias de imunização aleatória e imunização dos maiores hubs.

## Modelos epidemiológicos

Foram implementados três modelos:

### SI

No modelo **SI**, os vértices passam de suscetíveis para infectados:

```text
S -> I
```

Nesse modelo, não há recuperação. Uma vez infectado, o vértice permanece infectado até o fim da simulação.

### SIR

No modelo **SIR**, os vértices passam de suscetíveis para infectados e depois para recuperados:

```text
S -> I -> R
```

Os vértices recuperados não voltam a ser infectados.

### SIS

No modelo **SIS**, os vértices passam de suscetíveis para infectados e depois voltam a ser suscetíveis:

```text
S -> I -> S
```

Nesse modelo, os vértices podem ser reinfectados.

## Redes utilizadas

As simulações consideram redes com:

```text
N = 1000
<k> = 8
```

As principais topologias analisadas foram:

* **ER**: rede aleatória, com conexões distribuídas aleatoriamente;
* **BA**: rede com hubs, gerada por ligação preferencial;
* **WS**: rede de mundo pequeno, com conexões locais e atalhos aleatórios;
* **BA não-linear**: variação da rede BA, controlada pelo parâmetro `alpha`.

## Experimentos realizados

### 1. Propagação de epidemias

Foram simulados os modelos **SI**, **SIR** e **SIS** nas redes:

* ER;
* BA;
* WS com `p = 0.001`;
* WS com `p = 0.01`.

Para cada modelo, foi analisada a curva da fração de infectados ao longo do tempo.

### 2. Influência da topologia

Foi analisado o modelo **SIR** em diferentes topologias:

* ER;
* BA;
* WS com `p = 0.001`;
* WS com `p = 0.1`;
* BA não-linear com `alpha = 0.5`;
* BA não-linear com `alpha = 1.5`.

O objetivo foi verificar como a estrutura da rede influencia a velocidade e a intensidade da propagação da epidemia.

### 3. Imunização

Foi utilizada uma rede **BA** com `N = 1000` e grau médio `<k> = 8`.

Foram comparadas duas estratégias de imunização:

1. imunização aleatória de `x%` dos vértices;
2. imunização dos `x%` maiores hubs da rede.

Para cada valor de `x`, o processo foi repetido 10 vezes, calculando média e desvio padrão da fração final de recuperados.

## Principais resultados

Os resultados indicam que a topologia da rede influencia diretamente a propagação da epidemia.

Redes com hubs, como a rede **BA**, favorecem uma disseminação mais rápida, pois poucos vértices altamente conectados conseguem transmitir a infecção para muitas partes da rede. Já redes **WS** com baixo valor de `p` apresentam propagação mais lenta, pois possuem uma estrutura mais local e poucos atalhos aleatórios.

Na análise de imunização, a estratégia de imunizar os maiores hubs foi mais efetiva do que a imunização aleatória. Isso ocorre porque, em redes BA, os hubs concentram muitas conexões e funcionam como pontos centrais de disseminação. Ao imunizar esses vértices, a rede perde caminhos importantes de transmissão.

## Bibliotecas utilizadas

* Python
* NumPy
* NetworkX
* Matplotlib
* EoN
