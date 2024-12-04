import pygame

pygame.init()
pygame.joystick.init()
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("controller input!")
clock = pygame.time.Clock()

if pygame.joystick.get_count() > 0:
    joystick = pygame.joystick.Joystick(0)
    joystick.init()
else:
    joystick = None

px = 300
py = 300

running = True
while running:
    clock.tick(60)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

        if event.type == pygame.JOYBUTTONDOWN:
            print("Button pressed:", event.button)
            continue
        if event.type == pygame.JOYBUTTONUP:
            print("Button released!")
            continue
        # Handle joystick axis motion
        if event.type == pygame.JOYAXISMOTION:
            print("Axis", event.axis, "moved to", event.value)
            continue

        # Handle joystick hat (D-pad) motion
        if event.type == pygame.JOYHATMOTION:
            print("Hat moved to", event.value)
            continue

    if joystick:
        stick1_x = joystick.get_axis(0)
        stick1_y = joystick.get_axis(1)
        if abs(stick1_x) > 0.01:
            px += stick1_x * 10
        if abs(stick1_y) > 0.01:
            py += stick1_y * 10

    screen.fill((0, 0, 0))
    pygame.draw.rect(screen, (40, 40, 150), (px, py, 50, 50))
    pygame.display.flip()

pygame.quit()
