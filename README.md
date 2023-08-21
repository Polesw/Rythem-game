# Rythem-game
simple rythem game

from pygame import *
from random import randint

win_width = 500
win_height = 900
clock = time.Clock()

img_down_arrow = "/Users/jakeduker/Desktop/rythem game things/down arrow.png" # arrow facing down
img_up_arrow = "/Users/jakeduker/Desktop/rythem game things/up arrow.png" # arrow facing up
img_right_arrow = "/Users/jakeduker/Desktop/rythem game things/right arrow.png" # arrow facing right
img_left_arrow = "/Users/jakeduker/Desktop/rythem game things/left arrow.png"#arrow facing left
img_back ="/Users/jakeduker/Desktop/rythem game things/background.png" #background

window = display.set_mode((win_width, win_height))
background = transform.scale(image.load(img_back),(win_width, win_height))
display.set_caption("RYTHEM")

class GameSprite(sprite.Sprite):
 #class constructor
   def __init__(self, player_image, player_x, player_y, size_x, size_y, player_speed):
       #Call for the class (Sprite) constructor:
       sprite.Sprite.__init__(self)


       #every sprite must store the image property
       self.image = transform.scale(image.load(player_image), (size_x, size_y))
       self.speed = player_speed


       #every sprite must have the rect property that represents the rectangle it is fitted in
       self.rect = self.image.get_rect()
       self.rect.x = player_x
       self.rect.y = player_y
 #method drawing the character on the window
   def draw(self):
       window.blit(self.image, (self.rect.x, self.rect.y))



#arrow sprite classes
class Up_arrow(GameSprite):
   #up arrow movement
   def update(self):
       self.rect.y += self.speed
       global lost
       #disappears upon reaching the screen edge
       if self.rect.y > win_height:
           self.rect.x = 217.5
           self.rect.y = 0


class Down_arrow(GameSprite):
   #down arrow movement
   def update(self):
       self.rect.y += self.speed
       global lost
       #disappears upon reaching the screen edge
       if self.rect.y > win_height:
           self.rect.x = 93.5
           self.rect.y = 0

class Left_arrow(GameSprite):
   #left arrow movement
   def update(self):
       self.rect.y += self.speed
       global lost
       #disappears upon reaching the screen edge
       if self.rect.y > win_height:
           self.rect.x = 20.5
           self.rect.y = 0

class Right_arrow(GameSprite):
   #right arrow movement
   def update(self):
       self.rect.y += self.speed
       global lost
       #disappears upon reaching the screen edge
       if self.rect.y > win_height:
           self.rect.x = 280.5
           self.rect.y = 0

up1 = Up_arrow(img_up_arrow,217.5,0,200,200,10)
down1 = Down_arrow(img_down_arrow,93.5,-120,200,200,10)
right1 = Right_arrow(img_right_arrow,280.5,-67,200,200,10)
left1 = Left_arrow(img_left_arrow,20.5,-67,200,200,10)
   #monsters.add(up_arrow)

#the window
run = True #the flag is reset by the window close button
while run:
   #"Close" button press event
    for e in event.get():
        if e.type == QUIT:
           run = False
    
    window.fill((255,255,255))
    window.blit(background,(0,0))
    left1.draw()
    left1.update()
    right1.draw()
    right1.update()
    down1.draw()
    down1.update()
    up1.draw()
    up1.update()
    display.update()
    clock.tick(60)

