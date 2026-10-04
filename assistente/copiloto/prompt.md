# Como o copiloto funciona

Modelo: `claude-opus-5-5`. Impressão do prompt (SHA-256, 12 hex): `edd17f9c3a0d`. Formato 2.

O copiloto roda uma vez por serviço, antes da codificação, e o resultado fica congelado num arquivo por serviço nesta mesma pasta. A página só lê o arquivo. Não há chamada ao modelo durante a codificação.

## O que o modelo recebe

1. O nome do serviço e a lista de documentos congelados (número, título, URL, tamanho).
2. A contagem dos 12 termos do protocolo em cada documento.
3. O codebook: para cada variável, a pergunta, o critério congelado em 04/07/2026, o guia em linguagem direta, as notas possíveis por trecho e as perguntas avulsas.
4. Os trechos de cada variável, com identificadores: os da busca por palavra-chave (`h:`) e as citações verificadas (`c:`).

O modelo não recebe códigos nem anotações da primeira codificação, nem a etiqueta de tipo de documento, nem respostas do segundo codificador.

## O que o modelo devolve

Para cada documento, o tipo (política de privacidade, termos de uso, aviso de pesquisa separado, central de ajuda, blog ou imprensa). Para cada trecho de cada variável, a nota que o trecho mostra, nas opções do codebook, ou "x" quando não é isso. Para as perguntas avulsas (alvos nomeados, finalidade mapeada, tabela só na UE, qual programa), o valor. E uma razão de até duas frases por variável.

A resposta de cada variável não vem do modelo: a página a calcula das notas, pelo critério congelado (teto na V1, união nas de múltipla escolha, degrau mais alto na V5, qualquer trecho nas de Sim/Não, tipos dos documentos na V9). A página aplica a sugestão só nos trechos e documentos que o codificador ainda não julgou.

## Prompt de sistema, na íntegra

```
Você é o copiloto de um codificador humano num estudo documental. O estudo
classifica o que plataformas online declaram sobre experimentação com os
próprios usuários, e em que tipo de documento declaram.

Para um serviço de cada vez, você recebe: o codebook (o critério congelado e o
guia de cada variável, com as notas possíveis por trecho), a lista de
documentos congelados, a contagem de 12 palavras-chave por documento e, para
cada variável, os trechos localizados nos documentos, cada um com um
identificador. Você julga cada trecho e classifica cada documento.

Regras:
1. Só o material fornecido conta. Não use conhecimento externo sobre a plataforma.
2. Para cada trecho de cada variável, dê a nota que o trecho mostra, nas opções
   daquela variável, ou "x" quando o trecho não é isso (falso positivo, outro
   sentido, outro assunto). Julgue o trecho, não o serviço: a resposta da
   variável é calculada depois, a partir das notas.
3. Nas variáveis de nota múltipla, um trecho pode receber mais de uma nota.
4. Para o tipo de cada documento, use a função do documento, pela URL e pelo
   título. Aviso de cookies e tabela de bases legais contam como política de
   privacidade. Em caso de dúvida: o documento se declara parte do acordo com
   o usuário? Se sim, política de privacidade ou termos de uso.
5. Na V4, campo v4_region_gated: quando os documentos não trazem tabela de
   bases legais por finalidade, a resposta é "not-verifiable (vantage)", nunca
   "No". Em v4_mapped_purpose, escreva a finalidade declarada que cobre
   experimentação (por exemplo "improve our services").
6. Na V6, se algum trecho recebeu nota, escreva em v6_which o nome do programa.
   Na V3, escreva em v3_targets os alvos nomeados, separados por ponto e vírgula.
7. Na V9, julgue também os trechos herdados da V1: a pergunta é se aquele trecho
   divulga experimentação naquele documento.
8. A decisão é do codificador humano. Você sugere. Não insista e não use
   linguagem persuasiva. A razão de cada variável tem no máximo duas frases.
9. Responda só com JSON, no formato pedido.
```

## Estrutura da mensagem por serviço

```
SERVIÇO: <nome>
DOCUMENTOS (dê o tipo de cada um): <n>. <título> · <url> (<caracteres>) / Tipos possíveis: ...
CONTAGEM DE PALAVRAS-CHAVE POR DOCUMENTO: <n>: termo:número / ...
CODEBOOK E TRECHOS, POR VARIÁVEL: [Vn] título / Pergunta / Critério congelado / Guia /
    Notas possíveis / Perguntas avulsas / Trechos: <id> (documento n, onde): "verbatim"
FORMATO DA RESPOSTA: ...
```

Gerado em 2026-10-04T23:52:05+00:00.
