import pygame
import random
import os

pygame.init()
size = width, height = 800, 500
screen = pygame.display.set_mode(size)
screen.fill((255, 255, 255))
clock = pygame.time.Clock()
FPS = 50


main_window_sprite = pygame.sprite.Group()
picture_for_start = pygame.sprite.Group()
now_sprite = picture_for_start
all_sprites = pygame.sprite.Group()


def load_image(name, color_key=None):
    fullname = os.path.join('data', name)
    try:
        image = pygame.image.load(fullname).convert()
    except pygame.error as message:
        print('Cannot load image:', name)
        raise SystemExit(message)

    if color_key is not None:
        if color_key == -1:
            color_key = image.get_at((0, 0))
        image.set_colorkey(color_key)
    else:
        image = image.convert_alpha()
    return image


# class First_Window():
#     surf = pygame.Surface(width, height)
#     surf.fill((255, 255, 255))



class StartGame(pygame.sprite.Sprite):
    # image = pygame.image.load('data/fon23.png').convert_alpha()
    # image = load_image('fon23.png', color_key=-1)
    image = load_image('coin_pos1.png', color_key=-1)

    def __init__(self, *group):
        super().__init__(*group)
        self.image = StartGame.image
        self.rect = self.image.get_rect()
        self.rect.center = (self.rect.width // 2, self.rect.height // 2 - 20)

    def update(self, event):
        if self.rect.collidepoint(event.pos):
            print(44)

def start_game():
    image = load_image('fon_main_window.png')

# def draw_sprites(name):
#     name.draw(screen)
#     name.update(event)


# first = First_window(all_sprites, picture_for_start)
# settings = Settings(all_sprites)
# running = True
# while running:
#     for event in pygame.event.get():
#         if event.type == pygame.QUIT:
#             running = False
#         if event.type == pygame.MOUSEBUTTONDOWN:
#             now_sprite.update(event)
#     pygame.display.flip()
#     draw_sprites(now_sprite)
#     clock.tick(FPS)
# pygame.quit()
