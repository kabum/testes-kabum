# Atividade Back-end KaBuM!

<div style="text-align:center">
    <img src="https://static.kabum.com.br/conteudo/faq/img/banner-faq.jpg">
</div>


## Contexto

Fundado em 2003, o KaBuM! foi um dos pioneiros no comércio eletrônico brasileiro e hoje é o maior e-commerce do segmento de tecnologia na América Latina. Desde sua criação, a empresa é formada por histórias e conquistas de um time obcecado por agilidade, qualidade de atendimento, velocidade de entrega e respeito pelo consumidor.

Com preços imbatíveis e mais de 20 mil produtos em seu catálogo, o KaBuM! está sempre à frente e traz em primeira mão os melhores lançamentos do mercado mundial. São mais de 8 milhões de pessoas atendidas e entregas realizadas em todas as regiões do país, totalizando mais de 5.000 cidades.

O e-commerce é um dos sites mais acessados do país e lidera o ranking das lojas virtuais mais recomendadas pelos consumidores brasileiros, no segmento de tecnologia, com os principais índices de avaliação e selos de qualidade da internet.

Além do e-commerce, o KaBuM! é um grande incentivador dos esportes eletrônicos, sendo responsável pela criação de uma das maiores equipes de League of Legends do Brasil, a KaBuM! e-Sports, tetracampeã nacional e a primeira representante brasileira no Campeonato Mundial. A equipe de Free Fire da organização também já ganhou a liga NFA.

## O desafio

O KaBuM necessita realizar cotações de fretes em suas transportadoras parceiras e você, como desenvolvedor back-end, deve desenvolver uma API REST que será utilizada pelo site para a consulta de opções de transportes dos produtos.

O candidato terá que ser capaz de construir uma API REST.

O teste está baseado em uma consulta dos valores de frete para cada transportadora existente conforme as especificações das **dimensões** e **peso** do produto.

Cada transportadora terá seus requisitos e o retorno deverá ser conforme o exemplo “output”, uma listagem com as transportadoras e seus valores de frete. Se o produto **não** estiver de acordo com tal transportadora, ela **não** deverá ser retornada.

A  requisição deverá ser via **POST** e as informações do produto deverão ser enviadas body da requisição, como JSON.

```json
{
    "dimensao": {
                    "altura":102,
                    "largura":40
                },
    "peso":400
}
```
A medida da dimensão é **centímetro (cm)** e a medida do peso é **gramas (g)**.


Caso nenhuma transportadora atenda o produto, deverá ser retornada uma lista vazia.

---

## Requisitos para construção da API
- Disponibilizar em repositório público (GitHub) o resultado do projeto.

---

## Validações
Ao receber uma requisição, a **API** deve realizar as seguintes validações para retornar ou não a opção do frete:

- Validação de altura máxima e mínima para cada opção de frete
- Validação de largura máxima e mínima para cada opção de frete
- Validação se o peso do produto é maior que 0.

Caso alguma validação não seja satisfeita, a **opção do frete** não deve ser retornada!

---

## Cálculo do valor do frete
Caso todas as validações do payload recebido sejam válidas, o cálculo do valor do frete muda de transportadora para transportadora.

Disponibilizamos logo abaixo uma constante para calcular esse valor.

Para isso, utilize a fórmula abaixo e calcule o valor do frete:
<center><b>(Peso x constante_frete) / 10<b></center>

---

## Opções de Frete
- Entrega Ninja:
    - Constante para cálculo do frete: 0.3
    - Altura mínima: 10 cm
    - Altura máxima: 200 cm
    - Largura mínima: 6 cm
    - Largura máxima: 140 cm
    - Prazo para entrega: 6 dias

- Entrega KaBuM:
    - Constante para cálculo do frete: 0.2
    - Altura mínima: 5 cm
    - Altura máxima: 140 cm
    - Largura mínima: 13 cm
    - Largura máxima: 125 cm
    - Prazo para entrega: 4 dias

---
## Pontos avaliados

- Arquitetura
- Design Patterns (código e GIT)
- Qualidade de documentação
- Organização
- Funcionamento da API


## Exemplos

### input

```json
{
    "dimensao": {
                    "altura":102,
                    "largura":40
                },
    "peso":400
}
```

### output

```json
[
	{
        "nome":"Entrega Ninja",
    	  "valor_frete": 12.00,
    	  "prazo_dias": 6
	},
	{
    	  "nome":"Entrega KaBuM",
    	  "valor_frete": 8.00,
    	  "prazo_dias": 4
	}
]
```

---

### input

```json
{
    "dimensao": {
                    "altura":152,
                    "largura":50
                },
    "peso":850
}
```

### output

```json
[
	{
        "nome":"Entrega Ninja",
        "valor_frete": 25.50,
    	"prazo_dias": 6
	}
]
```

---

### input

```json
{
    "dimensao": {
                    "altura":230,
                    "largura":162
                },
    "peso":5600
}
```

### output

```json
[]
```
