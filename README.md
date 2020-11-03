# Pong_Game
> Multiplayer game (2 players)

it is a faithful revival of a fundamental game: Pong. ! [Capture](https://user-images.githubusercontent.com/71081511/94304996-ced97800-ff70-11ea-93df-795dc9e2df52.PNG)


## Access

OS X & Linux:
(Coming soon)

Windows:
(Coming soon)


## Setup For Development

In order to complete the project, it would have been necessary to import some pictureBox, to obtain the pucks as well as the ball.

```csharp
using System.Media;
```

We add Ce using to be able, at the end of our code add sounds for example for a point addition, a victory.

### Conception :
Il faut tout d'abord récupérer la localisation de notre balle (déclarer en tant que pictureBox1)
On Utilise un timer pour pousser notre PictureBox a avoir un mouvement constant.

```csharp
 private void timer1_Tick(object sender, EventArgs e)
        {
            // Ici on fait déplacer automatique l'objet vers la droite. 
            // Le but étant de faire rebondir la balle sur les parois
            // du Group Box, afin d'avoir une balle autonome.

            int x = pictureBox1.Location.X;
            int y = pictureBox1.Location.Y;
        }
```

Then! We have to manage the rebound of this Ball so that it does not leave the screen.
In this Application, it is managed statically and not dynamically.
(That is, we know the dimensions of our window)
When bouncing the player’s score is enhanced.
We’re doing the same thing down in HAut by managing this time Y.

```csharp
            if (x > 1263)
            {
                sens_balle_x = -20;
                int score = Convert.ToInt32(Score_Joueur1.Text);
                Score_Joueur1.Text = Convert.ToString(score + 1);
                
            }
            // rebond sur le bord Verticale Gauche.
            if (x < 0)
            {
                sens_balle_x = 20;
                int score = Convert.ToInt32(Score_Joueur2.Text);
                Score_Joueur2.Text = Convert.ToString(score + 1);
            }
```
We add the puck bounces.
Adding a feature: The ball changes color with a touch of a game.
To do this you simply change the pictureBox during a touch.

```csharp
            if(pictureBox1.Bounds.IntersectsWith(Joueur2.Bounds))
            {
                sens_balle_x = - 20;
                pictureBox1.Image = Properties.Resources.ball_magenta;
            }
            if (pictureBox1.Bounds.IntersectsWith(Joueur1.Bounds))
            {
                sens_balle_x = 20;
                pictureBox1.Image = Properties.Resources.ball_green;
            }
```

Finally, we code the management of the victory of one of the players.

```csharp

            if (Score_Joueur2.Text == "10")
            {
                Score_Joueur2.Location = new Point(790, 250);
                Score_Joueur1.Location = new Point(485, 250);
                Score_Joueur1.ForeColor = System.Drawing.Color.White;
                button1.Visible = true;
                button2.Visible = true;
                label2.Visible = true;
                timer1.Enabled = false;


            }
            if(Score_Joueur1.Text == "10")
            {
                Score_Joueur2.Location = new Point(750, 250);
                Score_Joueur1.Location = new Point(465, 250);
                Score_Joueur2.ForeColor = System.Drawing.Color.White;
                button1.Visible = true;
                button2.Visible = true;
                label2.Visible = true;
                timer1.Enabled = false;
            }
```

![Capture1](https://user-images.githubusercontent.com/71081511/94305002-d0a33b80-ff70-11ea-8353-457d9e2121ef.PNG)
## History

* 0.2.0
* Second Version
* Fixation: Unable to send Two Keys to Windows Forms System
To counter this, the left puck can only move when the ball is in its court.
Possibility of using libraries like DirectX also to counter this problem.
* 0.1.5
* addition: Audio to enhance the game fun.
* 0.1.1
* addition: EndGame and RestartGame management and Score label management.
* Fixation: Management of Ball Collisions on Plaets and Walls
* 0.1.0
* First Public Release.
* Change: Increase the speed of the ball per tick from 10 to 20.
* Adding palets and formatting the screen
* 0.0.1
* Added methods for changing ball colors start a click event
## Future Version 

* 0.4.0
    * added: Added a home page (another Windows Forms).
* 0.3.0
    * addition: A Database that manages each player’s scores.
    with a filing system.

## Meta

Bourdon Maxime – Mbourdon.pro@gmail.com

[https://github.com/Mbourdon95/github-link](https://github.com/Mbourdon95/)
