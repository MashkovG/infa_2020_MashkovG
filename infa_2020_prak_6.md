import pygame
from pygame.draw import *
from random import randint
import time
pygame.init()

FPS = 1
screen = pygame.display.set_mode((1200, 900))

RED = (255, 0, 0)
BLUE = (0, 0, 255)
YELLOW = (255, 255, 0)
GREEN = (0, 255, 0)
MAGENTA = (255, 0, 255)
CYAN = (0, 255, 255)
BLACK = (0, 0, 0)
COLORS = [RED, BLUE, YELLOW, GREEN, MAGENTA, CYAN]

def new_ball():
    '''рисует новый шарик '''
    global x, y, r
    x = randint(100, 1100)
    y = randint(100, 900)
    r = randint(10, 100)
    color = COLORS[randint(0, 5)]
    circle(screen, color, (x, y), r)
    pygame.display.update()

pygame.display.update()
clock = pygame.time.Clock()
finished = False

n = 0
while not finished:
    strike = False
    clock.tick(FPS)
    k = 0
    new_ball()
    q = x
    w = y
    e = r
    new_ball()
    screen.fill(BLACK)

    if strike == False:
        while k <= 10 and strike == False:
            q += randint(-10, 10)
            w += randint(-10, 10)
            e += randint(-10, 10)
            x += randint(-10, 10)
            y += randint(-10, 10)
            r += randint(-10, 10)
            color = COLORS[randint(0, 5)]
            circle(screen, color, (x, y), r)
            circle(screen, color, (q, w), e)
            pygame.display.update()
            screen.fill(BLACK)
            time.sleep(0.3)
            if x < 0:
                x += 50
            elif x > 1200:
                x -= 50
            elif y < 0:
                y += 50
            elif y > 1200:
                y -= 50
            elif r < 11:
                r += 10
            elif r > 30:
                r -= 10
            if q < 0:
                q += 50
            elif q > 1200:
                q -= 50
            elif w < 0:
                w += 50
            elif w > 1200:
                w -= 50
            elif e < 11:
                e += 10
            elif e > 30:
                e -= 10
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    print(n)
                    finished = True
                elif event.type == pygame.MOUSEBUTTONDOWN:
                    if event.button == 1:
                        if (abs(event.pos[0] - x))^2 + (abs(event.pos[1] - y))^2 <= r:
                            n += 1
                            strike = True
                        elif (abs(event.pos[0] - q))^2 + (abs(event.pos[1] - w))^2 <= e:
                            n += 1
                            strike = True
            k += 1
    else: break

pygame.quit()

