import pygame
from pygame.draw import *
import pygame.freetype
pygame.init()
FPS = 30
screen = pygame.display.set_mode((1000, 500))

skin = (255, 213, 176)
brown = (117, 79, 55)
black = (0, 0, 0)
red = (255, 0, 0)
pink = (222, 194, 164)
white = (255, 255, 255)
cyan = (123, 209, 175)
green = (50, 150, 8)
yellow = (255, 255, 0)
lblue = (112, 203, 255)
orange = (255, 136, 0)
purple = (183, 0, 255)
lgreen = (0, 51, 0)

def draw_human(x, y, eyescoolor, clothescolor, haircolor):
    '''
    функция рисует человека
    x, y - координаты центра головы
    eyescoolor - цвет глаз
    clothescolor - цвет одежды
    haircolor - цвет волос
    '''
    hair(x, y, haircolor)
    circle(screen, clothescolor, (x, y + 240), 140)
    circle(screen, skin, (x, y + 5), 130)
    eye(x - 42, y - 25, eyescoolor)
    eye(x + 42, y - 25, eyescoolor)
    nose(x, y + 20)
    mouth(x, y + 65)
    larm(x - 130, y + 110)
    rarm(x + 130, y + 110)
    hand(x - 165, y - 180)
    hand(x + 165, y - 180)
    pentagon(x - 120, y + 110, clothescolor)
    pentagon(x + 96, y + 110, clothescolor)
    polygon(screen, (0, 255, 0), ([(x - 200, y - 180), (x + 200, y - 180), (x + 200, y - 230), (x - 200, y - 230)]) )
def eye(x, y, eyescoolor):
    '''
    функция рисует глаза
    x, y - координаты центра головы
    eyescoolor - цвет глаз
    '''
    circle(screen, eyescoolor, (x, y), 28)
    circle(screen, black, (x, y), 28, 1)
    circle(screen, black, (x, y), 7)
def nose(x, y):
    '''
    функция рисует нос
    x, y - координаты центра головы
    '''
    polygon(screen, brown, [(x - 15, y - 13),
     (x + 15, y - 13), (x, y + 13)])
    polygon(screen, black, [(x - 15, y - 13),
     (x + 15, y - 13), (x, y + 13)], 1)
def mouth(x, y):
    '''
    функция рисует рот
    x, y - координаты центра головы
    '''
    polygon(screen, red,
    [(x - 75, y - 25),
     (x + 75, y - 25), (x, y + 25)])
    polygon(screen, black,
    [(x - 75, y - 25),
     (x + 75, y - 25), (x, y + 25)], 1)
def pentagon(x, y, clothescolor):
    '''
    функция рисует рукава
    x, y - координаты центра головы
    clothescolor - цвет одежды
    '''
    polygon(screen, clothescolor,
    [(x + 45, y),
     (x + 30, y + 45), (x - 10, y + 45),
     (x - 20, y), (x + 10, y - 25)])
    polygon(screen, black,
    [(x + 45, y),
     (x + 30, y + 45), (x - 10, y + 45),
     (x - 20, y), (x + 10, y - 25)], 1)
def larm(x, y):
    '''
    функция рисует левую руку
    x, y - координаты центра головы
    '''
    polygon(screen, pink, 
    [(x + 10, y - 10), (x, y),
     (x - 40, y - 300), (x - 25, y - 300)])
def rarm(x, y):
    '''
    функция рисует правую руку
    x, y - координаты центра головы
    '''
    polygon(screen, pink, 
    [(x - 10, y - 10), (x, y),
     (x + 40, y - 300), (x + 25, y - 300)])
def hand(x, y):
    '''
    функция рисует кисти
    x, y - координаты центра головы
    '''
    circle(screen, white, (x, y), 21)
    circle(screen, pink, (x, y), 20)
def hair(x, y, haircolor):
    '''
    функция рисует волосы
    x, y - координаты центра головы
    haircolor - цвет волос
    '''
    for i in range(10):
        polygon(screen, haircolor, 
        [(x - 50, y), (x + 50, y), (x - i * 14, y - 140 + i * i * 0.5)])
        polygon(screen, haircolor, 
        [(x - 50, y), (x + 50, y), (x + i * 14, y - 140 + i * i * 0.5)])

#у меня нет файла со шрифтом, так что картинка без текста 
        
draw_human(250, 250, cyan, green, yellow)
draw_human(580, 250, lblue, orange, purple)
# FONT = pygame.freetype.Font("Calibri.ttf", 50)
# FONT.render_to(screen, (120, 30), "PYTHON is REALLY AMAZING", lgreen)

pygame.display.update()
clock = pygame.time.Clock()
finished = False
while not finished:
    clock.tick(FPS)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            finished = True
pygame.quit()