🐭 Rat in a Maze – Wall Avoidance Robot

Have you ever watched a mouse run through a maze, pausing at every corner to decide where to go next? That’s exactly what this project is about — except my “rat” is a robot.

This is a maze-solving bot that can navigate a pathway while avoiding walls. It doesn’t have eyes, but it does have sensors that help it “see” its surroundings and make decisions in real time. It’s a blend of robotics, electronics, and a bit of algorithmic thinking.

⸻

💡 The Idea Behind It

The main challenge I wanted to tackle was autonomous navigation — how to make a robot move through a maze without human control and without hitting obstacles.

The solution? Give the robot just enough “awareness” to decide on its own:
	•	If the path is open, keep moving forward.
	•	If there’s an obstacle, figure out a way around it.
	•	If it’s stuck, try a different path.

It’s not a supercomputer, but it’s smart enough to make these small decisions instantly while it’s moving.

⸻

🛠 How I Built It

The Brain

At the heart of the robot is an Arduino Uno. It’s simple, reliable, and perfect for quick prototyping. The Arduino takes all the sensor readings, processes them, and tells the motors what to do next.

The Senses

For wall detection, I used ultrasonic sensors. These sensors send out sound waves, measure how long it takes for them to bounce back, and calculate how far away an object is. This is how the robot “knows” if there’s a wall ahead, to the left, or to the right.

I also experimented with infrared sensors to detect the edges of the pathway or specific markings, though these are optional depending on the maze design.

The Muscles

Two DC geared motors give the robot movement. They’re connected to an L298N motor driver, which allows the Arduino to control their speed and direction. A small caster wheel at the back keeps it stable.

The Power

The whole system is powered by a Li-ion battery pack, which keeps it lightweight and mobile.

⸻

🧠 The Navigation Logic

The robot follows a wall-following strategy (I chose right-hand rule, but left-hand would work too). This means it tries to keep one wall on its right side at all times.

Here’s the basic decision process:


Loop:
    Check distance in front
    If front is clear:
        Move forward
    Else:
        Check right side
        If right is clear:
            Turn right
        Else:
            Check left side
            If left is clear:
                Turn left
            Else:
                Reverse and turn around
This simple logic is surprisingly effective in many maze layouts. The robot doesn’t need to map the maze — it just reacts based on what it senses.

⸻

🚀 Running the Robot
	1.	Build the chassis and attach motors, wheels, and caster wheel.
	2.	Mount the sensors so they face forward and to the sides.
	3.	Wire everything to the Arduino and motor driver.
	4.	Upload the code from Arduino IDE.
	5.	Place the robot at the maze entrance, power it on, and watch it go.

⸻

📈 Future Improvements

While the current design works well, there’s a lot of room for upgrades:
	•	Adding mapping algorithms like BFS, DFS, or Dijkstra’s to find the shortest path.
	•	Using a camera module and computer vision for more advanced navigation.
	•	Making the bot self-learning with reinforcement learning.
	•	Adding Bluetooth or Wi-Fi control for debugging or manual override.

⸻

🎯 Why I Built It

I wanted something more exciting than a simple line follower — something that could deal with unpredictable paths and make its own choices. This project taught me:
	•	How to work with sensors and motor control in real time.
	•	The importance of decision-making algorithms in robotics.
	•	How to combine hardware and software to create something autonomous.

It’s not perfect, but watching the robot confidently roll through a maze without touching the walls is incredibly satisfying — it really feels like it has a tiny bit of life.
