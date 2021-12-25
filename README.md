# Unity Plane Programming
 
Project repository for the Unity Junior Programmer Pathway: Challenge 1 - Plane Programming

I will need to utilize the skill I have learned in my driving simulation prototype to fly a plane around arial obstacles. 
I will need:
 - User input for: Up & down = Plane's pitch up and down
 - Make the camera follow alongside the plane

 Challenge Assets: https://connect-prd-cdn.unity.com/20210506/913574fa-af65-4d95-abe8-d90282b27a83/Challenge%201%20-%20Starter%20Files.zip

 Source: https://learn.unity.com/tutorial/challenge-1-steer-a-plane-through-obstacles-in-the-sky?uv=2020.3&pathwayId=5f7e17e1edbc2a5ec21a20af&missionId=5f71fe63edbc2a00200e9de0&projectId=5caccdfbedbc2a3cef0efe63#

 Bugs to fix:

 1. The plane is going backward
 Resolution: 
 Change Vector3.back -> Vector3.forward in transform.Translate parameters from script PlayerControllerX.cs in method FixedUpdate()

 2. The plane is going too fast
 Resolution:
 Include Time.deltaTime in transform.Translate calculation from script PlayerControllerX.cs in method FixedUpdate()

 3. The plane is tilting automatically
 Resolution: 
 Include verticalInput variable in transform.Rotate calculation from script PlayerControllerX.cs in method FixedUpdate()
 Also, in RigidBody Contraints, freeze the X rotation

 4. The camera is in front of the plane
 Resolution:
 Find the camera position, where the camera is beside the plane
 Apply a rotation to the camera -90 degrees in the Y

 5. The camera is not following the plane
 Resolution:
 Select the MainCamera. Then in the inspector, assign the Player as the Plane variable from script FollowPlayerX.
 Set the camera offset in the FollowPlayerX script.

 6. Bonus: The plane's propeller does not spin
 Resolution:
 Create a new script (Rotation.cs) to handle rotation.
 Handle rotation in a LateUpdate() event. Create two serialized private variables rotObj and rotationSpeed. Variables being Transform and float respectively. Apply the following Rotation to rotObj:
 Vector3.forward, rotationSpeed * Time.deltaTime
 Since rotationSpeed is serialized, set the rotation speed in the inspector.
 Add Rotation.cs to the Propeller game object. Assign Propeller to the serialized rotObj.

 7. Plane slowly clips through walls
 Resolution:
 Adjust value from 10 -> 100 in project settings

