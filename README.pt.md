<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/virtual_joystick_cf_logo_dark.png">
    <img alt="Virtual Joystick Logo" src="assets/virtual_joystick_cf_logo_light.png">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/cf_studios_logo_dark.png">
    <img alt="Cf Studio Logo" src="assets/cf_studios_logo_light.png" height=24>
  </picture>
</h1>

[![Godot Engine][godot-badge]][godot-link] [![Version][changelog-badge]][changelog-link] [![MIT License][license-badge]][license-link]

Um Joystick Virtual profissional, de alta performance e pronta para uso. Projetado especificamente para jogos mobile no Godot 4.5 ou superior.

## 🌎 Linguagem

- [English](README.md)
- **Português**

## 📋 Sumário

- [🌎 Linguagem](#-linguagem)
- [📋 Sumário](#-sumário)
- [✨ Funcionalidades](#-funcionalidades)
- [🚀 Instalação](#-instalação)
- [🛠️ Modo de Usar](#️-modo-de-usar)
  - [Opção 1: Instância da Cena (Recomendado)](#opção-1-instância-da-cena-recomendado)
  - [Opção 2: Cena do Sistema de Arquivos](#opção-2-cena-do-sistema-de-arquivos)
- [⚙️ Configurações](#️-configurações)
- [💻 Integração de Código](#-integração-de-código)
  - [Opção 1: Input Action](#opção-1-input-action)
  - [Opção 2: Sinais](#opção-2-sinais)
- [📂 Estrutura do Projeto](#-estrutura-do-projeto)
- [☕ Apoie o Projeto](#-apoie-o-projeto)
- [⚖️ Licença](#️-licença)
- [📘 Sobre](#-sobre)

## ✨ Funcionalidades

- **Definição de Modos:** Suporte para modo *Static*, *Dynamic* e *Following*;
- **Ajuste de Direções:** Suporte para modos de movimento em 2, 4 e 8 direções ou 360° (analógico completo);
- **Calibração Precisa:** Customização das *Zona Morta*, *Limite de Toque* e *Área Dinâmica* para garantir uma sensação de controle profissional;
- **Visual Personalizável:** Personalize a aparência com suas texturas para base e alavanca do joystick virtual;
- **Ações de Entrada:** Dispara automaticamente os `InputMap` definidos no joystick virtual, assim permitindo usar `Input.get_vector` ou `Input.get_axis` em seus scripts;
- **Feedback Tátil:** Vibração integrada e ajustável para mudanças de direção;
- **Depuração Visual:** Ferramentas para visualizar das áreas de ativação, zonas mortas e limites diretamente na viewport do Godot.

## 🚀 Instalação

1. Mova a pasta `addons/` para dentro do diretório `res://` do seu projeto.
2. Vá para **Projeto -> Configurações do Projeto -> Plugins**.
3. Localize o **Virtual Joystick CF** e altere o status para **Ativado**.

## 🛠️ Modo de Usar

Para garantir que todos os componentes visuais e nós internos funcionem corretamente, você deve instanciar a **Cena do Virtual Joystick**:

### Opção 1: Instância da Cena (Recomendado)
1. Abra a cena onde deseja adicionar o controle (ex: seu HUD ou UI);
2. Clique em **Instantiate Child Scene** ou use suas teclas de atalho *Ctrl+Shift+A*;
3. E escolha a cena `virtual_joystick_cf.tscn`.
> **⚠️ Nota:** Lembre de marcar o checkbox **Addons** localizado no canto inferior direito da janela, para incluir os arquivos do `addons/`.

### Opção 2: Cena do Sistema de Arquivos
1. Abra a cena onde deseja adicionar o controle (ex: seu HUD ou UI);
2. No **Sistema de Arquivos**, vá para `addons/virtual_joystick_cf/`;
3. Arraste o arquivo `virtual_joystick_cf.tscn` para dentro da sua **Árvore de Cenas**.

## ⚙️ Configurações

O **Inspetor** fornece grupos organizados para facilitar a customização:
- **Virtual Joystick:** Desabilite o joystick virtual, configure seu modo de comportamento, ajuste de direção, zona morta e limite do toque.
- **Dynamic Area Margin:** Defina a área de ativação onde o joystick virtual pode ser criado usando margens normalizadas (0.0 a 1.0).
- **Visual:** Atribua suas texturas e ajuste a escala global.
- **Action:** Mapeie o joystick virtual com os `InputMap` (ex: `&ui_up`, `&ui_down`).
- **Vibration:** Ative o feedback tátil e ajuste sua intensidade.
- **Editor:** Ative os desenhos de debug para visualizar a lógica durante os testes nas gameplay ou edição.

## 💻 Integração de Código

### Opção 1: Input Action
Uma vez que as ações estejam mapeadas, o script do seu personagem não precisa saber da existência do joystick virtual:
```gdscript
func _physics_process(_delta: float) -> void:
    var direction: Vector2 = Input.get_vector(
        "ui_left",
        "ui_right",
        "ui_up",
        "ui_down")
    velocity = direction * SPEED
    move_and_slide()
```

### Opção 2: Sinais
Disponíveis sinais para melhor acesso aos eventos, como `pressed`, `released` e `direction_changed` para acesso direto ao `input_direction`:
```gdscript
func _on_joystick_direction_changed(input_direction: Vector2) -> void:
    print("Virtual Joystick CF input_direction: ", input_direction)
```

## 📂 Estrutura do Projeto

- `res://addons/virtual_joystick_cf/`: Raiz do plugin com cena principal, scripts e ícone;
- `res://addons/virtual_joystick_cf/direction_utils`: Utilitário matemático central para manipulação de direções 2D e ajuste de vetores;
- `res://addons/virtual_joystick_cf/example`: Jogo de exemplo para demonstração do Joystick Virtual CF em uso;
- `res://addons/virtual_joystick_cf/textures`: Texturas padrão para a base e alavanca do Joystick Virtual CF;
- `res://addons/virtual_joystick_cf/docs`: Documentações detalhadas para:
  - [Virtual Joystick CF](addons/virtual_joystick_cf/docs/VIRTUAL_JOYSTICK_CF.pt.md);
  - [Direction Utils](addons/virtual_joystick_cf/docs/DIRECTION_UTILS.pt.md).

## ☕ Apoie o Projeto

O desenvolvimento deste plugin é mantido de forma gratuita e independente. Se este plugin for útil para o seu jogo, considere apoiar o **CF Studios**. Qualquer valor é muito bem-vindo!

[![Ko-fi][ko-fi-badge]][ko-fi-link]

## ⚖️ Licença

Distribuído sob a **Licença MIT**. Consulte o arquivo [LICENSE](LICENSE) para obter mais informações. 

Se este plugin for útil para o seu projeto, a atribuição de créditos à **CF Studios** é apreciada, mas não obrigatória por lei (além de manter o arquivo de licença original).

## 📘 Sobre

- **Autor:** Carlos Filho
- **Email:** <cf.studios.dev@gmail.com>

[changelog-badge]: https://img.shields.io/badge/version-1.0.0-blue?
[changelog-link]: CHANGELOG.md
[itch-io-badge]: https://img.shields.io/badge/Itch-%23FF0B34.svg?style=for-the-badge&logo=Itch.io&logoColor=white
[itch-io-link]: https://cf-studios.itch.io/
[ko-fi-badge]: https://img.shields.io/badge/Ko--fi-F16061?style=for-the-badge&logo=ko-fi&logoColor=white
[ko-fi-link]: https://ko-fi.com/cfstudiosdev/donate
[license-badge]: https://img.shields.io/badge/license-MIT-blue
[license-link]: LICENSE
[godot-link]: https://godotengine.org/
[godot-badge]: https://img.shields.io/badge/Godot-4.5+-blue?logo=godot-engine&logoColor=white