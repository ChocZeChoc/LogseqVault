- #Animation
	- #2DSprite
	- #Kenimatic
		- #IK
		- #FK
	- #CharacterMovement
	  collapsed:: true
		- ```C#
		  using System.Collections;
		  using System.Collections.Generic;
		  using UnityEngine;
		  using UnityEngine.InputSystem; // Adding Unity's Input system, because we are using it to control the animation via the keysystem
		  
		  public class playerMovement : MonoBehaviour
		  {
		  
		      private Vector2 movement; // Im instantiating a Vector2 movement variable that stores the direction of movement, that will be used by the onMovements function
		      private Rigidbody2D myBody; // This variables stores the Rigidbody component
		      private Animator myAnimator; // This variable stores the Animator component
		  
		      [SerializeField] private int speed = 5; // Here im making a serialized private int variable, that stores the current speed of the object
		  
		      private void Awake() // Awake is called only once when the script starts
		      {
		          myBody = GetComponent<Rigidbody2D>(); //Im setting the myBody variable to the Rigidbody component of the current object
		          myAnimator = GetComponent<Animator>(); //Im setting the myAnimator variable to the Animator component of the current object
		      }
		  
		      private void OnMovement(InputValue value) // Im making a function that keeps an eye on our Inputs system's values
		      {
		          movement = value.Get<Vector2>(); //This gets the direction of input and sets the movement variable to that.
		  
		          if (movement.x != 0 || movement.y != 0) //If one of the components of the vector arent = 0 then you know it is moving
		          {
		              myAnimator.SetFloat("x", movement.x); //If it is moving then we are setting the x float equal to the x component of our movement variable
		              myAnimator.SetFloat("y", movement.y); //If it is moving then we are setting the y float equal to the y component of our movement variable
		  
		              myAnimator.SetBool("isWalking", true); // If it is moving then set the isWalking to true 
		          }
		          else
		          {
		              myAnimator.SetBool("isWalking", false); // Else, If it is not moving then set the isWalking to false
		          }
		      }
		  
		      private void FixedUpdate() // Im using FixedUpdate as it is more effecient than Update when it comes to things such as movement, as it isnt get called every frame
		      {
		          myBody.velocity = movement * speed; // Im setting the velocity of the current rigidbody to the movement Vector2 multiplied by the speed
		  
		      }
		    
		  }
		  ```
		-
	- #MonoBehaviour.Update()
		-
	-