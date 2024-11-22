# Função `lidar_entrada`

A função `lidar_entrada` é responsável por capturar e processar as entradas do jogador (teclado e eventos) e, com base nessas entradas, alterar o comportamento do personagem no jogo. Um dos principais focos dessa função é gerenciar a troca de sprites do personagem para refletir suas ações, como movimento para esquerda, direita ou inatividade.

## Objetivo

- Capturar eventos e entradas do jogador.
- Alterar o estado do personagem com base nas entradas.
- Atualizar o sprite do personagem para refletir sua última ação ou direção.

## Como Funciona

1. **Captura de Eventos**:
   Utiliza o adaptador `pygame_input_adapter` para capturar eventos e interações, como teclas pressionadas ou fechamento da janela.

2. **Movimento do Personagem**:
   - Com base nas teclas pressionadas (`esquerda`, `direita`, ou `esc`), a função altera a posição e a velocidade do personagem.
   - Verifica os limites da tela para impedir que o personagem ultrapasse as bordas.

3. **Troca de Sprites**:
   - Troca o sprite do personagem dinamicamente de acordo com a direção do movimento ou estado de inatividade:
     - **Movimento para a Esquerda**: Usa `animar_personagem_esquerda` para animar o personagem enquanto ele se move para a esquerda.
     - **Movimento para a Direita**: Usa `animar_personagem_direita` para animar o personagem enquanto ele se move para a direita.
     - **Personagem Parado**: Define o sprite apropriado para a última direção em que o personagem estava (esquerda ou direita).

4. **Gerenciamento de Eventos Especiais**:
   - Fecha o jogo se o evento de saída for detectado.
   - Reinicia o jogo ao pressionar `esc`.

## Implementação

```python
def lidar_entrada(self):
    """
    Processa as entradas do jogador e gerencia a troca de sprites do personagem.

    Args:
        None

    Returns:
        None
    """
    # Captura os eventos do jogo
    for evento in pygame_input_adapter.capturar_eventos():
        if pygame_input_adapter.eh_sair(evento):
            self.is_running = False
            quit()
    
    # Captura as teclas pressionadas
    tecla_pressionada = pygame_input_adapter.capturar_tecla()
    
    # Movimento para a esquerda
    if tecla_pressionada['esquerda']:
        if isinstance(self.fase_model.personagem, Personagem):
            self.sprite_atual = self.sprites.animar_personagem_esquerda()
            self.ultima_posicao = 'esquerda'
            if self.fase_model.personagem.posicao.x >= 0:
                self.fase_model.personagem.velocidade.x = -500
            else:
                self.fase_model.personagem.velocidade.x = 0
    
    # Movimento para a direita
    elif tecla_pressionada['direita']:
        if isinstance(self.fase_model.personagem, Personagem):
            self.sprite_atual = self.sprites.animar_personagem_direita()
            self.ultima_posicao = 'direita'
            if self.fase_model.personagem.posicao.x <= 700:
                self.fase_model.personagem.velocidade.x = +500
            else:
                self.fase_model.personagem.velocidade.x = 0
    
    # Reinicia o jogo ao pressionar ESC
    elif tecla_pressionada['esc']:
        gerenciar_jogo.iniciar_jogo(self.tela_largura, self.tela_altura)
    
    # Personagem parado
    else:
        if isinstance(self.fase_model.personagem, Personagem):
            self.fase_model.personagem.velocidade.x = 0
            if self.ultima_posicao == 'esquerda':
                self.sprite_atual = self.sprites.get_personagem_sprite_esquerda_parado()
            else:
                self.sprite_atual = self.sprites.get_personagem_sprite_direita_parado()
```

## Foco na Troca de Sprites
A troca de sprites é um aspecto essencial da função, pois:

### Feedback Visual:

* A troca de sprites informa ao jogador sobre o estado atual do personagem, como movimento ou inatividade.
Cria uma experiência visual mais envolvente e intuitiva.
Dinamismo:

* Permite que o jogo reaja visualmente às ações do jogador, tornando a experiência mais imersiva.
Facilidade de Escalabilidade:

* A troca de sprites é modular e facilmente expansível. Por exemplo, novos estados ou animações podem ser adicionados, como "pulando" ou "atacando".
Consistência na Lógica do Jogo:

* Mantém o sprite sincronizado com o estado lógico do personagem, como direção e velocidade.

## Aplicações
* Jogos de Plataforma: Troca de sprites para indicar direção e ações como andar, correr ou parar.

* Animações Dinâmicas: Garante que o personagem sempre tenha uma aparência visual condizente com o movimento.

* Jogos Imersivos: Melhora a experiência do jogador com transições suaves e visuais consistentes.

A função lidar_entrada é um exemplo de boa prática no desenvolvimento de jogos, promovendo modularidade, clareza e uma experiência de jogo mais rica.