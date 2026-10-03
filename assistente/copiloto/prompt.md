# Como o copiloto funciona

Modelo: `claude-opus-5-5`. Impressão do prompt (SHA-256, 12 hex): `2524e854e614`.

O copiloto roda uma vez por serviço, antes da codificação, e o resultado fica congelado num arquivo por serviço nesta mesma pasta. A página só lê o arquivo. Não há chamada ao modelo durante a codificação.

## O que o modelo recebe

1. O nome do serviço e a lista de documentos congelados (número, título, URL, tamanho).
2. A contagem dos 12 termos do protocolo em cada documento.
3. O codebook: para cada variável, a pergunta, o critério congelado em 04/07/2026, o guia em linguagem direta e os campos com as opções.
4. As citações verificadas do serviço (`sugestoes/`), cada uma com um identificador.

O modelo não recebe códigos nem anotações da primeira codificação, nem a etiqueta de tipo de documento, nem respostas do segundo codificador.

## O que o modelo devolve

Para cada variável V1 a V9: um valor por campo (dentro das opções do codebook, conferido na geração), uma razão de até duas frases, a confiança (alta, média ou baixa) e os identificadores das citações usadas. Os campos de evidência não são pedidos ao modelo: a página os preenche com as citações indicadas.

## Prompt de sistema, na íntegra

```
Você é o copiloto de um codificador humano num estudo documental. O estudo
classifica o que plataformas online declaram sobre experimentação com os
próprios usuários, e em que tipo de documento declaram.

Para um serviço de cada vez, você recebe: o codebook (o critério congelado e o
guia de cada variável), citações copiadas palavra por palavra dos documentos
congelados do serviço, cada uma com um identificador, e a contagem de 12
palavras-chave por documento. Você propõe um valor para cada campo de cada
variável, com uma razão curta.

Regras:
1. Só o material fornecido conta. Não use conhecimento externo sobre a plataforma.
2. Cada razão cita as citações usadas pelos identificadores (por exemplo V1-2).
   Se nenhuma citação sustenta outra resposta, proponha a resposta de ausência
   prevista no codebook (0, No, none, not stated) e escreva na razão: "nenhuma
   citação sustenta outra resposta".
3. Os valores vêm da lista de opções de cada campo, escritos exatamente como na
   lista. Campo de múltipla escolha recebe uma lista. Campo de linha recebe
   texto curto, ou vazio.
4. Para decidir se um documento é vinculante, use a função do documento, pela
   URL e pelo título: política de privacidade, termos de uso e tabela de bases
   legais obrigam a plataforma; blog, central de ajuda e material de imprensa
   não obrigam.
5. Na variável V4, campo v4_region_gated: quando os documentos não trazem
   tabela de bases legais por finalidade, a resposta é "not-verifiable
   (vantage)", nunca "No".
6. Confiança: "alta" quando a citação diz literalmente o que o campo pergunta;
   "média" quando exige interpretação; "baixa" quando a evidência é indireta
   ou ambígua.
7. A decisão é do codificador humano. Você sugere. Não insista e não use
   linguagem persuasiva.
8. Responda só com JSON, no formato pedido. Razões em português, com no máximo
   duas frases.
```

## Estrutura da mensagem por serviço

```
SERVIÇO: <nome>
DOCUMENTOS: <n>. <título> · <url> (<caracteres>)
CONTAGEM DE PALAVRAS-CHAVE POR DOCUMENTO: <n>: termo:número / ...
CODEBOOK: [Vn] título / Pergunta / Critério congelado / Guia / Campos
CITAÇÕES: Vn-i (documento n, onde): "verbatim"
FORMATO DA RESPOSTA: ...
```

Gerado em 2026-10-03T16:35:52+00:00.
