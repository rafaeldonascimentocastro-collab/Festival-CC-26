# Festival do Clube de Criação 2026 · Transmissão ao vivo

Página única (HTML + CSS + JS, sem build) com os dois auditórios, seletor de dia (17/10 e 18/10), player do YouTube embutido, programação oficial com status (Em andamento / A seguir / Encerrada) e filtros.

| Arquivo | Para quê |
|---|---|
| `index.html` | A página completa. É o arquivo que vai para o site. |
| `teste-mobile.html` | Diagnóstico para celular: ambiente, https e teste dos 4 vídeos. |
| `GUIA-DE-PUBLICACAO.md` | Passo a passo de publicação e onde corrigir cada coisa. |
| `regras/` | Regras `.htaccess`, nginx e opção B (página WordPress com iframe). |

## Links oficiais (não alterar)

| Dia | Auditório Papaki | Auditório Clube de Criação |
|---|---|---|
| 17/10 | https://www.youtube.com/live/6eUy33JLQGA | https://www.youtube.com/live/40fZ5IqIrfo |
| 18/10 | https://www.youtube.com/live/uNp9h-T3ruU | https://www.youtube.com/live/lF7RIQ-_fkw |

Os links ficam no bloco `var LINKS` do `index.html`.

## Testes

Parâmetros na URL: `?simular=2026-10-17T11:00`, `?dia=17|18`, `?sala=plateia-1|2`, `?diagnostico=1` (confere se as 4 lives permitem incorporação).

## Atenção

O vídeo embutido só funciona em endereço **https**. Aberto como arquivo no celular ou numa prévia, o YouTube mostra o erro 153. Publique (GitHub Pages ou site oficial) e abra pelo endereço.

Programação conferida com https://clubedecriacao.com.br/festival/ em 10/10/2026. Reconferir nos dias do evento.
