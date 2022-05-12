---
layout: post
---

Hello world!
This is the current date and time, as computed by Python:


<html lang="en">
    <head>
      <script defer src="https://pyscript.net/alpha/pyscript.js"></script>
      <py-env>
        - pygame
      </py-env>
    </head>

  <body>
    <h1>Let's plot random numbers</h1>
    <div id="plot"></div>
    <py-script output="plot">
import pygame
pygame.init()
scr = pygame.display.set_mode((600, 500))
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    scr.fill((255, 255, 255))
    pygame.draw.circle(scr, (200, 0, 0), (250, 250), 80)
    pygame.display.flip()
pygame.quit()
    </py-script>
  </body>
</html>