# Houdini Strawberry Plant Tool
### Design Doc
#### Introduction

I want to take this project as an opportunity to make artist-facing tools in Houdini - adjusting parameters to make an asset or a part of a scene appear naturalistic yet easily controllable without the artist having to make a model from scratch and duplicating and varying the object multiple times. Thus, I choose to make procedural strawberry plants in Houdini that allow artists to tweak parameters like strawberry size, ratio of strawberry to flowering to leaves, amount of growth, etc.


#### Goal

The goal of this project is to create a way to procedurally generate strawberry plants with artist-friendly tweakable parameters within Houdini. Perhaps there is a scene that takes place in a garden store, or a scene that takes place in a field of strawberries, and where the character is peering between the bushes - then a 3D artist might need a way to place many strawberry plants that all look different in terms of the placement of leaves, number of flowers and strawberries, yet all strawberry plants are in the same stage of ripeness in the early summer - the perfect time for strawberry picking. Being able to reduce the number of ways to create a strawberry plant to its bare essential attributes for production, such as amount of growth, number of strawberries, etc, will allow artists to easily generate lots of strawberry plants as needed, as teh game or film sees fit.

#### Inspiration/reference:
- Here are some reference photos:
![A strawberry plant with fruit](https://github.com/user-attachments/assets/9d17e283-43bd-40cb-b8db-8c48b5fa30c2)
![s-l1600](https://github.com/user-attachments/assets/7f9ba88f-1034-4659-b1fb-9bfa3ea11673)
![8338a51a986d27bfb4457e28b5d3c6ac](https://github.com/user-attachments/assets/f5ffcbcc-6892-40de-8b2b-f20649cf48c4)


- Here are some reeadings I came across that break down the structure of strawberry plants:
  - [Strawberry Plant Structure and Growth Habit ](http://www.hort.cornell.edu/expo/proceedings/2012/Berries/Berry%20Plant%20Structure%20Poling.pdf)
  - [How Strawberry Plants Grow](https://extension.umn.edu/strawberry-farming/how-strawberry-plants-grow)

#### Specification:
- The user can generate a strawberry plant with the following parameters:
    - How much/how little growth of plant (small, sparse plant, or large, bushy plant)
    - Number of strawberries in the plant
    - Number of leaf nodes
    - Number of flowers
    - Ripeness of strawberries scale
  
#### Techniques:
- What are the main technical/algorithmic tools you’ll be using? Give an overview, citing specific papers/articles.
- We will use L systems to create the stem structure of the strawberries
- Follow this tutorial to make the strawberry leaves : https://www.youtube.com/watch?v=s5RwLhmLzHM
  - The strawberry leaves will also contain adjustable parameters for leaf size/age
- Use four models of strawberries in various stages of their lives temporarily, then procedurally generate strawberries later on
  - Tutorial to potentially follow : https://www.youtube.com/watch?v=o2lqjgt4RwU
- Procedurally generate flowers in Houdini as well, following a similar workflow as the Jellyfish lab

#### Design:
<img width="1380" height="672" alt="Screenshot 2025-11-07 at 10 03 11 PM" src="https://github.com/user-attachments/assets/1faf5e89-1ccc-48e9-834a-3145365c2cc6" />

(Please imagine an actual procedurally generated strawberry is in its place)

#### Timeline:
The plan
- 11/5 - 11/12:
   - Create a workable L-system node for the stems, with dummy leaves and strawberry models that can populate on the tip of the stems by adjusting the UI parameters
   - Create the UI
- 11/12 - 11/24:
   - Create the leaves, the strawberries, and the flowers procedurally, and make sure they attach and orient correctly onto the plant. Make sure that the amount of strawberries, leaves, and flowers are easily adjustable 
- 11/26 - 12/1
   - Finishing touches - anything that needs to be fixed, make a demo-reel and also applying materials and lighting to a custom scene with the strawberries, last-minute UI changes

 ### Milestone 1
 I have created a couple of stems for the strawberry which includes a subnetwork that takes a geometry as input to put at the very top. The geometry is oriented with respect to the normal at the very end of the stem, and points along the trajectory of itself:
<img width="1080" height="730" alt="Screenshot 2025-11-12 at 9 13 47 PM" src="https://github.com/user-attachments/assets/93cc0ea4-de7c-4d27-97c3-e73859a4fcba" />

Furthermore, I added some sliders for each branch that allows the user to decide the angle at which the stem is bending and in what direction. These two attributes I believe will eb essential to randomizing stem generations for the strawberry plant. Furthermore, I also created a sub network that allows the user to generate a stem with more stems branching off of it following a noise function. However, I still have to work on orienting the normals correctly for which the sub-stems branches off of the main branch. I'm also considerign writing an l-system for this to make a shape easier to generate for the stem, although the main issue is querying the end-points of the L system to attach strawberries, leaves, and whatever other geometry there are since I wasn't able to search up a way to query these points.

<img width="1000" height="738" alt="Screenshot 2025-11-12 at 9 14 06 PM" src="https://github.com/user-attachments/assets/d0a4fa4a-0d43-4684-8ae9-d98ca521dce1" />

### Milestone 2
The progress on my goals:
- I have created strawberries that are easily customizable in shape and size:
<img height="300" alt="Screenshot 2025-11-24 at 11 59 39 PM" src="https://github.com/user-attachments/assets/9832e84a-e1f5-42cf-937c-823d8e9da806" />
<img height="300" alt="Screenshot 2025-11-24 at 11 59 50 PM" src="https://github.com/user-attachments/assets/fc9ee0a1-de55-40c5-a255-03a114257853" />
<img  height="300" alt="Screenshot 2025-11-24 at 11 59 54 PM" src="https://github.com/user-attachments/assets/f36a417a-8ed1-4301-8d55-1880d55a547d" />

  
- And created strawberry flowers where the user can toggle if a flower is fully bloomed and if it is only in its bud stage
<img height="400" alt="Screenshot 2025-11-24 at 11 59 14 PM" src="https://github.com/user-attachments/assets/0915615a-e6be-4846-83a6-447900c7745f" />
<img height="400" alt="Screenshot 2025-11-24 at 11 59 21 PM" src="https://github.com/user-attachments/assets/f0cd8089-3547-4eb3-bb94-e424d3b15f6b" />
<img height="400" alt="Screenshot 2025-11-24 at 11 59 26 PM" src="https://github.com/user-attachments/assets/75e12d23-a8dd-40a7-a7c6-1e192d101203" />

I still need to create the leaves of the strawberry (at this point, this should be a pretty straightforward task from practicing making flowers and strawberries), adn of course, the stems.

In terms of cutting out certain features of my project, I plan on focusing less heavily on making the strawberry plants botanically realistic and focus more on getting the stems done and to finish attaching the leaves via L-systems. I also plan on only having a "bushiness" slider to vary up the strawberry plant, since the goal of this project is to be able to generate many strawberry plants at once, and the "bushiness" of a strawberry plant is the main macroscopic feature needed for strawberry plant variation.

### Final Submission

The Houdini files can be downloaded here:
https://drive.google.com/drive/folders/10e0fsh1068Qv1wMEVW3PbDMGlbQIp9OO?usp=sharing

#### The Strawberry Plant
Here are the final results of the generated strawberry plants:
<img height="400" alt="0_553" src="https://github.com/user-attachments/assets/dd9f8702-9600-46c6-bb5c-d2f8bc371d99" />
<img height="400" alt="1" src="https://github.com/user-attachments/assets/23fe9015-d16a-44c3-9d4d-10664b7abc96" />
<img  height="400" alt="0_767" src="https://github.com/user-attachments/assets/0f333059-16c3-48d0-abdb-20f9f265d223" />
<img height="400" alt="0_263" src="https://github.com/user-attachments/assets/7db93b65-ae0a-4e2e-8d54-d1b00d3c7c6c" />

In order to vary each strawberry plant, there is a "bountifulness" slider (0 yielding no strawberry plant and 1 yielding a very bushy strawberry plant), and a randomize slider which feeds a integer seed into the strawberry generator to create strawberries varying in shape. From first image to last, the following "bountifulness" parameters were used: 0.533, 1, 0.767, 0.263

In order to make this strawberry plant, I modeled the leaves, the flowers, and the strawberries procedurally, giving room for me to vary up the shape and size of each part. I then exported out 5 geometry instances of flowers and strawberries to use for the strawberry generator. There are 10 geometry instances for the leaves.

#### The Strawberry
The strawberry's shape was created by following this tutorial: https://www.youtube.com/watch?v=o2lqjgt4RwU&t=1733s
<img height="500" alt="strawb00004" src="https://github.com/user-attachments/assets/3699b558-4ab0-4e8a-af1e-87c8120e5055" />
<img height="500" alt="strawb00003" src="https://github.com/user-attachments/assets/a41c60ba-2a43-4895-8547-6770e9e3b533" />
<img height="500" alt="strawb00002" src="https://github.com/user-attachments/assets/65185d6c-7052-41b7-808e-9a7a03d7df53" />
<img height="500" alt="strawb00001" src="https://github.com/user-attachments/assets/757e8718-5b39-408f-bbb2-8329ab00da55" />

The shape of the strawberry can be varied using a manually created slider, which is connected to a "mountain" node that adds noise to the shape of the strawberry.

#### The Flowers
The flower was created by taking inspiration from this playlist: https://www.youtube.com/playlist?list=PLOGJpcoBCf0MhmgDJKTY9SMJJDWrhYLIu

https://github.com/user-attachments/assets/71cdb06c-aefc-48d3-88bd-764dfeea09fe

We create a rig for each petal and leaf belonging to the flower in order to get the petal to open and uncurl.

#### The Leaves
The leaves were modeled with L systems.

