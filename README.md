# Jeu_Du_Pong
> Jeu Multijoueur (2 players)

il s'agit d'une reprise fidèle d'un jeu fondamental : Le pong. ![Capture](https://user-images.githubusercontent.com/71081511/94304996-ced97800-ff70-11ea-93df-795dc9e2df52.PNG)


## Accès

OS X & Linux:
(Bientôt Disponible)

Windows:
(Bientôt Disponible)


## Setup Pour Le Developpement

Il eut fallu, afin de mener à bien le projet, l'import de quelque pictureBox, pour obtenir les palets de jeu ainsi que la balle.

```csharp
using System.Media;
```

On ajoute Ce using pour pouvoir, à la fin de notre code ajouter des sons par exemple pour un ajout de point, une victoire.

### Conception :
Il faut tout d'abord récupérer la localisation de notre balle (déclarer en tant que pictureBox1)
On Utilise un timer pour pousser notre PictureBow a avoir un mouvement constant.

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

Ensuite ! Nous devons gérer les rebond de cette Balle afin qu'elle ne sorte pas de l'écran.
Dans cette Application, on le gère de manière statique et non dynamique. 
(C'est-à-dire que l'on connaît les dimmensions de notre fenêtre)
Lors du rebond le score du joueur est agrémenter.
On fait la même chose de bas en HAut en gérant cette fois-ci Y.

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
On ajoute les rebonds sur palet.
Ajout d'une fonctionnalité : La balle change de couleur lors d'une touche d'un jeu.
Pour le faire on change simplement la pictureBox lors d'une touche.

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

Enfin, on code la gestion de la victoire d'un des joueurs.

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
## Historique

* 0.3.0
    * ajout : Initialisation dans le Main()
    * ajout : Du Contrôle Utilisateur.
* 0.2.0
    * ajout : Add newGame();
* 0.1.5
    * ajout : Définition Des Event de Mouvement(Variable global)
* 0.1.1
    * ajout : Définition du Serpent, de la Pomme, et des déplacement.
    * Fixation : Changement Taille de la Pomme, bug de Collision.
* 0.1.0
    * Premiere Version.
    * Changement: Renommer Event() en Test()
    * Fixation : La Vitesse Maximale Du Serpent.
    * Fixation : Ajout D'une nouvelle sphère Au serpent après Eat de la pomme. 
* 0.0.1
    * Ajout des Définitions de Event() : Re-Spawn des Pommes et Accélération du Serpent
## Future Version 

* 0.5.0
    * ajout : Ajout d'une page d'accueil (un autre Windows Forms).
* 0.4.0
    * ajout : Une Base De Donnée qui gère Les scores de chaque joueur.
    avec un système classement.

## Meta

Bourdon Maxime – Mbourdon.pro@gmail.com

[https://github.com/Mbourdon95/github-link](https://github.com/Mbourdon95/)
