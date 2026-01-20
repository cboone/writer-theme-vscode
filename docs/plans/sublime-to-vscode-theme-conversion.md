# Plano: Converter Writer Theme para VSCode

## Resumo

Converter o tema de cores «Writer» do Sublime Text para uma extensão de tema VSCode. O tema tem duas variantes (claro e escuro) otimizadas para escrita em Markdown.

## Ficheiros a Criar

```text
writer-theme-vscode/
├── package.json                           # Manifesto da extensão (CRIAR)
├── themes/
│   ├── writer-light-color-theme.json      # Tema claro (CRIAR)
│   └── writer-dark-color-theme.json       # Tema escuro (CRIAR)
└── README.md                              # Atualizar instruções (MODIFICAR)
```

## Passos de Implementação

### 1. Criar `package.json`

Manifesto da extensão com:

- `name`: `writer-theme`
- `displayName`: `Writer Color Theme`
- `engines.vscode`: `^1.60.0`
- `categories`: `["Themes"]`
- `contributes.themes`: referências aos dois ficheiros de tema

### 2. Criar `themes/writer-light-color-theme.json`

Estrutura:

```json
{
  "$schema": "vscode://schemas/color-theme",
  "name": "Writer",
  "type": "light",
  "colors": {
    /* cores do workbench */
  },
  "tokenColors": [
    /* regras de sintaxe */
  ]
}
```

**Mapeamento de cores do editor (globals → colors):**

| Sublime               | VSCode                               | Valor     |
| --------------------- | ------------------------------------ | --------- |
| `background`          | `editor.background`                  | `#F7F7F7` |
| `foreground`          | `editor.foreground`                  | `#1a1a1a` |
| `caret`               | `editorCursor.foreground`            | `#58bae7` |
| `selection`           | `editor.selectionBackground`         | `#cee7f3` |
| `inactive_selection`  | `editor.inactiveSelectionBackground` | `#dcdcdc` |
| `line_highlight`      | `editor.lineHighlightBackground`     | `#f0f0f0` |
| `find_highlight`      | `editor.findMatchBackground`         | `#FFBC5D` |
| `brackets_foreground` | `editorBracketMatch.border`          | `#58bae7` |

**Cores adicionais do workbench** (sidebar, tabs, titlebar, etc.) derivadas da paleta base.

**Mapeamento de sintaxe (rules → tokenColors):**

| Scope Sublime                             | Scope VSCode                                  | Estilo                                       |
| ----------------------------------------- | --------------------------------------------- | -------------------------------------------- |
| `markup.heading`                          | `markup.heading`                              | `bold`                                       |
| `markup.italic`                           | `markup.italic`                               | `italic`                                     |
| `markup.bold`                             | `markup.bold`                                 | `bold`                                       |
| `markup.bold & markup.italic`             | `markup.bold markup.italic`                   | `bold italic`                                |
| `markup.raw, meta.code-fence`             | `markup.inline.raw, markup.fenced_code.block` | background: `#edeeed`                        |
| `comment, punctuation.definition.link...` | mesmos scopes                                 | foreground: `#c6c5c2`                        |
| `markup.underline.link`                   | `markup.underline.link`                       | `underline`                                  |
| `invalid`                                 | `invalid`                                     | foreground: `#ef786c`, background: `#fce4e2` |
| `markup.inserted`                         | `markup.inserted`                             | foreground: `#6abf40`                        |
| `markup.deleted`                          | `markup.deleted`                              | foreground: `#d32d2a`                        |
| `markup.changed`                          | `markup.changed`                              | foreground: `#ec9112`                        |

### 3. Criar `themes/writer-dark-color-theme.json`

Mesma estrutura, com valores escuros:

- Background: `#1b1b1b`
- Foreground: `#cbcccc`
- Accent: `#55bbe7`
- Highlight: `#fffd54`
- Code block background: `#262626`
- Comment foreground: `#706f70`
- Invalid background: `#462726`

### 4. Atualizar `README.md`

Converter instruções de Sublime para VSCode:

- Instalação via Extensions marketplace
- Atalho para selecionar tema: `Cmd+K Cmd+T`
- Configurações recomendadas para `settings.json`

## Conversões Especiais

**Variáveis:** Sublime usa `var(name)` - substituir por valores diretos.

**Cores com alpha:** `color(var(red) alpha(0.2))` → calcular cor resultante:

- Tema claro: `#ef786c` a 20% sobre `#F7F7F7` = `#fce4e2`
- Tema escuro: `#ef786c` a 20% sobre `#1b1b1b` = `#462726`

**Cores HSL:** Converter para hex:

- `hsl(100, 50%, 50%)` = `#6abf40` (inserted)
- `hsl(2, 65%, 50%)` = `#d32d2a` (deleted)
- `hsl(30, 85%, 50%)` = `#ec9112` (changed)

## Ficheiros Fonte

- `Writer.sublime-color-scheme` - tema claro original
- `Writer Dark.sublime-color-scheme` - tema escuro original
- `specimen.md` - ficheiro de teste para Markdown

## Verificação

1. Executar `F5` no VSCode para abrir Extension Development Host
2. Selecionar tema «Writer» ou «Writer Dark»
3. Abrir `specimen.md` e verificar:
   - Cabeçalhos em negrito
   - Texto _itálico_ e **negrito** corretamente formatados
   - Blocos de código com fundo diferente
   - Links com pontuação esmaecida e URL sublinhado
   - Cores de seleção e destaque
4. Verificar cores do workbench (sidebar, tabs, statusbar)
5. Testar bracket matching com ficheiro de código
