import pygame
from pygame.draw import *

pygame.init()

FPS = 30
sc = pygame.display.set_mode((1000, 1000))

# задаю цвета (два чёрных цвета нужны для того, чтобы не конфликтовать с "плоскость.set_colorkey(black)")
white = ((255,255,255))
blue = ((0,0,255))
dblue = ((0,30,100))
green = ((0,255,0))
dgreen = ((0,50,15))
red = ((255,0,0))
black = ((0,0,0))
blackw = ((1,1,1))
gray = ((100,100,100))
lgray = ((150,150,150))
llgray = ((200,200,200))
dgray = ((50,50,50))
mg = ((235,245,255))
lime = ((180,255,100))


# земля, небо, луна, облака
rect(sc, dblue, (0, 0, 1000, 500))
rect(sc, dgreen, (0, 500, 1000, 500))
circle(sc, white, (700, 200), 100)
ellipse(sc, gray, (10, 50, 400, 100))
ellipse(sc, lgray, (40, 150, 400, 100))
ellipse(sc, gray, (400, 300, 400, 100))
ellipse(sc, gray, (450, 0, 400, 100))
ellipse(sc, lgray, (150, 250, 400, 100))
ellipse(sc, gray, (250, 150, 400, 100))
ellipse(sc, dgray, (700, 200, 400, 100))
ellipse(sc, dgray, (500, 80, 400, 100))
ellipse(sc, dgray, (600, 350, 400, 100))
ellipse(sc, dgray, (100, 200, 400, 100))

# большая летающая тарелка
ellipse(sc, llgray, (30, 320, 450, 200))
ellipse(sc, white, (110, 300, 300, 150))
ellipse(sc, white, (50, 420, 100, 50))
ellipse(sc, white, (140, 450, 100, 50))
ellipse(sc, white, (260, 455, 100, 50))
ellipse(sc, white, (360, 420, 100, 50))
# свет от тарелки (плоупрозрачный)
li = pygame.Surface((1000, 1000))
li.set_colorkey(black)
li.set_alpha(100)
polygon(li, white, [[180, 517], [290,520], [350,700], [100,700]])
sc.blit(li, (0, 0))


# большой инопланетянин
ellipse(sc, green, (600, 600, 100, 200))
polygon(sc, green, [[590,530], [650,620], [700,520]])
circle(sc, black, (625, 550), 15)
circle(sc, black, (665, 545), 15)
circle(sc, white, (625, 550), 5)
circle(sc, white, (665, 545), 5)
circle(sc, green, (600, 650), 20)
circle(sc, green, (575, 670), 20)
circle(sc, green, (555, 695), 20)
circle(sc, green, (700, 650), 20)
circle(sc, green, (725, 675), 20)
circle(sc, green, (750, 680), 20)
circle(sc, red, (780, 660), 30)
ellipse(sc, lime, (775, 620, 40, 20))
circle(sc, green, (620, 800), 20)
circle(sc, green, (610, 830), 20)
circle(sc, green, (605, 860), 20)
circle(sc, green, (580, 870), 20)
circle(sc, green, (680, 800), 20)
circle(sc, green, (690, 830), 20)
circle(sc, green, (695, 860), 20)
circle(sc, green, (720, 870), 20)



# маленький перевёрнутый инопланетянин под большой тарелкой:
lital = pygame.Surface((1000, 1000))
# убираем чёрный фон
lital.set_colorkey(black)
# сам рисунок
ellipse(lital, green, (600, 600, 100, 200))
polygon(lital, green, [[590,530], [650,620], [700,520]])
circle(lital, blackw, (625, 550), 15)
circle(lital, blackw, (665, 545), 15)
circle(lital, white, (625, 550), 5)
circle(lital, white, (665, 545), 5)
circle(lital, green, (600, 650), 20)
circle(lital, green, (575, 670), 20)
circle(lital, green, (555, 695), 20)
circle(lital, green, (700, 650), 20)
circle(lital, green, (725, 675), 20)
circle(lital, green, (750, 680), 20)
circle(lital, red, (780, 660), 30)
ellipse(lital, lime, (775, 620, 40, 20))
circle(lital, green, (620, 800), 20)
circle(lital, green, (610, 830), 20)
circle(lital, green, (605, 860), 20)
circle(lital, green, (580, 870), 20)
circle(lital, green, (680, 800), 20)
circle(lital, green, (690, 830), 20)
circle(lital, green, (695, 860), 20)
circle(lital, green, (720, 870), 20)
# меняем размер
lital = pygame.transform.scale(lital, (300, 300))
# поворачиваем
lital = pygame.transform.flip(lital, 1, 0)
# добавляем в определённое место
sc.blit(lital, (100, 500))

# средний инопланетянин
lital = pygame.Surface((1000, 1000))
lital.set_colorkey(black)
ellipse(lital, green, (600, 600, 100, 200))
polygon(lital, green, [[590,530], [650,620], [700,520]])
circle(lital, blackw, (625, 550), 15)
circle(lital, blackw, (665, 545), 15)
circle(lital, white, (625, 550), 5)
circle(lital, white, (665, 545), 5)
circle(lital, green, (600, 650), 20)
circle(lital, green, (575, 670), 20)
circle(lital, green, (555, 695), 20)
circle(lital, green, (700, 650), 20)
circle(lital, green, (725, 675), 20)
circle(lital, green, (750, 680), 20)
circle(lital, red, (780, 660), 30)
ellipse(lital, lime, (775, 620, 40, 20))
circle(lital, green, (620, 800), 20)
circle(lital, green, (610, 830), 20)
circle(lital, green, (605, 860), 20)
circle(lital, green, (580, 870), 20)
circle(lital, green, (680, 800), 20)
circle(lital, green, (690, 830), 20)
circle(lital, green, (695, 860), 20)
circle(lital, green, (720, 870), 20)
lital = pygame.transform.scale(lital, (500, 500))
lital = pygame.transform.flip(lital, 0, 0)
sc.blit(lital, (100, 500))

# маленькая летающая тарелка
ufo = pygame.Surface((1000, 1000))
ufo.set_colorkey(black)
# маленькая летающая тарелка (тело)
ellipse(ufo, llgray, (30, 320, 450, 200))
ellipse(ufo, white, (110, 300, 300, 150))
ellipse(ufo, white, (50, 420, 100, 50))
ellipse(ufo, white, (140, 450, 100, 50))
ellipse(ufo, white, (260, 455, 100, 50))
ellipse(ufo, white, (360, 420, 100, 50))
ufo = pygame.transform.scale(ufo, (500, 500))
ufo = pygame.transform.flip(ufo, 1, 0)
sc.blit(ufo, (470, 130))
# свет от vfktymrjq тарелки (плоупрозрачный)
li2 = pygame.Surface((1000, 1000))
li2.set_colorkey(black)
li2.set_alpha(100)
polygon(li2, white, [[180, 517], [290,520], [350,700], [100,700]])
sc.blit(li2, (0, 0))
li2 = pygame.transform.scale(li2, (500, 500))
li2 = pygame.transform.flip(li2, 1, 0)
sc.blit(li2, (460, 130))

# чтобы работало))
pygame.display.update()
clock = pygame.time.Clock()
finished = False

while not finished:
    clock.tick(FPS)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            finished = True

pygame.quit()