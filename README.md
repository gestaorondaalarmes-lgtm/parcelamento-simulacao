# Gerador de Parcelas

Ferramenta única em HTML (sem instalação, sem dependências de backend) para gerar a relação de parcelas de um parcelamento, pronta para copiar e colar em planilhas ou no Nibo.

**Acesse em:** https://gestaorondaalarmes-lgtm.github.io/parcelamento-simulacao/

## O que ela faz

A partir do valor total, número de parcelas, competência e vencimento inicial, gera uma tabela com:

| Referência | Valor da Parcela | Competência | Vencimento | Descrição |
|---|---|---|---|---|

- **Valor da parcela**: divisão exata em centavos (sem erro de arredondamento) — se sobrar centavo, ele é distribuído nas primeiras parcelas.
- **Competência**: fixa em todas as linhas (é uma parcela de uma compra, não uma recorrência mensal).
- **Vencimento**: avança um mês por parcela a partir da data inicial, ajustando automaticamente o dia em meses mais curtos (ex.: dia 31 → último dia de fevereiro) e virando o ano corretamente.
- **Referência**: `PARC. X/X`, com prefixo opcional de Nota Fiscal (ex.: `NFe 999 PARC. 1/12`).
- **Descrição**: `Fatura Mensal Ref. MM/AAAA`, com o número da parcela ao final quando habilitado (ex.: `Fatura Mensal Ref. 01/2026 - 01/12`).

## Campos do formulário

- **Valor total** — com máscara de moeda automática.
- **Nº de parcelas**
- **Competência** — data completa; define o mês fixo usado na tabela e no período.
- **Vencimento inicial**
- **Nota Fiscal** (Sim/Não) — se Sim, abre Tipo (NFe / NFS / Outros) e o número da nota, que passam a compor a Referência.
- **Nº da parcela na descrição** (Sim/Não) — controla se a Descrição traz o `X/X` no final.
- **Período** — calculado automaticamente a partir da Competência (1º ao último dia do mês, ex.: `Periodo: 01/12/2026 a 31/12/2026`). Clique no texto para copiar.
- **Botão Gerar** — dispara a geração da tabela.

## Registro parcial

Abaixo da tabela principal, um seletor **"Considerar a partir da parcela"** monta uma segunda tabela somente com a parcela escolhida em diante (ex.: da 7ª à última), com o **total somado** dessas parcelas e botão para copiar esse valor.

## Copiar e colar

- Clique em qualquer célula (ou no ícone de cópia em Referência/Descrição) para copiar só aquele valor.
- Botão **Copiar tabela** copia todas as linhas em formato TSV (compatível com Excel/Nibo), com ou sem cabeçalho.

## Publicação

Arquivo hospedado via GitHub Pages a partir da raiz do repositório (`main` / `root`). Como o Pages serve automaticamente o arquivo `index.html`, o deploy exige que o arquivo principal tenha exatamente esse nome, em minúsculas.
