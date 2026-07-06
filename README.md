# Selection Text OCR (Windhawk)

Mod Windhawk para Windows 11 que adiciona um atalho global para capturar uma região da tela e copiar apenas o texto reconhecido (OCR) para a área de transferência.

## Funcionalidades

- Atalho global configurável (padrão: `Ctrl+Shift+O`)
- Seleção visual de região na tela (clique e arraste)
- OCR usando a API nativa do Windows (`Windows.Media.Ocr`)
- Texto copiado automaticamente para a área de transferência
- Cancelamento com `Esc`

## Requisitos

- [Windhawk](https://windhawk.net/) instalado
- Windows 10 ou 11
- Pacote de idioma OCR instalado no Windows

### Instalar pacote OCR

1. Abra **Configurações** → **Hora e idioma** → **Idioma e região**
2. Selecione seu idioma (ex.: Português Brasil)
3. Clique em **Opções de idioma**
4. Em **Recursos de idioma**, instale **Reconhecimento óptico de caracteres (OCR)**

Para português, o idioma padrão do mod é `pt-BR`. Para inglês, altere para `en-US` nas configurações do mod.

## Instalação

1. Abra o Windhawk
2. Clique em **Criar novo mod** (ou **Create new mod**)
3. Substitua o conteúdo de `mod.wh.cpp` pelo arquivo [`mods/selection-text-ocr.wh.cpp`](mods/selection-text-ocr.wh.cpp)
4. Compile com `Ctrl+B`
5. Ative o mod

## Uso

1. Pressione o atalho configurado (`Ctrl+Shift+O` por padrão)
2. A tela ficará escurecida — arraste o mouse para selecionar a áirea com texto
3. Solte o botão do mouse
4. O texto reconhecido será copiado para a área de transferência

Pressione `Esc` a qualquer momento para cancelar.

## Configurações

| Configuração | Padrão | Descrição |
|---|---|---|
| Hotkey modifier | `ctrl+shift` | Modificadores do atalho (`alt`, `ctrl`, `shift`, `win`) |
| Hotkey key | `O` | Tecla do atalho |
| OCR language | `pt-BR` | Idioma do OCR (tag BCP-47) |
| Show result dialog | `false` | Exibir diálogo com o texto extraído |
| Minimum selection size | `8` | Tamanho mínimo da seleção em pixels |

## Como funciona

O mod roda como um **tool mod** em um processo dedicado do `windhawk.exe`. Ao pressionar o atalho:

1. Uma sobreposição em tela cheia permite selecionar a região
2. A região é capturada como imagem
3. O Windows PowerShell 5.1 executa OCR via `Windows.Media.Ocr`
4. O texto é copiado para a área de transferência

## Limitações

- A qualidade do OCR depende do pacote de idioma instalado e da nitidez do texto na tela
- O OCR usa o Windows PowerShell clássico (`powershell.exe`), não o PowerShell 7
- Selecões muito pequenas são ignoradas

## Apoio e desenvolvimento

Repositório oficial: [github.com/adfastltda/selection-text-ocr](https://github.com/adfastltda/selection-text-ocr)

- **Suporte:** abra uma issue no GitHub para relatar problemas ou pedir ajuda
- **Contribuições:** pull requests são bem-vindos para melhorias e correções
- **Código-fonte:** disponível no repositório acima

## Licença

MIT
