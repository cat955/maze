import pygame

pygame.init()

display_width = 800
display_height = 600

# declares some colors
black = (0, 0, 0)
white = (255, 255, 255)

# creates the game display and game clock
gameDisplay = pygame.display.set_mode((display_width, display_height))
pygame.display.set_caption('Spirit Hallows')
clock = pygame.time.Clock()

# loads the different characters images
main_char_image = pygame.image.load('Y:\HauntedHouseCharacterSmall.png')
ghost_girl_char_image = pygame.image.load('Y:\Ghostgirl.png')
fire_boy_char_image = pygame.image.load('Y:\Firedude.png')
water_girl_char_image = pygame.image.load('Y:\watergirl.png')
blu_char_image = pygame.image.load('Y:\improvedversionofPG.png')
background_image_before = pygame.image.load('Y:\BlockMazeCopy.png')
background_image = pygame.transform.rotozoom(background_image_before, 0, 3)


# moves the background
def background_dis(background_func_x, background_func_y):
    gameDisplay.blit(background_image, (background_func_x, background_func_y))


# moves the given object/character, given the image of the character, and its x and y position
def character(char_image, cur_char_x, cur_char_y):
    gameDisplay.blit(char_image, (cur_char_x, cur_char_y))

# declaring all the characters x and y positions
main_char_x = (display_width/2.0) - 20.0
main_char_y = (display_height/4.0)
ghost_girl_x = (display_width/4.5)
ghost_girl_y = (display_height/4.5)
background_x = -400
background_y = 0
fire_boy_x = (display_width/3.5)
fire_boy_y = (display_height/3.5)
water_girl_x = (display_width/3.0)
water_girl_y = (display_height/3.0)
blu_x = (display_width/2.0)
blu_y = (display_height/2.0)

# declares the different characters x change and y change movement variables
main_char_x_change = 0
main_char_y_change = 0
ghost_girl_x_change = 0
ghost_girl_y_change = 0
background_x_change = 0
background_y_change = 0
fire_boy_x_change = 0
fire_boy_y_change = 0
water_girl_x_change = 0
water_girl_y_change = 0
blu_x_change = 0
blu_y_change = 0

# sets the game to not have crashed yet
crashed = False

# runs the game
while not crashed:

    # checks events
    for event in pygame.event.get():
        # if the user wants to quit, changes crashed to true and quits
        if event.type == pygame.QUIT:
            crashed = True

        # if a movement key is down, move the character
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_a:
                main_char_x_change = -5
            elif event.key == pygame.K_d:
                main_char_x_change = 5
            if event.key == pygame.K_w:
                main_char_y_change = -5
            elif event.key == pygame.K_s:
                main_char_y_change = 5

        # moves the main character FLUENTLY
        if event.type == pygame.KEYUP:
            if event.key == pygame.K_a:
                pressed = pygame.key.get_pressed()
                if pressed[pygame.K_d]:
                    main_char_x_change = 5
                else:
                    main_char_x_change = 0

        if event.type == pygame.KEYUP:
            if event.key == pygame.K_d:
                pressed = pygame.key.get_pressed()
                if pressed[pygame.K_a]:
                        main_char_x_change = -5
                else:
                    main_char_x_change = 0

        if event.type == pygame.KEYUP:
            if event.key == pygame.K_w:
                pressed = pygame.key.get_pressed()
                if pressed[pygame.K_s]:
                        main_char_y_change = 5
                else:
                    main_char_y_change = 0

        if event.type == pygame.KEYUP:
            if event.key == pygame.K_s:
                pressed = pygame.key.get_pressed()
                if pressed[pygame.K_w]:
                        main_char_y_change = -5
                else:
                    main_char_y_change = 0
        """
        # if a key is picked up, stops moving the character
        if event.type == pygame.KEYUP:
            if event.key == pygame.K_a:
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_d:
                        main_char_x_change = 5
                    else:
                        main_char_x_change == 0
                else:
                    main_char_x_change = 0
            elif event.key == pygame.K_d:
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_a:
                        main_char_x_change = -5
                    #else:
                        #main_char_x_change == 0
                else:
                    main_char_x_change = 0

            if event.key == pygame.K_w:
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_s:
                        main_char_y_change = 5
                    else:
                        main_char_y_change == 0
                else:
                    main_char_y_change = 0
            elif event.key == pygame.K_s:
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_w:
                        main_char_y_change = -5
                    else:
                        main_char_y_change == 0
                else:
                    main_char_y_change = 0
        """

        # original movement code before trying to make it more fluent
        """
        if event.type == pygame.KEYUP:
            if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
                main_char_x_change = 0

        if event.type == pygame.KEYUP:
             if event.key == pygame.K_UP or event.key == pygame.K_DOWN:
                main_char_y_change = 0
        """

    # changes the different characters positions based on their x change and y change variables
    main_char_x += main_char_x_change
    main_char_y += main_char_y_change
    ghost_girl_x += ghost_girl_x_change
    ghost_girl_y += ghost_girl_y_change
    fire_boy_x += fire_boy_x_change
    fire_boy_y += fire_boy_y_change
    water_girl_x += water_girl_x_change
    water_girl_y += water_girl_y_change
    blu_x += blu_x_change
    blu_y += blu_y_change

    """
    # wall limits and door movement through first two rooms working on another room, the bottom one to the left,
    # background changes by 1 pixel depending on the room

    #room 1, background at (-400,0)
    if background_x == -400 and background_y == 0:
        if main_char_y >= 205:
            if not(main_char_x >= 325 and main_char_x <= 410):
                main_char_y = 205
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_e:
                    background_x = -401
                else:
                    main_char_y = 205
            else:
                main_char_y = 205
        elif main_char_y <= 105:
            main_char_y = 105

        if main_char_x <= 270:
            main_char_x = 270
        elif main_char_x >= 695:
            main_char_x = 695

    #room 2, background at (-401,0)
    if background_x == -401 and background_y == 0:
        if main_char_y >= 255 and not(main_char_x >= 105 and main_char_x <= 160):
            main_char_y = 255
        elif not(main_char_x >= 325 and main_char_x <= 410)and not(main_char_x >= 105 and main_char_x <= 160) and main_char_y <= 254:
                main_char_y = 254
        elif main_char_x >= 325 and main_char_x <= 410:
            if event.type == pygame.KEYDOWN or main_char_y <= 253:
                if event.key == pygame.K_e:
                    if main_char_y <= 205:
                        background_x = -400
                else:
                    main_char_y = 254
            else:
                main_char_y = 254
        elif main_char_x >= 105 and main_char_x <= 160:
            if main_char_y <= 254:
                main_char_y = 254
            if main_char_y >= 445:
                main_char_y = 445

        if main_char_x <= 105:
            main_char_x = 105
        elif main_char_x >= 465:
            main_char_x = 465
        if main_char_y >254 and not(main_char_x >= 165 and main_char_x <= 465):
            if main_char_x >= 160:
                main_char_x = 155
            if main_char_x <= 105:
                main_char_x = 110
        if main_char_x == 110 and main_char_y >= 445:
            if event.type == pygame.KEYDOWN or main_char_x <= 110:
                if event.key == pygame.K_e:
                    if main_char_x <= 110:
                        background_x = -403
                        background_x = 1
                else:
                    main_char_x = 110
            else:
                main_char_y = 110


    # room 3, background (-403, 0):
    if (background_x >= -403 and background_x <= 0) and (background_y >=1 and background_y <= 150):
        if main_char_x <= 10 and (background_x >= -403 and background_x <= 0):
            main_char_x_change = 0
        if background_x != 0:
            background_x_change = 5
            background_x += background_x_change
            background_dis(background_x, background_y)
    """



    """
    # THIS WAS THE ORIGINAL CODE FOR THE FIRST TWO ROOMS OF BigMaze BACKGROUND
    # wall limits and door movement through first two rooms, background changes by 1 pixel depending on the room
    if background_x == -400 and background_y == 0:
        if main_char_y >= 205:
            if not(main_char_x >= 325 and main_char_x <= 410):
                main_char_y = 205
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_e:
                    background_x = -401
                else:
                    main_char_y = 205
            else:
                main_char_y = 205
        elif main_char_y <= 105:
            main_char_y = 105

        if main_char_x <= 270:
            main_char_x = 270
        elif main_char_x >= 695:
            main_char_x = 695

    if background_x == -401 and background_y == 0:
        if main_char_y >= 255 and not(main_char_x >= 105 and main_char_x <= 160):
            main_char_y = 255
        elif not(main_char_x >= 325 and main_char_x <= 410)and not(main_char_x >= 105 and main_char_x <= 160) and main_char_y <= 254:
                main_char_y = 254
        elif main_char_x >= 325 and main_char_x <= 410:
            if event.type == pygame.KEYDOWN or main_char_y <= 253:
                if event.key == pygame.K_e:
                    if main_char_y <= 205:
                        background_x = -400
                else:
                    main_char_y = 254
            else:
                main_char_y = 254
        elif main_char_x >= 105 and main_char_x <= 160:
            if main_char_y <= 254:
                main_char_y = 254
            if main_char_y >= 445:
                main_char_y = 445

        if main_char_x <= 105:
            main_char_x = 105
        elif main_char_x >= 465:
            main_char_x = 465
        if main_char_y >254 and not(main_char_x >= 165 and main_char_x <= 465):
            if main_char_x >= 160:
                main_char_x = 155
            if main_char_x <= 105:
                main_char_x = 110
    """

    """
    #trying to figure out basic wall limits, being quite honest, i remember i saved this to pull code from later, but I
    #cant remember which code it was

    if background_x == -400 and background_y == 0:
        if main_char_y >= 205:
            if not(main_char_x >= 325 and main_char_x <= 410):
                main_char_y = 205
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_e:
                    background_x = -401
                else:
                    main_char_y = 205
            else:
                main_char_y = 205
        elif main_char_y <= 105:
            main_char_y = 105

        if main_char_x <= 270:
            main_char_x = 270
        elif main_char_x >= 695:
            main_char_x = 695

    if background_x == -401 and background_y == 0:
        if main_char_y >= 255:
            if not(main_char_x >= 325 and main_char_x <= 410):
                main_char_y = 255
            elif event.type == pygame.KEYDOWN:
                if event.key == pygame.K_e:
                    background_x = -402
                else:
                    main_char_y = 255
            else:
                main_char_y = 255
    """


    # THIS WAS THE ORIGINAL BASIC MOVEMENT OF THE BACKGROUND, PULL HOW THE BACKGROUND MOVES AROUND FROM THIS ONE
    # IMPLEMENT BASIC BACKGROUND BOARDER MOVEMENT
    # moves the background if the character gets to the game display/canvas limit
    if main_char_x >= 760 and background_x >= -10000:
        main_char_x_change = 0
        background_x_change = -5
        background_x += background_x_change
        background_dis(background_x, background_y)

    if main_char_x <= 10 and background_x <= 0:
        main_char_x_change = 0
        if background_x != 0:
            background_x_change = 5
            background_x += background_x_change
            background_dis(background_x, background_y)

    if main_char_y >= 514 and background_y >= -1000:
        main_char_y_change = 0
        background_y_change = -5
        background_y += background_y_change
        background_dis(background_x, background_y)

    if main_char_y <= 98 and background_y <= 0:
        main_char_y_change = 0
        if background_y != 0:
            background_y_change = 5
            background_y += background_y_change
            background_dis(background_x, background_y)



    """
    if background_x == 0:
        if main_char_x <= 10:
            main_char_x = 10
        if main_char_x >= 560:
            main_char_x = 560
    """


    """
    background_dis(background_x, background_y)
    # a boarder around the edge of the screen that does not allow the character to move off screen
    if main_char_x <= 10:
        main_char_x = 10
    if main_char_x >= 760:
        main_char_x = 760
    if main_char_y <= 0:
        main_char_y = 0
    if main_char_y >= 514:
        main_char_y = 514
    """



    """
    # me derping around thinking about background programming movement
        if (background_x <= (certain point) and background_x >= (certain point)) and (background_y >= (certain position) and background_y <= (certain position)):
            if main_char_x == (wall position):
                main_char_x_change = 0


    """

    # displays the characters
    # character(ghost_girl_char_image, ghost_girl_x, ghost_girl_y)
    # character(fire_boy_char_image, fire_boy_x, fire_boy_y)
    # character(water_girl_char_image, water_girl_x, water_girl_y)
    # character(blu_char_image, blu_x, blu_y)
    character(main_char_image, main_char_x, main_char_y)

    # updates the display/canvas
    pygame.display.update()
    # changing the parameter number in this changes the frame rate
    clock.tick(60)
    print("main_char_x: " + str(main_char_x))
    print("main_char_y: " + str(main_char_y))

pygame.quit()
quit()

