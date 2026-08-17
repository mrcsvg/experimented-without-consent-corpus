# Corpus congelado — 2º passe de codificação

Congelado em 2026-08-03, de vantagem IT (UE).
142 documentos, 26 serviços.

## Por que ler daqui e não do site

Os documentos das plataformas mudam sem aviso. Se os dois codificadores lerem
versões diferentes da mesma página, a discordância entre eles deixa de ser
discordância de codificação e vira deriva do documento, e depois não há como
separar as duas. Ler deste corpus garante que os dois passes leram o mesmo
texto.

Há um ganho prático junto: o protocolo exige registrar, por documento, a
contagem de cada termo da busca por palavra-chave. Em texto plano o Ctrl-F /
Cmd-F conta certo. Na página ao vivo ele erra, porque parte do conteúdo só
existe depois do JavaScript, ou aparece conforme você rola.

## Como usar

Abra **`index.html`** (duplo clique). Ele lista os documentos por serviço, com a
URL de origem ao lado, e clica direto no arquivo. `index.json` traz o mesmo em
formato de dados, se preferir.

Cada arquivo começa com um cabeçalho dizendo de onde veio:

```
==============================================================================
FONTE      https://help.x.com/en/rules-and-policies/x-cookies
CAPTURADO  2026-07-31T16:12:03+00:00  ·  vantagem IT
MÉTODO     captura automatizada (HTTP)
SHA-256    e294269a13b0…
           (do texto abaixo da linha, sem este cabeçalho)
------------------------------------------------------------------------------
```

## Como o texto foi extraído (e o que isso implica)

O que está aqui é o **texto** do documento, não a página. A extração remove
scripts, estilos e as marcações de HTML, desfaz as entidades (`&amp;` volta a
ser `&`) e normaliza o espaço em branco. O que sobra é a prosa na ordem em que
aparecia.

Consequências que importam para a codificação:

- **Não há formatação.** Tabelas viram linhas soltas; a tabela de bases legais
  por finalidade, por exemplo, aparece como sequência de células. O conteúdo
  está lá, a grade não.
- **Não há imagens nem elementos interativos.** Se um documento comunicasse algo
  só por imagem, isso não estaria aqui — não encontramos nenhum caso, mas se
  desconfiar, registre.
- **Menus, rodapés e banners de cookie entram no texto**, porque fazem parte da
  página. Ignore-os; não são o documento.
- Documentos marcados **manual** foram salvos pelo navegador, com a página já
  montada, porque o site monta o conteúdo por JavaScript ou recusa acesso
  automatizado. São equivalentes em conteúdo; a diferença de procedência fica
  registrada porque ela existe, não porque compromete algo.

Se algum documento parecer incompleto, truncado, ou não corresponder à URL do
cabeçalho, **registre no campo "Problemas de acesso" do instrumento e não
codifique o campo afetado** — como o protocolo já manda para link morto. É
preferível uma célula vazia e explicada a uma célula preenchida sobre texto
duvidoso.

## Conferir que um arquivo não foi alterado

O SHA-256 do cabeçalho cobre o texto abaixo dele — o cabeçalho tem 7 linhas
mais uma em branco, então o corpo começa na linha 9:

```bash
tail -n +9 arquivo.txt | shasum -a 256
```

Deve bater com o SHA-256 do cabeçalho. Não batendo, avise: significa que o
arquivo foi editado depois do congelamento.

## O que NÃO está aqui

Nenhuma codificação, de nenhum passe. O 2º passe é cego por desenho: você
codifica a partir do documento e do codebook, sem ver o que foi codificado
antes.
