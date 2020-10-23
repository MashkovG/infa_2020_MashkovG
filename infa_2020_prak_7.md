# результаты игры сохряняются на диске D в виде текстогого файла с названием "leaderboard"
# перед игрой не забудьте ввести имя
import pygame
from pygame.draw import *
from random import randint
import time
pygame.init()

name = input('gimme yooor naaame')

FPS = 2
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
    '''рисует новый шарик'''
    global x, y, r
    x = randint(100, 1100)
    y = randint(100, 900)
    r = randint(10, 100)
    color = COLORS[randint(0, 5)]
    circle(screen, color, (x, y), r)
    pygame.display.update()

def new_square():
    global a, s, d, f
    a = randint(100, 1100)
    s = randint(100, 900)
    d = randint(20, 50)
    f = randint(20, 50)
    color = COLORS[randint(0, 5)]
    rect(screen, color, (a,s,d,f))
    pygame.display.update()

screen.fill(MAGENTA)
rect(screen, YELLOW, (500,400,200,100))
pygame.display.update()
finished = False
start = False
while start == False:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            print(n)
            finished = True
        elif event.type == pygame.MOUSEBUTTONDOWN:
            if event.button == 1:
                if event.pos[0] >= 500 and event.pos[0] <= 700 and event.pos[1] >= 400 and event.pos[1] <= 500:
                    start = True

screen.fill(BLACK)
pygame.display.update()
clock = pygame.time.Clock()

num = 0
t = 0
while not finished:
    strike = False
    clock.tick(FPS)
    k = 0
    new_ball()
    q = x
    w = y
    e = r
    new_ball()
    new_square()
    g = randint(0, 1)
    h = randint(0, 1)
    screen.fill(BLACK)

    if strike == False:
        while k <= 10 and strike == False:
            q += randint(-10, 10)
            w += randint(-10, 10)
            e += randint(-10, 20)
            x += randint(-10, 10)
            y += randint(-10, 10)
            r += randint(-10, 20)
            if g == 0:
                a += 20
            if g == 1:
                a -= 20
            if h == 0:
                s += 20
            if h == 0:
                s -= 20
            color = COLORS[randint(0, 5)]
            circle(screen, color, (x, y), r)
            circle(screen, color, (q, w), e)
            rect(screen, color, (a,s,d,f))
            pygame.display.update()
            screen.fill(BLACK)
            time.sleep(0.1)

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
                            num += 1
                            strike = True
                        elif (abs(event.pos[0] - q))^2 + (abs(event.pos[1] - w))^2 <= e:
                            num += 1
                            strike = True
                        elif event.pos[0] >= a and event.pos[0] <= a+d and event.pos[1] >= s and event.pos[1] <= s+f:
                            num += 2
                            strike = True
            k += 1
            t += 1
    if t >= 70:
        finished = True
        screen.fill(RED)
        pygame.display.update()
        file = open("D:\leaderboard.txt", 'a')
        file.write(str(name)+ ' - ' + str(num) + '\n')
        file.close()



pygame.quit()

