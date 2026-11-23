# VANTZ Tech Wiki

Enciclopédia gratuita para suporte N1/N2, manutenção de computadores e TI. Aplicação estática em React, TypeScript, Vite e React Router.

**Endereço de publicação:** <https://goliveiraxx.github.io/vantz-wiki/>

## Rodar localmente

Use Node.js 22.12 ou superior. Na pasta do projeto:

```sh
npm ci
npm run dev
```

Abra o endereço mostrado pelo Vite. Para verificar os tipos e conferir a versão de produção:

```sh
npm run build
npm run preview
```

## Publicação estática

1. Execute `npm ci` e `npm run build`.
2. Publique o conteúdo de `dist/` no diretório público do serviço de hospedagem estática escolhido.
3. Confira a página inicial e uma rota direta como `/#/sintoma/corte-papel`. O site usa hash nas rotas e caminhos relativos para recursos, inclusive quando publicado em subpastas.

### GitHub Pages

O projeto já está configurado para ser publicado no repositório `vantz-wiki` da conta `goliveiraxx`. O Vite gera os recursos usando o caminho `/vantz-wiki/`, necessário para o endereço do GitHub Pages.

1. Envie esta pasta para o repositório `vantz-wiki`.
2. Execute `npm ci` e `npm run build`.
3. Publique o conteúdo de `dist/` pelo GitHub Pages ou configure uma GitHub Action para executar esse build automaticamente.
4. Acesse <https://goliveiraxx.github.io/vantz-wiki/>.

O site funciona sem banco de dados ou API.

## Catálogo e dados locais

- `src/tools.ts`, `src/phase2-tools.ts` e `src/wiki-data.ts` mantêm as fichas e referências cruzadas entre categorias.
- `src/devices.ts` mantém modelos de impressoras, interfaces documentadas, portais e pacotes de drivers.
- `src/sources.ts` mantém as referências oficiais encontradas na revisão editorial.
- `src/guides.ts`, `src/catalog.ts` e `src/commands.ts` contêm roteiros, checklists, tutoriais e comandos.
- As observações e os estados de checklist, bem como a seleção do Kit do Técnico, ficam no armazenamento local da origem no navegador. Limpar os dados do site apaga essas informações.
- As páginas de checklist e do kit usam **Imprimir / Salvar PDF** para abrir o diálogo de impressão do navegador. O kit também gera um TXT local com a lista e as referências.
- A arquitetura já distingue referências oficiais, documentação e o tipo reservado para um instalador redistribuível. Antes de cadastrar um binário futuramente, confirme autorização, versão, licença e origem. A Fase 2 usa referências externas.

Consulte `RELATORIO-FASE-2.md` para o escopo e testes e `PENDENCIAS-DE-VERIFICACAO.md` para lacunas editoriais.

## Repetir a auditoria de interface

Com as dependências instaladas, gere o build e execute a suíte Playwright:

```sh
npx playwright install chromium
npm run build
npm test
```

A suíte testa o build estático nas larguras desktop e mobile. Para usar Chromium ou Chrome já instalado, defina `VANTZ_CHROMIUM_PATH` com o caminho do executável. Para usar um servidor de teste já aberto, defina `VANTZ_TEST_BASE_URL` com a origem do preview. O relatório JSON fica em `test-results/audit.json` e os PDFs de teste em `test-results/`.

Consulte `AUDITORIA-FINAL-VANTZ-TECH-WIKI.md` e `RESULTADO-DOWNLOADS.csv` para os resultados da revisão. Os instaladores usados durante os testes de download não são distribuídos com o projeto.
