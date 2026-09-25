## média Aritmética simples

$$M= \frac{x1+x2+...+xn}{n}$$

## média Ponderada


$$M= \frac{(X1 \cdot Peso1)+(X2 \cdot Peso2)+...+(Xn \cdot Peson)}{(Peso1+Peso2+...+Peson)}$$
## média Geométrica
Usada quando os dados representam **taxas de crescimento** ou variações multiplicativas ao longo do tempo

**Caso de uso:** taxa média de crescimento populacional, retorno médio de investimentos ao longo de vários anos, índices financeiros.

$$\sqrt[n]{X1 \cdot X2 \cdot ... \cdot Xn}$$

## média Harmônica
usada quando os dados são **taxas** (razões, como velocidade, "por unidade de algo") e é preciso compensar valores muito diferentes entre si — dá mais peso aos valores menores (o resultado sempre puxa para baixo, próximo do menor valor)

$$\frac{n}{\frac{1}{X1}+\frac{1}{X2}+ ... + \frac{1}{Xn}}$$
## média Aritmética aparada
**Definição:** ordena os dados, remove os `k` menores e `k` maiores valores, e calcula a média do que sobrou. Reduz o efeito de outliers.

**Exemplo:** salários (em milhares): 3, 3, 4, 4, 5, 5, 50 → removendo 1 de cada ponta (k=1): 3, 4, 4, 5, 5 → média = **4,2** (vs. média simples de 10,57, distorcida pelo outlier 50)

**Caso de uso:** julgamento esportivo (ex.: ginástica, patinação — remove-se nota mais alta e mais baixa), avaliação de desempenho, dados com erros de medição ou valores extremos.
$$Xap = \frac{\sum_{i=k+1}^{n-k} xi}{n-2k}$$


## Amplitude
Diferença entre maior e menor valor de um conjunto, sendo a medida de dispersão mais simples possível
**Caso de uso:** controle de qualidade rápido (verificação visual de variação), amplitude de temperatura diária, primeira checagem exploratória de um conjunto de dados.
$$R = Xmax - Xmin$$

## Variância
mede o quanto os dados se afastam, em média, da média
**Caso de uso:** avaliar a consistência de um processo de fabricação, comparar a variabilidade de retornos de dois investimentos, base matemática para desvio padrão, ANOVA e regressão.
- populacional
$$\sigma ^2 = = \frac{\sum\limits(x - \mu)^2}{n}$$
- amostral
$$ S^2 = \frac{\sum\limits(\bar{x}- xi)^2}{n-1}$$
## Desvio padrão 

- populacional
$$\sigma =\sqrt{\frac{\sum\limits(xi-x~)^2}{n}}$$
- amostral
$$S = \sqrt{\frac{\sum\limits(xi-x~)^2}{n-1}}$$

## Coeficiente de variação
desvio padrão relativo à média, em %.

$$ Coeficiente Variacao = \frac{\sigma}{x} \cdot 100$$
ou
$$ Coeficiente Variacao = \frac{S}{x} \cdot 100 $$

## Cep
O controle estatístico de processos é um conjunto de técnicas estatísticas (cartas de controle, principalmente) usado para monitorar um processo produtivo ao longo do tempo, distinguindo **variação natural** (causas comuns, inerentes ao processo) de **variação anormal** (causas especiais, que exigem investigação/ação corretiva).

### Limites de controle (o processo em si)

- **Linha Central (LC):** a média do processo, $$\bar{x}$$
- **Limite Superior de Controle (LSC):** $$\bar{x} +3\sigma$$
- **Limite Inferior de Controle (LIC):** $$\bar{x} - 3\sigma$$

São calculados **a partir dos próprios dados do processo** (o que ele realmente entrega) e respondem: "o processo está estável/previsível?". Pontos fora desses limites, ou padrões suspeitos (ex.: 7 pontos seguidos subindo, ou todos de um mesmo lado da LC), indicam processo **fora de controle estatístico** — algo mudou e precisa ser investigado.

### Limites de especificação (o que o cliente exige)
- **LSE — Limite Superior de Especificação:** valor máximo tolerado pelo cliente/projeto
- **LIE — Limite Inferior de Especificação:** valor mínimo tolerado pelo cliente/projeto
Diferença: **LSC/LIC vêm dos dados** ("o que o processo faz"); **LSE/LIE vêm da especificação do produto** ("o que é aceitável"). Um processo pode estar 100% sob controle estatístico (dentro de LSC/LIC) e, ainda assim, produzir peças fora da especificação (fora de LSE/LIE) — isso significa que o processo é estável, porém **incapaz** para aquela exigência.

### Cp e Cpk — Índices de capacidade do processo

$$Cp=\frac{LSE−LIE}{6\sigma}$$

Compara a **largura da especificação** com a **largura natural do processo** (6\sigma ). Não considera se o processo está centralizado.

- Cp < 1: processo incapaz (a dispersão é maior que a tolerância)
- Cp = 1: processo no limite
- Cp > 1,33: processo considerado capaz (regra prática comum na indústria)

$$
Cpk=min⁡(LSE−\bar{x}  \cdot3\sigma ,\bar{x} −LIE \cdot 3\sigma )$$
$$Cpk = \min\left(\frac{LSE - \bar{x}}{3\sigma}, \frac{\bar{x} - LIE}{3\sigma}\right)$$
$$Cpk=min(3\sigma LSE−\bar{x} ​,3\sigma \bar{x} −LIE​)$$

Igual ao Cp, mas penaliza processos **descentralizados** (fora do meio da especificação). É possível ter Cp bom e Cpk ruim, se o processo estiver deslocado para um dos lados — ótimo contraste visual para o vídeo.

**Caso de uso (Cp/Cpk):** aprovação de fornecedores na indústria automotiva/aeroespacial, validação de processo antes de produção em série, decisão entre "ajustar centragem" vs. "reduzir variabilidade".

### Carta X̄ (X-barra) e Carta R

Usadas em conjunto para monitorar mudanças no processos por **amostras** (subgrupos), não ponto a ponto:

- **Carta X̄:** acompanha a **média de cada subgrupo** ao longo do tempo → monitora se o processo está **centrado** (mudanças na média/tendência)
$$LSC = \bar{x} + A2 \cdot \bar{R}$$
$$LC = \bar{x}$$
$$LIC = \bar{X} - A2 \cdot \bar{R}$$
- **Carta R:** acompanha a **amplitude (range) de cada subgrupo** ao longo do tempo → monitora se a **dispersão/variabilidade** do processo está estável
$$LSC = D4 \cdot \bar{R}$$
$$LC = \bar{R}$$
$$LIC = D3 \cdot \bar{R}$$

As duas são lidas juntas: a Carta R deve ser analisada **primeiro** — se a variabilidade está fora de controle, os limites da Carta X̄ (que dependem de R̄) não são confiáveis

**Caso de uso:** linhas de produção contínua (injeção plástica, usinagem, envase), onde é mais prático amostrar em grupos pequenos e regulares do que medir 100% das peças.

criar videos manim explicando de forma visual como funciona o processo