# Festival do Clube de Criação 2026 · Página de transmissão
## Guia de publicação e de correções · https://clubedecriacao.com.br/festival/transmissao2026/

**Versão:** 10/10/2026 · **Site:** WordPress (tema `clube-criacao-1.0`, Evolut), página `/festival/` criada no WordPress, site atrás do Cloudflare.

---

## 1. O que vai no pacote

| Arquivo | Para que serve |
|---|---|
| `transmissao2026/index.html` | **A página pronta.** Arquivo único (HTML + CSS + JavaScript + imagens embutidas, ≈ 285 KB). Não depende de outros arquivos. |
| `regras/htaccess-raiz.txt` | Regra para a URL `/festival/transmissao2026/` abrir a página (Apache/LiteSpeed). |
| `regras/htaccess-pasta.txt` | `.htaccess` da pasta da página (acentos e cache curto). |
| `regras/nginx.txt` | Equivalente, se o servidor for Nginx. |
| `regras/wordpress-iframe-opcao-b.html` | Alternativa sem mexer no servidor (página WordPress com quadro incorporado). |
| `GUIA-DE-PUBLICACAO.md` | Este guia. |

**Endereço recomendado:** `https://clubedecriacao.com.br/festival/transmissao2026/` (minúsculas, sem acento). O endereço com acento e maiúscula (`/festival/Transmissão2026`) vira `transmiss%C3%A3o2026` nos links e costuma quebrar. A regra do item 4 redireciona quem digitar do jeito acentuado.

> **Importante:** não abra o `index.html` com duplo clique nem pelo celular (arquivo baixado, WhatsApp, Drive, Arquivos) para testar o vídeo. Para ver no celular, abra o **endereço publicado**. O YouTube recusa o player em arquivos locais (**erro 153**). A página detecta isso e mostra um aviso com botão de acesso direto. Teste pelo endereço publicado.

## 2. Como a página funciona (resumo)

- Duas abas de dia (**Sábado 17/10** e **Domingo 18/10**). No evento, abre no dia certo pelo horário de São Paulo.
- Dois cartões no cabeçalho para escolher o auditório: **Auditório Papaki** (dourado) e **Auditório Clube de Criação** (bordô). A cor da página inteira muda conforme o auditório selecionado.
- O player do YouTube mostra a transmissão do **dia + auditório** escolhidos. O botão **▶ Assistir à transmissão** abre o mesmo vídeo no YouTube, em nova aba.
- Programação por auditório (com filtro “Todos / Papaki / Clube de Criação”), com o status de cada sessão: **Em andamento**, **A seguir** ou **Encerrada**, calculado pelos horários oficiais.
- Não há troca automática de auditório: quem assiste escolhe.

## 3. O que você precisa ter em mãos

1. Acesso ao servidor por **FTP/SFTP** ou pelo **Gerenciador de Arquivos** da hospedagem. Se não tiver, peça à **Evolut** ou à hospedagem.
2. Acesso de **administrador** ao WordPress (só para a Opção B e para colocar o botão na página do Festival).
3. Acesso ao **Cloudflare** (só se precisar limpar o cache).
4. Um editor de texto simples: **VS Code**, **Notepad++** ou **Bloco de Notas**. Não use o Word. Salve sempre em **UTF-8**.

## 4. OPÇÃO A (recomendada): arquivo no servidor + regra de endereço

Mantém a URL limpa dentro de `/festival/`, abre a página inteira (sem o cabeçalho do tema) e é a mais estável para o dia do evento.

> ⚠️ **Não crie uma pasta física chamada `festival`** na raiz do site. `/festival/` é uma página do WordPress; uma pasta com esse nome faria a página oficial parar de abrir. Por isso o arquivo fica em `wp-content/uploads/` e a regra faz o endereço apontar para ele.

1. **Backup:** baixe uma cópia do `.htaccess` da raiz (`public_html/.htaccess`).
2. Conecte por FTP/SFTP ou abra o Gerenciador de Arquivos.
3. Em `public_html/wp-content/uploads/`, crie a pasta **`festival-transmissao-2026`**.
4. Envie `transmissao2026/index.html` para essa pasta. Caminho final: `wp-content/uploads/festival-transmissao-2026/index.html`.
5. (Recomendado) Na mesma pasta, crie um arquivo **`.htaccess`** com o conteúdo de `regras/htaccess-pasta.txt`.
6. Abra o `.htaccess` da raiz e cole o bloco de `regras/htaccess-raiz.txt` **acima** da linha `# BEGIN WordPress`. Salve.
7. Abra `https://clubedecriacao.com.br/festival/transmissao2026/`.
8. Se o servidor for **Nginx** (o `.htaccess` não tem efeito), use `regras/nginx.txt` com a hospedagem.
9. Faça os testes do item 8.

## 5. OPÇÃO B: página WordPress (sem mexer no `.htaccess`)

A página aparece **dentro** do tema (menu e rodapé do Clube) e a transmissão é incorporada em um quadro.

1. Faça os passos 3 e 4 da Opção A (envio do `index.html`).
2. No painel: **Páginas → Adicionar nova**. Título: `Transmissão 2026`.
3. Em **Endereço (slug)**: `transmissao2026`. Em **Atributos da página → Superior**: **Festival**. A URL ficará `/festival/transmissao2026/`.
4. Adicione um bloco **HTML personalizado** e cole o conteúdo de `regras/wordpress-iframe-opcao-b.html`.
5. Escolha o modelo de página sem barra lateral (se existir) e clique em **Publicar**.
6. Teste no celular. O quadro ajusta a altura sozinho. Se o tema bloquear scripts no editor, peça à Evolut para liberar o bloco HTML para administradores.

Na Opção B a barra fixa de seleção do topo não aparece (o quadro é maior que a tela). Para a transmissão, prefira a Opção A.

## 6. Divulgar a página

- Na página `/festival/` (Páginas → Festival), adicione um botão **“Assista ao vivo”** apontando para `/festival/transmissao2026/`.
- Em **Aparência → Menus**, acrescente o item **Transmissão ao vivo** ao menu Festival.
- Use o mesmo endereço nas redes sociais, na newsletter e na Sympla.

---

## 7. ONDE CORRIGIR: mapa do `index.html`

Abra o arquivo em um editor de texto e use **Ctrl+F** para procurar o texto da coluna “Procure por”. As linhas são aproximadas (mudam se você acrescentar ou remover linhas antes).

| Quero mudar… | Procure por | Linha aprox. |
|---|---|---|
| **Links das transmissões (os 4 links)** | `var LINKS` | 274–279 |
| Auditório que abre selecionado | `destaquePadrao` | 283 |
| Canal do YouTube (usado só se um link ficar vazio) | `canalId` | 284 |
| Nome dos auditórios na tela | `var SALAS` | 289–292 |
| Dias do festival (rótulo e data) e **shows** | `var DIAS` | 295–301 |
| **Programação** (início, fim, título, participantes) | `var PROG` | 308–360 |
| Cores e temas (dourado / bordô) | `--papaki` e `html[data-sala=` | 24 e 33–34 |
| Título da aba do navegador | `<title>` | 7 |
| Texto “A programação pode sofrer alterações” (caixa) | `class="aviso-prog"` | 250 |
| Rodapé (endereço, portões, ingressos, aviso) | `<footer>` | 259–264 |
| Link de ingressos | `sympla.com.br` (aparece 2 vezes: linhas ~241 e ~261) | 241, 261 |
| Link do mapa | `maps.app` | 260 |
| Sala Oliver / portfólios | `Sala Oliver` | 551 |
| Texto “Escolha o auditório” | `Escolha o auditório` | 215 |
| **Links de reserva (aparecem quando o aparelho não executa JavaScript)** | `<noscript>` | 226 |

### 7.1 Trocar um link de transmissão

Procure por **`var LINKS`**. Cada linha é um dia + auditório:

```js
var LINKS = {
  "17": { "plateia-1": "https://www.youtube.com/live/6eUy33JLQGA",    // 17/10 · Auditório Papaki
          "plateia-2": "https://www.youtube.com/live/40fZ5IqIrfo" },  // 17/10 · Auditório Clube de Criação
  "18": { "plateia-1": "https://www.youtube.com/live/uNp9h-T3ruU",    // 18/10 · Auditório Papaki
          "plateia-2": "https://www.youtube.com/live/lF7RIQ-_fkw" }   // 18/10 · Auditório Clube de Criação
};
```

Troque **somente o endereço entre aspas**. **Troque também no bloco `<noscript>`** (procure por `<noscript>`): é a cópia de reserva dos 4 links que aparece quando o aparelho não executa JavaScript. Aceita `youtube.com/live/…`, `youtube.com/watch?v=…`, `youtu.be/…` ou só o ID de 11 caracteres. Não apague as aspas, as vírgulas nem as chaves. Os links já cadastrados:

| Dia | Auditório | Link |
|---|---|---|
| 17/10 | Auditório Papaki (`plateia-1`) | https://www.youtube.com/live/6eUy33JLQGA |
| 17/10 | Auditório Clube de Criação (`plateia-2`) | https://www.youtube.com/live/40fZ5IqIrfo |
| 18/10 | Auditório Papaki (`plateia-1`) | https://www.youtube.com/live/uNp9h-T3ruU |
| 18/10 | Auditório Clube de Criação (`plateia-2`) | https://www.youtube.com/live/lF7RIQ-_fkw |

### 7.2 Corrigir horário, título ou participantes de uma sessão

Procure por **`var PROG`**. Cada sessão é uma linha: `[início, fim, título, tipo, participantes]`.

```js
["10:30","11:20","Indie BR: o futuro é mesmo independente?","","Mediação: Felipe Silva. Com Ana Paula Passarelli, ..."],
```

- Mude o texto entre aspas. **Horários sempre no formato `"HH:MM"`** (ex.: `"9:30"` ou `"09:30"`).
- `tipo`: `""` normal · `"i"` almoço/intervalo · `"m"` mentoria · `"p"` premiação · `"c"` em construção.
- O bloco de cada dia/auditório começa em: sábado Papaki (linha ~310), sábado Clube de Criação (~324), domingo Papaki (~337), domingo Clube de Criação (~349).
- Para **incluir** uma sessão: copie uma linha inteira, cole na ordem cronológica e ajuste. Todas as linhas terminam com vírgula, **menos a última** de cada bloco.
- Para **remover**: apague a linha inteira.
- Se uma sessão não tiver fim definido, deixe `""` no segundo campo (a página assume 60 min; premiação 90 min).

### 7.3 Mudar nome, cores, dias ou shows

- **Nome do auditório:** em `var SALAS`, altere `nome:"…"` (e `curto:"…"`, que aparece nos filtros no celular). **Não altere** `id:"plateia-1"` / `id:"plateia-2"`.
- **Cores:** em `--papaki` e `--clube` (linhas ~24–25) e nos dois temas `html[data-sala="plateia-1"]` e `html[data-sala="plateia-2"]` (linhas 33–34). `--bg` é o fundo, `--bg2` o tom mais escuro (faixa dos dias e rodapé), `--on` a cor do texto.
- **Shows:** em `var DIAS`, no campo `shows`.
- **Data do evento:** em `var DIAS`, campo `data:"AAAA-MM-DD"` (também ajuste a chave `"17"`/`"18"` apenas se mudar de dia, e a mesma chave em `LINKS` e `PROG`).

### 7.4 Depois de qualquer alteração

1. Salve o arquivo (UTF-8).
2. Teste no seu computador com um servidor local, ou envie para o servidor.
3. **Envie o arquivo de novo**, sobrescrevendo o anterior (`wp-content/uploads/festival-transmissao-2026/index.html`).
4. Atualize no navegador com **Ctrl+F5** e, se houver Cloudflare, limpe o cache da URL (item 9).

---

## 8. Testar antes e depois de publicar

### Verificador de links (novo)
Abra a página com **`?diagnostico=1`** no final do endereço, por exemplo:
`https://clubedecriacao.com.br/festival/transmissao2026/?diagnostico=1`

Aparece uma tabela com os 4 links, o ID extraído de cada um e a situação:

- **OK · vídeo encontrado e incorporável**: tudo certo.
- **INCORPORAÇÃO DESATIVADA**: no YouTube Studio, ative **Personalizar → Permitir incorporação**.
- **NÃO ENCONTRADO ou privado**: confira se a live existe e está pública ou não listada.
- **LINK INVÁLIDO ou vazio**: o texto em `var LINKS` está errado (volte ao item 7.1).
- **Formato válido (verificação online indisponível)**: o link está bem escrito, mas o navegador não conseguiu consultar o YouTube.

### Simular um horário
Acrescente `?simular=2026-10-17T11:00` ao endereço: a página se comporta como se fosse sábado, 11h (mostra sessões em andamento, a seguir e encerradas). Outros exemplos: `?simular=2026-10-18T14:30`, `?simular=2026-10-19T10:00` (festival encerrado).

### Atalhos de endereço
- `?dia=17` ou `?dia=18`: abre o dia desejado.
- `#plateia-1` (Papaki) ou `#plateia-2` (Clube de Criação): abre o auditório desejado. Também funciona `?sala=plateia-2`.

### Checklist
- [ ] `/festival/transmissao2026/` abre (computador e celular).
- [ ] `/festival/` continua abrindo normalmente.
- [ ] Botões **Sábado 17/10** e **Domingo 18/10** trocam os dados.
- [ ] Cada combinação dia + auditório abre o link correto (tabela do item 7.1). Use o verificador.
- [ ] **▶ Assistir à transmissão** abre o YouTube em nova aba.
- [ ] O player carrega.
- [ ] A cor da página muda ao trocar de auditório (dourado ↔ bordô), inclusive no rodapé.
- [ ] Filtros **Todos / Papaki / Clube de Criação** funcionam.
- [ ] Sem rolagem lateral no celular.

## 9. Cloudflare e cache

- O HTML normalmente **não** é guardado pelo Cloudflare. Se existir regra “Cache Everything”, exclua `/festival/transmissao2026*` (**Rules → Cache Rules → Bypass cache**).
- Depois de cada atualização do arquivo: **Caching → Configuration → Purge Cache → Custom Purge** e informe a URL da página.
- Se o **Rocket Loader** estiver ligado e algo falhar, desative-o para este caminho (o script já vem com `data-cfasync="false"`, que costuma bastar).

## 10. Solução de problemas

| Sintoma | Causa provável | O que fazer |
|---|---|---|
| Erro 404 em `/festival/transmissao2026/` | Regra não aplicada | Confira se o bloco está **acima** de `# BEGIN WordPress`; confirme o caminho do arquivo; se for Nginx, use `regras/nginx.txt`. |
| A página `/festival/` parou de abrir | Foi criada uma pasta `festival` na raiz | Apague a pasta `festival` criada por engano. |
| **Erro 153** (“erro de configuração do player”) | O YouTube não recebeu a origem da página: arquivo aberto com duplo clique (`file://`), prévia isolada ou servidor com `Referrer-Policy: no-referrer` | Teste por `https://` publicado ou `http://localhost:8000` (`python3 -m http.server`). No servidor, ajuste `Referrer-Policy` para `strict-origin-when-cross-origin` (a página já declara isso). O botão **▶ Assistir no YouTube** continua funcionando. |
| **Página em branco ou só com as imagens do topo ao abrir o arquivo no celular** | O visualizador do aparelho (prévia de arquivos do iOS, leitor de anexo, alguns aplicativos) não executa JavaScript, e a página é montada por script | Abra o arquivo no Chrome ou no Safari, ou, melhor, abra a página **publicada** (https). Mesmo sem JavaScript aparecem os 4 botões de reserva para assistir no YouTube (bloco `<noscript>`). |
| Erro 101 ou 150 | A live está com a incorporação desligada | YouTube Studio → **Permitir incorporação**. |
| Player preto / “vídeo indisponível” | Live ainda não criada, privada ou link errado | Use `?diagnostico=1` e confira o item 7.1. |
| Link de um auditório abre o vídeo do outro | Links trocados em `var LINKS` | Confira a tabela do item 7.1 (`plateia-1` = Papaki, `plateia-2` = Clube de Criação). |
| Acentos quebrados (Ã§) | Charset do servidor ou arquivo salvo fora de UTF-8 | Use o `.htaccess` da pasta e salve em UTF-8. |
| Página em branco após editar | Faltou aspas, vírgula ou colchete na edição | Volte ao arquivo original do pacote e refaça a edição, mudando só o texto entre aspas. |
| Mudei o arquivo e nada mudou | Cache do navegador/Cloudflare | **Ctrl+F5** e limpe o cache (item 9). |
| Fonte diferente | Google Fonts bloqueado na rede | A página usa fonte reserva e continua legível. |

## 11. Pendências com a organização do Festival

1. **Confirmar que as 4 lives estão agendadas** no YouTube e com incorporação permitida (use o verificador).
2. Informar o **tipo de servidor** (Apache/LiteSpeed ou Nginx) e quem tem acesso ao FTP/`.htaccess` (Evolut/hospedagem).
3. Definir quem **atualiza o arquivo** durante o evento se a programação mudar. A página reflete o site oficial conferido em 10/10/2026 (página do Clube atualizada em 09/10/2026).
4. Aprovar os nomes “Auditório Papaki” e “Auditório Clube de Criação” e as cores (dourado e bordô).
5. Clube Lab e Sala Criatividade **não estão** nesta página (só os dois auditórios com transmissão).
6. Confirmar o texto do **aviso legal** e o uso das peças do cabeçalho.
7. O próprio site oficial ainda chama a programação de “(quase, quase, quase) completa”: confira `clubedecriacao.com.br/festival/` na véspera (16/10) e no dia, e corrija `var PROG` se algum horário ou título mudar (item 7.2).
8. Quem abrir a página com o JavaScript desligado vê apenas um aviso com o link do canal do Clube no YouTube.
