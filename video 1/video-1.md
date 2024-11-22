# Função `lidar_entrada`

A função `lidar_entrada` gerencia os eventos de entrada do usuário em um jogo desenvolvido com Pygame. Ela captura os eventos do teclado e realiza ações específicas com base nas teclas pressionadas, incluindo movimentação do personagem e troca de sprites.

## Funcionalidades

1. **Captura de Eventos**:
   - Utiliza o adaptador `pygame_input_adapter` para capturar eventos e identificar se o usuário deseja sair do jogo.

2. **Movimentação do Personagem**:
   - Move o personagem para a esquerda ou direita ao pressionar as respectivas teclas.
   - Restringe a movimentação horizontal do personagem dentro dos limites de 0 a 700.

3. **Troca de Sprites**:
   - Atualiza o sprite do personagem para corresponder à direção do movimento (esquerda ou direita).
   - Garante que o sprite correto seja exibido quando o personagem está parado.

4. **Ação Personalizada para `ESC`**:
   - Ao pressionar a tecla `ESC`, o jogo reinicia com base na largura e altura da tela configuradas.

## Destaques: Troca de Sprites

A função faz uso do objeto `sprites` para trocar os sprites do personagem conforme o estado atual:

- **Movimento para a Esquerda**:
  - Atualiza o sprite para uma animação de movimento para a esquerda utilizando `self.sprites.animar_personagem_esquerda()`.

- **Movimento para a Direita**:
  - Atualiza o sprite para uma animação de movimento para a direita utilizando `self.sprites.animar_personagem_direita()`.

- **Personagem Parado**:
  - Quando o personagem não está se movendo, o sprite retorna ao estado parado:
    - Se a última posição foi à esquerda: `self.sprites.get_personagem_sprite_esquerda_parado()`.
    - Se a última posição foi à direita: `self.sprites.get_personagem_sprite_direita_parado()`.

## Dependências

- **`pygame_input_adapter`**: Um adaptador para gerenciar entradas do Pygame.
- **`Personagem`**: Classe que define o personagem do jogo.
- **`sprites`**: Objeto responsável por fornecer as animações e sprites estáticos para o personagem.
- **`gerenciar_jogo`**: Módulo que permite reiniciar o jogo.

## Exemplos de Uso

### 1. Movimento para a Esquerda
Ao pressionar a tecla "esquerda":
- O sprite muda para uma animação de movimento para a esquerda.
- A posição do personagem é atualizada se ele estiver dentro dos limites da tela.

### 2. Movimento para a Direita
Ao pressionar a tecla "direita":
- O sprite muda para uma animação de movimento para a direita.
- A posição do personagem é atualizada de forma similar.

### 3. Personagem Parado
Ao soltar as teclas de movimento:
- O sprite muda para o estado "parado" na última direção registrada (esquerda ou direita).

---

Com essa função, a interação entre o jogador e o jogo é fluida, e a experiência visual do personagem é dinâmica e responsiva às ações do jogador.
