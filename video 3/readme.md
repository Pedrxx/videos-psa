# Função `desenhar_rodar_item`

A função `desenhar_rodar_item` é responsável por exibir uma imagem rotacionada de um objeto em uma tela, posicionando-a corretamente no centro. Essa função é particularmente útil em aplicações como jogos ou simulações visuais, onde objetos precisam ser desenhados com rotações dinâmicas.

## Objetivo

O principal objetivo da função é:

1. Redimensionar a imagem do item conforme as dimensões especificadas.
2. Rotacionar a imagem em um ângulo definido.
3. Posicionar a imagem rotacionada no centro de um ponto específico na tela.
4. Desenhar a imagem rotacionada na tela.

## Como Funciona

1. **Redimensionamento da imagem**:
   A função utiliza a imagem original do item e ajusta suas dimensões para as especificadas nos atributos do objeto `item` (`largura` e `altura`).

2. **Rotação da imagem**:
   A função rotaciona a imagem redimensionada utilizando o método `pygame.transform.rotate`, aplicando o ângulo fornecido como parâmetro.

3. **Centralização da imagem**:
   A posição do item é usada como referência para centralizar a imagem rotacionada na tela.

4. **Desenho na tela**:
   A imagem rotacionada é renderizada na tela utilizando o método `blit`.

## Implementação

```python
def desenhar_rodar_item(item, angulo):
    """
    Desenha e rotaciona um item na tela.

    Args:
        item (Objeto): Objeto que contém informações sobre a imagem, posição, largura e altura.
        angulo (float): Ângulo em graus para rotacionar a imagem.

    Returns:
        pygame.Surface: Retorna a superfície onde a imagem rotacionada foi desenhada.
    """
    # Redimensiona a imagem do item
    imagem = redimensionar_imagem(item.imagem, item.largura, item.altura)
    
    # Rotaciona a imagem
    imgame_rodada = pygame.transform.rotate(imagem, angulo)
    
    # Centraliza a imagem na posição do item
    image_centro = item.imagem.get_rect(center=(item.posicao.x, item.posicao.y))
    rodada_centro = imgame_rodada.get_rect(center=image_centro.center)
    
    # Obtém a tela para desenhar
    tela = retornar_tela()
    
    # Desenha a imagem rotacionada na tela
    return tela.blit(imgame_rodada, rodada_centro)
```

## Argumentos
* item (Objeto): O objeto a ser desenhado. Deve possuir os seguintes atributos:

* imagem: A imagem associada ao objeto.
* posicao: As coordenadas (x, y) da posição do objeto.
* largura e altura: As dimensões da imagem desejadas.
angulo (float): O ângulo de rotação em graus. 

* Valores positivos rotacionam no sentido anti-horário.

## Aplicações
A função desenhar_rodar_item é ideal para:

* Jogos 2D: Exibir objetos como veículos, armas, ou personagens que precisam rotacionar dinamicamente.
* Simulações visuais: Mostrar movimento de objetos em trajetórias curvas.
Animações: Criar efeitos de rotação em elementos gráficos.