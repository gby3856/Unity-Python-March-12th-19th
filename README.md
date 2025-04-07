# Unity-Python-March-12th-19th

March 12

using UnityEngine.SceneManagement; // required for LoadScene()

if (Input.GetMouseButtonDown(0))
{
SceneManager.LoadScene("GameScene");
}
=> Clicking the screen switches to GameScene.

In Build Settings, register scenes starting from index 0 in the Scene List.

// If the player falls out of screen, restart scene
if (transform.position.y < -10)
{
SceneManager.LoadScene("GameScene");
}
=> Accidentally typed 10 instead of -10, so the game kept restarting on launch since the player starts below y=10.

Animation:

Animator window > Parameters tab > +Trigger > assign name

Click transition arrow > Conditions tab > add trigger name

In script:
if (Input.GetMouseButtonDown(0) && this.rigid2D.linearVelocity.y == 0)
{
this.animator.SetTrigger("JumpTrigger");
this.rigid2D.AddForce(transform.up * this.jumpForce);
}
=> Works only when the player is grounded (y velocity = 0)

Changed jump key to mouse click but forgot and kept pressing spacebar -> failed

March 13

Scene Gizmo: Used to check scene view direction

Terrain: Unity's built-in terrain object

March 14

Learned about terrain brush tools

Python:
my_list = ["apple", "banana", "cherry"]
user_input = input("Enter a fruit: ")

if user_input in my_list:
print("Exists in the list")
else:
print("Not in the list")

March 15

Built ramen cooking simulator in Python with full logic and choices

Used loops, list checks, string formatting, and conditionals to simulate re-try and branching paths

March 16

Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

Vector3 worldDir = ray.direction;

bamsongi.GetComponent().Shoot(worldDir.normalized * 2000);

March 17

Baked lighting: Pre-calculated light and shadow info to texture
=> Reduces runtime cost

March 18

Raycast detects collision with stage object

Uses Mathf.RoundToInt to snap position to grid

March 19
ItemController.cs
public float dropSpeed = -0.03f;
In Update(), object falls every frame via transform.Translate()
=> Destroy if position.y < -1.0f

Collision mode = detects + reacts

Trigger mode = detects only, passes through

OnTriggerEnter(Collider other) is event-based, doesn't need to be in Update()

Unity calls it automatically when a trigger is hit
