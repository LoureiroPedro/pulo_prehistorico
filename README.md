# pulo_prehistorico
//Bot criado para o joguinho do dinossauro do chrome //

import time

from PIL import ImageGrab
import pyautogui

# dino_position  = 107, 445
# inimigo_color = 83, 83, 83

X = 319

def capture_screen():
    
    screen = ImageGrab.grab()
    return screen

def detect_enemy(screen):
    aux_color = screen.getpixel((int(X), 390))    
    for x in range(int(X+15), 390):
        for y in range(353, 450):    
            color = screen.getpixel((x, y))
            if color != aux_color:
                return True
            else:
                aux_color = color

def jump():
    global X
    pyautogui.press("up")
    X += 0.4
    
    
print("Start 3 segundos ....")

time.sleep(3)
while True:
   screen = capture_screen()
   if detect_enemy(screen):
       jump()
