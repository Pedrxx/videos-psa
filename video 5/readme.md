# Configurações do Jogo (`settings.json`)

O arquivo `settings.json` contém as configurações principais para o funcionamento do jogo, organizadas em categorias como vídeo, sons e sprites. Este arquivo desempenha um papel crucial na personalização e gerenciamento do comportamento do jogo, oferecendo uma abordagem centralizada e flexível para ajustes.

## Estrutura do Arquivo

### 1. Configurações de Vídeo (`video`)
Define as propriedades relacionadas à exibição da interface gráfica do jogo.

```json
"video": {
    "screen_width": 800,
    "screen_height": 600,
    "fullscreen": false
}
```

* screen_width e screen_height: Determinam a resolução da tela do jogo.
* fullscreen: Define se o jogo será exibido em tela cheia (true) ou em modo janela (false).

### 2. Configurações de Sons (sons)
Gerencia as propriedades relacionadas ao áudio, como diretórios e volumes.

```json
Copiar código
"sons": {
    "sons_dir": "./adapters/primary/sons/",
    "volume_menu_inicial": 0.1,
    "volume_efeitos": 0.2
}
```

* sons_dir: Caminho para os arquivos de som utilizados no jogo.
* volume_menu_inicial: Volume inicial para a música ou sons no menu principal.
* volume_efeitos: Volume para os efeitos sonoros durante o jogo.

### 3. Configurações de Sprites (sprites)

Controla os diretórios onde os sprites do jogo estão localizados.

```json
Copiar código
"sprites": {
    "sprites_dir": "./adapters/primary/sprites/"
}
```

* sprites_dir: Caminho para os arquivos de sprites, como personagens, itens ou cenários.

## Importância das Configurações
O uso de um arquivo de configurações como este é fundamental para o desenvolvimento e a manutenção de jogos. Aqui estão os principais benefícios:

### 1. Centralização de Configurações
Todas as configurações essenciais estão em um único lugar, facilitando a leitura, manutenção e ajuste.
### 2. Personalização e Escalabilidade
Desenvolvedores e jogadores podem ajustar facilmente a experiência do jogo sem alterar diretamente o código. Exemplo: Alterar a resolução da tela ou os volumes de som.
### 3. Reutilização e Modularidade
Os valores definidos no settings.json podem ser reutilizados em diferentes módulos do jogo, garantindo consistência e redução de código repetitivo.
### 4. Facilidade para Depuração
Alterar parâmetros como resolução ou volumes é rápido e não requer recompilação, permitindo testes ágeis.
### 5. Adaptação para Diferentes Ambientes
Pode ser ajustado para rodar o jogo em diferentes dispositivos ou contextos (ex.: habilitar tela cheia para PCs e resolução reduzida para dispositivos móveis).

## Aplicações

* Configurações de Vídeo: Permitem que o jogo seja executado em diferentes hardwares com ajustes de resolução e modos de exibição.
* Configurações de Áudio: Facilitam o controle do volume ou a substituição de trilhas sonoras sem modificar o código-fonte.
* Configurações de Sprites: Garantem que os diretórios de assets sejam organizados, permitindo expansões ou modificações simples.
