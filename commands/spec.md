---
description: Generates a complete software specification document (SPEC) by analyzing the current Delphi project source code
---

Gere automaticamente um documento de especificacao de software (SPEC) a partir do
codigo-fonte do projeto Delphi no diretorio de trabalho atual.

**Escopo:** A SPEC cobre o projeto inteiro ou um modulo de negocio completo.
Nunca para uma unica unit ou classe.

**Idioma:** Detecte o idioma do usuario e responda sempre nesse idioma.
Padrao: portugues brasileiro.

Siga este protocolo sem interromper o usuario com perguntas:

1. **SCAN** — Use Glob para localizar todos os arquivos `.pas`, `.dfm`, `.dpr`, `.dproj`
   no diretorio de trabalho atual. Identifique o projeto principal, forms, services,
   repositories, entities e datamodules.

2. **READ** — Leia os arquivos relevantes priorizando units de dominio, services,
   repositories, forms principais e datamodules com regras de negocio.

3. **EXTRACT** — Mapeie diretamente do codigo:
   - Atores (forms e permissoes)
   - Requisitos Funcionais (metodos publicos, acoes, eventos)
   - Requisitos Nao Funcionais (tecnologia, banco, plataforma)
   - Regras de Negocio (validacoes, guards, if/raise)
   - Casos de Uso (fluxos de tela, acoes principais)
   - Modelo de Dados (entidades, records, queries)
   - Integracoes (HTTP, COM, DLL, WebService)
   - Restricoes Tecnicas (versao Delphi, banco, SO alvo)

4. **GENERATE** — Preencha todas as secoes do template carregando a skill `delphi-spec`
   e o arquivo `references/spec-template.md`. Marque com `[INFERIDO]` itens cuja intencao
   nao esteja explicita no codigo. Nunca deixe secoes em branco.

5. **SAVE** — Grave o documento como `SPEC.md` na raiz do projeto.

6. **REPORT** — Informe ao usuario: caminho do arquivo gerado, secoes reais vs. inferidas,
   arquivos nao analisados (se houver) e sugestoes de revisao manual.
