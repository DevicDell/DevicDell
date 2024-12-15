When Green Flag Clicked
    Set score to 0
    Repeat Forever
        Move apple down by 10
        If apple touches basket
            Change score by 1
            Move apple to a random position at top
        End
        If apple is below the screen
            Move apple to a random position at top
        End
    End

using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float speed = 5f;

    // Update is called once per frame
    void Update()
    {
        float horizontalInput = Input.GetAxis("Horizontal");
        transform.Translate(Vector2.right * horizontalInput * speed * Time.deltaTime);
    }
}


extends KinematicBody2D

# Declare variables for movement speed and direction
var speed = 200
var velocity = Vector2()

# Called every frame
func _process(delta):
    velocity = Vector2() # Reset the velocity to zero
    
    # Movement input
    if Input.is_action_pressed("ui_right"):
        velocity.x += speed
    if Input.is_action_pressed("ui_left"):
        velocity.x -= speed
    
    # Move the player
    move_and_slide(velocity)

import pygame

# Initialize Pygame
pygame.init()

# Set up the display
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption('Basic Game')

# Define the colors
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# Set up the player
player_size = 50
player_x = 375
player_y = 275
player_speed = 5

# Game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    
    # Key press handling for movement
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        player_x -= player_speed
    if keys[pygame.K_RIGHT]:
        player_x += player_speed
    if keys[pygame.K_UP]:
        player_y -= player_speed
    if keys[pygame.K_DOWN]:
        player_y += player_speed
    
    # Fill the screen with white and draw the player (red square)
    screen.fill(WHITE)
    pygame.draw.rect(screen, RED, (player_x, player_y, player_size, player_size))

    # Update the display
    pygame.display.flip()

    # Set the frame rate
    pygame.time.Clock().tick(60)

# Quit Pygame
pygame.quit()
