<!-- [![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-f059dc9a6f8d3a56e377f745f24479a46679e63a5d9fe6f495e02850cd0d8118.svg)](https://classroom.github.com/online_ide?assignment_repo_id=445323&assignment_repo_type=GroupAssignmentRepo) -->

<!-- <img src="https://images.unsplash.com/photo-1501776192086-602832fae6e6?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80"> -->

<img src="https://cdn.freebiesupply.com/logos/large/2x/the-university-of-melbourne-logo-svg-vector.svg" width=20% align=centre> 

<img src="/Gifs/mainScene.png">



# COMP30019 Group Project 2 Team 06
This repository is created for [University of Melbourne](https://www.unimelb.edu.au)
 [COMP30019 Graphics and Interaction Semester 2 2021](https://handbook.unimelb.edu.au/search) 

**Unity 3D Game Development** 

---

## Code Access Link and Master Branches
 |Master Branch | Download  |
| ---- | ---- |
 |https://bit.ly/3nnP5AX | https://bit.ly/3EteNej |


---

<img src="https://icons-for-free.com/iconfiles/png/512/notion-1324440204874385945.png" width=5% align=left>View our Project Management notes via. [notion](https://www.notion.so/COMP30019-3D-Game-5321bede7e8c41ddb5d76160b8e4b7b4).


---

## Table of Content
<!-- [<img src="https://cdn.freebiesupply.com/logos/large/2x/the-university-of-melbourne-logo-svg-vector.svg" width=20% align=left> -->
- [COMP30019 Group 2 Project Team 06](#comp30019-group-2-project-team-06)
- [Team Members](#team-members)
- [Introduction](#introduction)
- [Game Synopsis](#game-synopsis)
- [Game Instructions](#game-instructions)
- [Game Design](#game-design)
- [Graphics Render Pipeline And Camera Motion](#graphics-render-pipeline-and-camera-motion)
- [Procedural Generation Technique](#procedural-generation-technique)
- [Custom Shaders](#custom-shaders)
- [Particle System](#particle-system)
- [Observational and Querying Methods](#observational-and-querying-methods)
- [References](#references)
- [Task Checklist](#task-checklist)
---

## Team Members

| Name | Email | Key Contributions
| :---- | :---- | :---- | 
| Dian Lin | dilin@student.unimelb.edu.au | 
| Hongji Huang | hohuang@student.unimelb.edu.au |
| Wei Zhao | weizhao1@student.unimelb.edu.au |
| Zhejun Lyu | zhejun@student.unimelb.edu.au |

## Introduction
*Legend of Sword* is an open-world third-person action role-playing game (ARPG) developed by Team 06 for Graphics and Interactions, Semester 2 of 2021. This game involves a protagonist on an exciting adventure of defeating a plethora of enemies. All shaders in the game are implemented by Team 06 in HLSL / Shader graph / URP in-built shader, no external code has been used in implementation of shaders. 

## Game Synopsis 

Summoned into the alternate world of Quadrarena for his extraordinary bravery and outstanding battle skills, Aung the Knight carries with him the honourable yet vicious duty of conquering the four beasts that haunts the four arenas. Upon defeating the Fiery Fiend, Glacier Giant, Tree Titan and Stone Savage, he must enter the Portal of No-Return and put his life on the line to end the nightmare of Quadrarena by fighting the final Boss - or be engulfed by its darkness. Every step he takes and every move he makes must be the fruit of careful consideration, one mistake and the peoples of Quadrarena will be doomed under the control of the beasts forever. Are you up to help Aung in his quest and shed the light of eternal peace on Quadrarena?


## Game Instructions
### Download & Set-Up
- Download -> Unzip -> Run the .exe file  

- **Play in Unity Editor**  
  Switch to `MenuScene` and click the play button, do not enter the game from `InitialScene` or `MainScene`, otherwise the game would not run properly! Don't forget to unmute the music and we hope you enjoy the game : - )

### Gameplay 
- Keyboard Controls
  - **WASD**: Direction Controls
  - **Q**: Freeze opponent (skill gained by defeating the Glacier Giant) 
  - **E**: Burn area of effect (skill gained by defeating the Fiery Fiend)
  - **R**: Reflect damage with Blademail (skill gained by defeating the Stone Savage)
  - **T**: Health regeneration (skill gained by defeating the Tree Titan)
  - **F**: Enter Portal
  - **K**: Save Game Data 
  - **L**: Load Game Data
  - **Escape**: Return to Main Menu, automatically saves game data
  - **Tab**: Open/Close Backpack
  - **Space**: Jump
  - **Shift**: 
    - Hold to run
    - Press to dodge  
  - **Number 1-5**: Use item of this index in the backpack

- Mouse Controls
  - **Hovering**: Camera Control
  - **Left-Click**: Attack
  - When the backpack is open:
      - **Left-Click**: Drag an item to Character Stats to equip
      - **Double Left-click**: Use an item

## Game Design
The overall game structure of Elemental Arenas guarded by Beasts stemmed from our initial idea of designing thematic enemies that has persona, appearance and form of attack all highly aligned with their themes. We subquently decided to create biomes that also extend from each theme. Much of our game design is improved based on suggestions obtained from the evaluation phase of our game development, where many observed/queried players found the enemies difficult to defeat. We put a lot of thought into how we can grant the players with more power while still retaining the challenging part of a conquest-driven game of obtaining more powers, therefore we implemented a major design changes based on the feedback, which players observed/queried at later stages of game development found to be highlights of the game: we decided to gift the player with the corresponding form of attack possessed by each Elemental Beast upon the player defeating the beast, essentially as a transfer of power that symbolises the successful conquest of that Elemental Arena. After receiving these powers, players can defeat other beasts and enemies more easily.

Additional Details of Character and Object design highlights are as follows:

- **Protagonist**: Our protagonist is a knight 
- **Enemies**:
  - **Low-Level Enemies**: 
   - <img src="/Gifs/Slime.png" width="100"/>
   - **Slimes**: One of the most basic enemies in the game, and of course one of the most budget ones becaue it is a free and common asset on the asset store. It has two basic attack animation which are pridictable on their own and its appearance is not intimidating, therefore, it fits our expection of a early game enemy perfectly.

   - <img src="/Gifs/Turtle.png" width="100"/>
   - **Turtles**: Similar to Slimes, due to the fact that they are included in the same free asset pack and its animation and appearance are all newbie-friendly as well, we design it as one of the early game enemies. 
   - <img src="/Gifs/Grunt.png" width="100"/>
   - **Grunts**: Grunts are relatively strong enemies but not as strong as the elite ones and the bosses. It has more complicated attack and movement abilities but the player can still manage to beat it if the player can properlyu utilise the roll dodge. This is a great enemy for teaching player about the core mechanics of the combat system in the game.
   - **Elite Enemies**: <img src="/Gifs/Archer.png" width="100"/><img src="/Gifs/Cannon.png" width="100"/><img src="/Gifs/Cannon1.png" width="100"/><img src="/Gifs/Knight.png" width="100"/><img src="/Gifs/Knight1.png" width="100"/><img src="/Gifs/Mage.png" width="100"/><img src="/Gifs/Mage1.png" width="100"/><img src="/Gifs/Soldier.png" width="100"/><img src="/Gifs/Soldier1.png" width="100"/>There many more difficult enemies (with better rewards of course) in the world, including Archer, Knight, Mage, Soldier, etc. And they all have advanced versions of them (with scarlet skins!). These dangerous enemies are often guarding for powerful weapons or items. Make sure your character is strong enough before challenging them!

  - **High-Level Bosses (Elemental Beasts)**:
    - **Fiery Fiend**: <img src="/Gifs/Fire.png" width="100"/>The volcano has been simmering for as long as the Fiery Fiend has been alive, an angry Beast that thrives off heaven's charcoal with its rumbling anger so loud that anyone nearing the Fire Arena immediately flees for their lives on horseback. Fuelled by the rolling rage of Fire, the Fiery Fiend is in a constant state of fury and ready to burn anything or anyone that dares to come close. 

    - **Glacier Giant**: <img src="/Gifs/Ice.png" width="100"/>Soulless. Colorless. A world of white births and nurtures the Glacier Giant. The seas are frozen mid-wave, the rains are frozen mid-drop, only a handful of greenery is allowed the chance of life by the Glacier Giant. Powered by the ever-present cold that commoners see as their nemesis, the Glacier Giant unhesitantly freezes any earthly matter that enters its biome. 

    - **Tree Titan**: <img src="/Gifs/Tree.png" width="100"/>Superficially harmless, even a calming bliss on the surface, is the forest biome ruled by the Tree Titan. The ever-giving nature of this biome gifted the Tree Titan with incredible vitality and endless lifecycles. Do not be fooled by the disguise of Tree Titan and the forest biome, the player must defeat it for the valuable power-up of Health Regeneration.

    - **Stone Savage**: <img src="/Gifs/Stone.png" width="100"/>Stone biome speaks of permanence, of the tombstone of countless souls that died in their hopes of defeating the Stone Savage. Protected by an unbreakable layer of stones, the Savage Beast is seemingly impossible to defeat with its power of reflecting the damage back to its opponents. Only the brave has a chance against such a mighty being.

- **Supplies**: There are consumables for temporal restoration of the character status, such as health packs and energy drinks. There are also consumables that can permenantly improve the character status, such as essence that drops from the defeated enemies. The more difficult an enemy is, the better the consubales it would probably drop after it is defeat. We design these items as minor objectives and rewards for the player to explore the world. 

- **Weapons**:
  - **Weapon Features**: For a myriad of game experiences, we imeplemented a wide range of weapon options each with distinct features in the dimensions of attacking form, attack range, cool-down time, critical hit and damage levels etc.

  - **Long-Distance Weapon**: We want the player to be able to easily perform long-distance attacks like an archer, so we added Long-Distance Weapons that can fire projectiles. Projectiles will track an enemy within its attack range and apply relevant damage to the enemy. If the enemy is located outside of the attack range, the projectiles will shoot in the direction at which it is fired towards.   

- **Quick Access Bar**: We understand that opening backpack -> retrieving supplies -> using supplies is quite a long process during fast-paced combats against enemies, therefore we designed a Quick Access Bar that stores supplies and can be accessed with number keys 1-5 for the convenience of players at crucial combatting moments throughout the game.


## Graphics Render Pipeline And Camera Motion
### Graphics Render pipelines
- **Overview**

  According to the Unity3D manual, there are generally three types of render pipelines for us to choose from, built-in render pipeline, high definition render pipeline (HDRP), and   universal render pipeline (URP). Specifically, both HDRP and URP are scriptable render pipelines (SRP).
- **SRP**  

  According to the Unity3D manual, there are generally three types of render pipelines to choose from, built-in render pipeline, high definition render pipeline (HDRP), and universal render pipeline (URP). Specifically, both HDRP and URP are scriptable render pipelines (SRP).
- **HDRP**  

  According to the Unity3D manual, there are generally three types of render pipelines to choose from, built-in render pipeline, high definition render pipeline (HDRP), and universal render pipeline (URP). Specifically, both HDRP and URP are scriptable render pipelines (SRP).
- **URP**  

  It is another template render pipeline provided by Unity, its former version is known as lightweight render pipeline (LWRP) and LWRP formally changed its name to URP in Unity version 2019.3. URP is built for projects developed for multiple platforms which covers a wide range of devices, such as smartphones and game consoles or computers that has medium to low performance in graphics processing. Generally, URP outplays the built-in render pipeline in most of the aspects of graphics rendering and is highly customizable. It supports rendering with many different art styles and is becoming the new 'default render pipeline', taking the place of the built-in render pipeline.
- **Using URP over others**  

  We are not using the built-in render pipeline because 1) it is hardly customizable, due to reasons in the aforementioned explanation; 2) built-in render pipeline's performance and effect of rendering are generally worse than SRP, especially in lighting effects, where built-in render pipeline has multiple passes which increase as there are more dynamic lightings whilst for example URP handles dynamic lighting with a single pass and therefore can achieve better performance and results ; 3) Some of the visually-appealing versions of our art assets, such as prefabs of the characters and environmental objects only support URP/HDRP render pipeline or perform better with URP/HDRP compared to the built-in render pipeline.  

    URP and HDRP are not compatible with each other, so, we had to choose one render pipeline from them throughout the project development. One of the major reasons that we use URP is that the art style that we choose for our game is low poly instead of the more realistic ones, so, HDRP is simply not needed. Though HDRP can achieve cinema-level lighting effects rendering with abundant functionalities such as real-time global illumination, which can simulate the reflection, volume, particle piercing, and tracing of light, these advanced functionalities of HDRP are highly demanding for the developers' hardware, which is too over budget for us and the art style that we were aiming for only requires much more basic lighting effects. Besides, the shader we are using are either built-in or free from external resources, therefore, the high-end shader effects that HDRP supports are also irrelevant for this game project.  

    Moreover, URP can help us better in evaluation process as URP supports a wide range of platforms to export builds, whereas projects with HDRP can only export builds to high-end platforms, and many of our test participants only have access to normal PC or Mac.  

    Overall, URP was the simplest option for us that can help us to achieve all the rendering effects that we were aiming for.  

### Camera Motion

Camera motion is cotrolled in a single `C#` script. There are two key variables that control the camera motion, one is a `Transform` named `cameraTransform` represents the transform of the camera, another one is a `Vector3` named `offset` which represents the position of the transform of the controlled character. A function `CameraControl()` is being constantly called in `LateUpdate()` except for the situation when the inventory is open. In `Start()`, `offset` and the original postion of the camera is recorded. Within the function `CameraControl()`, the postion of the camera is first added with the difference between the position of an empty game object and the position of the character (`offset`). Next, the value of the `offset` is assigned with the position of the former empty game obejct. Then, the rotation of the camera is calculated by multiplying mouse axis coordinates and the configurable rotation speeds in x axis and y axis. Also, the rotation of the camera on y axix is limited in a range to avoid disorientation due to excessive movement of the mouse. It is also worth mentioning that `Physics.Linecast` is used to ease the problem that camera directly goes through the terrain and captured the unrendered side of the terrain when parts of the terrain is too uneven or complex.

## Procedural Generation Technique

Procedural generation is a method of creating data through algorithms rather than manually,
Our team used procedural generation in many places in the game.

- Initial Scene (Tutorial Mission)
  - random color of grass

  - terrain generated by script using perlin noise map

- Drops / Loot Items
  - Defeating a Enemy the Enemy will randomly drop a item.
  - In the center of the map, in the village, there will be a rain with some loots every ten minutes.

**Implementation details:**

click the link to checkout the code in github.com

1) **/Assets/Scripts/Scene/RandomGrassColor.cs**
 For the random color of grass, we use [script](https://github.com/Graphics-and-Interaction-COMP30019-2021/project2-project2_group_06/blob/master/COMP30019%203D%20Game/Assets/Scripts/Scene/RandomGrassColor.cs) set three groups of grass colors, including the color for the root, tip of the grass and the ground. We use the built-in random function of Unity to generate a random integer between 1-3.
 `int color = UnityEngine.Random.Range(1, 4)`
Then we use switch case to achieve randomly selected scene color matching.

    ```C#
      switch(color) {
        case 1: //color combo 1;
        case 2: //color combo 2;
        case 3: //color combo 3;
      }
    ```

2) **/Assets/Scripts/Scene/PerlinNoiseGenearator.cs**
 We created some terrain using a [script](https://github.com/Graphics-and-Interaction-COMP30019-2021/project2-project2_group_06/blob/master/COMP30019%203D%20Game/Assets/Scripts/Scene/PerlinNoiseGenearator.cs), using built-in functions `y = Mathf.PerlinNoise(x,y)` to control the height of a certain point to achieve the effect of waves for terrain.

3) **/Assets/Scripts/Inventory/Item/Monobehaviour/LootBonus.cs**
 In the [script](https://github.com/Graphics-and-Interaction-COMP30019-2021/project2-project2_group_06/blob/master/COMP30019%203D%20Game/Assets/Scripts/Inventory/Item/Monobehaviour/LootBonus.cs), We can add a list of items that the enemy may drop, and set a weight for each item (meaning the probability of dropping). The weight is between 0-1, when the enemy is dead, a random number between 0-1 will be generated. If that number is smaller or equal to weight of loot, then the loot will drop out.

    ```C#
      if (currentValue <= loopItem.weight) {
        // drop some loots in the ground
      }
    ```

4) **/Assets/Scripts/Tools/RandomlyGenerateSupplies.cs**
The last one procedural generation is that we create a supply items rain in the game per 10 mins. The position, the kind of item are generated by the C# [Script](https://github.com/Graphics-and-Interaction-COMP30019-2021/project2-project2_group_06/blob/master/COMP30019%203D%20Game/Assets/Scripts/Tools/RandomlyGenerateSupplies.cs).Similar to the algorithm introduced in 3), We use random numbers to control the generated items. First we get a random number  for the numbers of items that will drop down in the rain. Then in each for loop we also use random numbers to determine which kind of item and whether it will drop or not. Cool down time of supply rain could be set as well and it will display on the Player UI.

    ```C#
    void OnEnable()
    {
        for (int i = 0; i < randomGenerateNum; i++) {
            randomGenerateSupply();
        }
        ...
    }
    void randomGenerateSupply() 
    {
      randomIndex = Random.Range(0, supplies.Length); // randomly get the index in the supplies array
      currentValue = Random.value; 
      // compare the weight with the random value
      if (currentValue <= supplies[randomIndex].weight) {
          // generate this item in random position with given range.
      }
    }
    ```

## Custom Shaders

All the shaders used in the game are written by ourselves, including shader graph and CG/HLSL shader.

here is the list of shaders we used:

- Rock (Shader Graph)
- Water (CG Shader)
- Lava (Shader Graph)
- Grass in initial scene (HLSL Shader)
- Grass in main scene (Shader Graph)
- Leaves (Shader Graph)
- Portal effects (Shader Graph)
- Rock (Shader graph)

**List for shader that need to mark**

- [Water (fragment and vertex shaders)](https://github.com/Graphics-and-Interaction-COMP30019-2021/project2-project2_group_06/blob/master/COMP30019%203D%20Game/Assets/Shader/SimpleWater.shader) **Assets/Shader/SimpleWater.shader**

  1. Introduction
     This shader is based on the Roystan's article "[Toon Water Shader](https://roystan.net/articles/toon-water.html)", this tutorial is suitable for who are new to the shader programming. Really learned a lot by following his tutorial step by step. In tutorial, Roystan has explained how to render the effect of the surface noise wave and the interaction foam between water and objects. These will be introduced in the detail section below. In addition to the effects implemented in the tutorial, the Blinn-Phong lighting model, the vertex animation based on the trigonometric function waveform superimposition and the edge/rim lighting model are added to the shader.
     <img src="/Gifs/water_mesh.gif">

  2. How it works ?
     This water shader is a fragment and vertex shaders, which means it contains a vertex shader and a pixel/fragment shader. For vertex shader, it receives the geometry data from the CPU - a plane. In the vertex shader, the vertex data gets processed and updates the output into the structure we specify which contains data like normal and position vector in world space or view space etc.(as the input of the fragment shader)
     a) **Vertex part**
     There is a function `calculateSurfaceHeight` that uses the superposition of two SIN functions to change the y value - height of the vertex. To achieve the up and down vertex animation.

     ```C#
       float calculateSurfaceHeight(float x, float z, float scale)
       {
           float y = 0.0;
           y += (sin(x * 1.0 / scale + _Time.y * 1.0) + sin(x * 2.3 / scale + _Time.y * 1.5) + sin(x * 3.3 / scale + _Time.y * 0.4)) / 3.0;
           y += (sin(z * 0.2 / scale + _Time.y * 1.8) + sin(z * 1.8 / scale + _Time.y * 1.8) + sin(z * 2.8 / scale + _Time.y * 0.8)) / 3.0;
           return y;
       }


       v2f vert (appdata v)
       {
         ...
         v.vertex.y += _WaveStrength * calculateSurfaceHeight(v.vertex.x, v.vertex.z, _WaveScale);
         o.vertex = UnityObjectToClipPos(v.vertex);
         ...
       }
     ```

      <img src="/Gifs/river_wave.gif">

     b) **Fragment/Pixel part**:
     depth-based coloring:
     Select two colors, `_ShadowColor` and `_DeepColor`, and use the `waterDepthDifference` (between 0-1) as interpolates for the `lerp` function to achieve a gradient of water color depth.
     `sampler2D _CameraDepthTexture` is the depth map obtained from the camera. The distance from the observation point to the bottom of the river can be obtained from the depth map. We are concerned about how deep this depth value is relative to our water surface. So eyeDepth need to reduce the w component of screenPos.
     <img src="/Gifs/beach-depth-diagram.png">

     ```C#
       float4 frag (v2f i) : SV_Target
       {
         ...
         half4 screenPos = i.screenPos;
         half eyeDepth = LinearEyeDepth(UNITY_SAMPLE_DEPTH(tex2Dproj(_CameraDepthTexture,UNITY_PROJ_COORD( screenPos ))));
         half eyeDepthToScreenPos = abs( eyeDepth - screenPos.w );
         float waterDepthDifference = saturate(eyeDepthToScreenPos / _DepthMaxDistance);
         float4 waterColor = lerp(_ShalowColor, _DeepColor, waterDepthDifference);
         ...
       }
     ```

     Blinn-Phong lighting model:
     In vertex part, the shader has processed the data about normal, so it can be used to calculated the illumination. Common illumination models include Lambert, Blinn-Phong, PBR,etc. Here we use Blinn-Phong lighting model, cause it a modification to the Phong reflection model. It calculated by 'halfway angle `halfDir` between the light and the view direction. So it will become much smoother as specular model.
     common implementation following this [tutorial](https://www.jordanstevenstechart.com/lighting-models):

     ```C#
       float4 frag (v2f i) : SV_Target
         {
           ...
           fixed3 diffuse = _LightColor0.rgb *waterColor* NdotV ; // NotV = dot(worldNormal,viewDir)
           fixed3 halfDir = normalize(lightDir + viewDir);
           fixed3 specular =  _Specular * pow(dot(worldNormal, halfDir), _Gloss) * _SpecularColor; // _Specular & _Gloss are params
           waterColor = fixed4((max(0,dot(worldNormal, lightDir))*diffuse.rgb+specular),1);
           ...
         }
     ```

     Rim Lighting Effect:
     When the line of sight is not perpendicular to the surface, the smaller the angle, the more obvious the rim color will be.

     ```C#
       float4 frag (v2f i) : SV_Target
       {
           ...
           float rim = 1 - max(0, dot(viewDir, worldNormal));
           fixed3 rimColor = _RimColor * pow(rim, 1 / _RimPower);
           waterColor = fixed4((max(0,dot(worldNormal, lightDir))*diffuse.rgb+specular+rimColor),1);
           ...
       }
     ```

     Foam effects:
     Foam effects will enable in two situations:1) on the shore 2) object intersect with the water. The algorithm is similar to what we used to calculated the water color rendering based on scene depth. Get the foam mask by comparing the depth of the scene and the depth of the water. Finally, let the formula composed of depth difference and parameters for interpolation, and use the `lerp` function to mix the original `diffuse` and `_formColor`.

     Waves:
     First,use a noise texture to generate original UV coordinates for the wave to the surface. Then, add a cutoff threshold to ignored these coordinates that smaller than the threshold. Add more movement and distortion using a distortion texture. Interpret the red and green channel as offset and displace the origin UV using `_Time.y` to affect the previous wave formed by the noise map. Finally use `alphaBlend` function to Blends `surfaceNoiseColor` and `WaterColor` together.

     **Discussion on CPU based approach**

- [Grass in initial scene (Geometry Shader)](https://github.com/Graphics-and-Interaction-COMP30019-2021/project2-project2_group_06/blob/master/COMP30019%203D%20Game/Assets/Shader/GrassShader.shader) **/Assets/Shader/GrassShader.shader**

  1. Introduction
     Unlike the previous water shader, this grass shader is a geometry shader. geometry shader includes the vertex processing stage function added in DX10 and OpenGL4.1. It can take a single primitive as input and output zero or more primitives, which means that we can use this function to obtain triangle primitive vertex information. Which means this grass shader will generate the mesh of grass by itself with given point and add color in the fragment step.
     reference:
     [GPU GEMS - CHAPTER 7](https://developer.nvidia.com/gpugems/gpugems/part-i-natural-effects/chapter-7-rendering-countless-blades-waving-grass)
     [Grass Shader by roystan](https://roystan.net/articles/grass-shader.html)
     [Using the Geometry Shader In Unity To Generate Countless Of Grass On GPU](https://medium.com/chenjd-xyz/using-the-geometry-shader-in-unity-to-generate-countless-of-grass-on-gpu-4ca6d78b3de6)
  2. How it works ?
     In the procedural generation mentioned above, we have several terrains generated based on perlin noise in the tutorial scene. The grass geometry shader will take effect on these terrains.

      1) First, we use the technique of tessellation (sourced from [here](https://catlikecoding.com/unity/tutorials/advanced-rendering/tessellation/)) to divide the vertices for our terrain. This link is executed on the CPU, and the random point output is the root of each grass.
      2) Use the Geometry Shader, to take the point as the "root" and use this as the bottom midpoint to generate a grass mesh. The algorithm how to insert the triangle is divided by [roystan](https://roystan.net/articles/grass-shader.html)'s article. Construct our blade with several triangles and bend it along the curve, each blade of grass will be subdivided into multiple parts. Each part is rectangular and consists of two triangles, except for the top part-this will be a triangle representing the tip of the blade.
      3) Use own construct uv to sample the texture of the Normal Map, and use the result for the wind x and y values. Now construct a matrix to rotate about this vector of grass.
      4) Use the rotation matrix to solve the artifacts generated when viewed from the side of the grass piece
     <img src="/Gifs/grass-construction.gif" width = 50%>
      5) After the calculation of the grass mess is completed, the data is passed to the fragment shader, and the color of the pixel is determined by the Blinn-Phong lighting model and the color determined by the height of the grass.

        ```C#
          float4 frag (GeomData input) : SV_Target
          {
            // Blinn-Phong lighting model
            real3 positionWS = input.worldPos;Light mainLight = GetMainLight();
            real3 lightColor = mainLight.color;
            real3 normalWS = normalize(input.normal);
            real3 lightDir = normalize(mainLight.direction);
            float4 albedo = tex2D(_BladeTexture, input.uv) ;
            real3 ambient = UNITY_LIGHTMODEL_AMBIENT * 2 * albedo;
            real3 viewDirectionWS = normalize(GetCameraPositionWS() - positionWS);
            real3 halfVector = normalize(viewDirectionWS + lightDir);
            real3 specular = pow(max(0,dot(halfVector, normalWS)), _Smoothness) * lightColor * saturate(_SpecColor);

            float3 light = ambient + diffuse + specular;

            // lerp function to achieve a gradient color from the root  to the top
            return real4( light,1.0f) * lerp(_BaseColor, _TipColor, input.uv.y);
            }
      ```

      <img src="/Gifs/Specular_Grass.gif">

  **Discussion on CPU based approach**
  The traditional way to render some grass is to pass the grass model data from the CPU to the GPU, and then the GPU renders based on the data. Because of the small size of a grass, there can be a lot of grass in a grassland. If the grass model is too complex, there will be too many polygons to pass to the GPU. This may cause a CPU performance bottleneck, which in turn leads to slow rendering speeds. (The GPU needs to wait for the CPU to transmit polygon data)
  But if it is implemented with a geometry shader, this problem will be solved. Because the CPU only needs to calculate the vertex position of each grass root. The remaining calculations, such as adding triangles and creating meshes, are all performed by GPUs with excellent graphics and floating-point computing capabilities.

## Particle System

This is the list of particle effects used in the game
  1. Spiral shot from a cannon
  <img src="/Gifs/cannon.gif">
  2. Ranged attack from yew-wood staff
  <img src="/Gifs/ranged_attack.gif">
  3. Snow effects in the snow mountain area
  <img src="/Gifs/snow.gif">
  4. Smoke effect on the top of the volcano
  <img src="/Gifs/volcano.gif">
  
  5. Explosion effect of enemy death
  <img src="/Gifs/enemy_dead.gif">
  6. Burn effects on characters and enemies (This does not represent the final game experience : D)
    <img src="/Gifs/burn_effect.gif"> No way, I'm back with the **hack** - edit the base health of player !


  <img src="/Gifs/hack.gif">

  7. The effect of the Treant Boss healing himself
    <img src="/Gifs/treant.gif">

### Which one should be marked
  **Spiral shot from a cannon** : The first Particle System mentioned above
  <img src="/Gifs/cannon.gif">

### How to locate it in the project
  The cannon’s particle effect (Spiral shot) will be triggered after the player walks within its range. The particle life cycle is divided into three stages.
  1)The first is the charging stage. The cannon’s muzzle will condense to generate particle effects, which will continue to rotate and become larger. It reaches the maximum after five seconds.
  2)The second stage is the projectile will move along the route calculated by the parabolic script. During this stage, particle effect will maintain in its completed form.
  3)The third stage is the explosion effect after the hit. After the hit, that is the end of particle life cycle.

## Observational and Querying Methods
### Observational Methods    
      
  There are three observational methods used in the evaluation process of the game. Which one or more of them to use on an observed player depends on the two following questions for the player: 1) How do you feel about playing the game while thinking aloud and having assistance? 2) What types of games do you often play? Given the answers from the player to these two questions, **appropriate methods would be used to balance between extracting information and avoiding interruptions.** For example, if a player is not feeling thinking aloud nor having any assistance during the playing process, then the observer would choose to use the post-task walkthrough method; on the other hand, if a player does not mind thinking aloud nor assistance during the game process, then the observer may choose to use both methods in the same observation process.
      
  1. Think aloud  
      
      Think Aloud is the most direct and simple method among the applied methods. It is also a productive method for observing experienced players or professionals in the game industries since these the observed often already have systematic methodologies to learn and understand a game and mechanics behind it and share their insights vocally. The information gained can be quite subjective which is exactly the point here, we want players' first-hand opinions so that we can process and reflect on them for later improvements on the game. Since the observed are all familiar with the observer as close friends and they are all formally informed that honest opinions are highly appreciated, there should be a little awkwardness during the observation.
      
  2. Cooperative Evaluation  
      
      Cooperative Evaluation is a much more relaxed method compared to the other methods (for players who does mind this method of course) because it is generally having conversations about the playing process. For the same reason, it can be a good practice 
      to combine this method with Think Aloud, as the cooperative conversation may help elicitating more information especially when the observed player somehow stops to think aloud, after all, not everyone can be accustomed to this playing style. Also, cooperative evaluation can obviously help the player to get through unexpected obstacles, especially when the game is still in the development process and bugs or other unintended situations may occur. This method can cause some biased results as the observer may help too much in the observation process, therefore, the observer should plan ahead on the issues to investigate during the observation, such as key game elements, mechanics, etc. Specifically, if there is a targeted issue that the player is confused about, then the observer should first collect enough information about the confusion before helping out the player.
      
  3. Post-task walkthrough  
      
      Post-task Walkthrough set the player free from any interruptions from the observer completely, in our game's case, letting a player explore the open area to test the 
      layout of the area in the game can be a good subject to observe with this method. In this case, the observer can also spend more time observing the player's behaviour without having to write down any comments from the player. The player may forget some of the details of the observed playthrough, therefore, it is best to keep a record of it to remind the player so they can share more of their thoughts on the played content.

  - **Observed Players & Evaluation**

  
    | Participant Name | Date | Persona | Observational Method | Tasks | Results | Evaluation | Improvements |
    |---|---|---|---|---|---|---|---|
    | Qingxun Huang | Oct 13, 2021 | Hardcore gamer that has extensive experiences in playing all kinds of games, especially for third-person action games and ARPGs. | Think Aloud, Cooperative Evaluation | Explore the bottom area (the area with river), basic combat, defeat the stone golem boss | The exploration was mostly smooth but the player find the exploration was a bit tedious, there were some unintended invisible obstacles that prevented the player from exploring freely. The player took a lot of damage before understanding the reflect damge mechanic of the stone golem but still managed to defeat it, the player liked the combat style despite its simplicity, but he thinks the movement transition was a bit clunky. | The open-world level should clearly distinguish the walkable areas and the non-walkable ones for the players. The stone golem's reflect damage mechanic was approved by the player but we should find a way to indicate the mechanic to the players before they engage with the stone golem.  | Ensure the walkable areas and the non-walkable areas area clearly distinguished. Set up a hint to the ability and potential vulnerablility of the bosses before playes engage with the boss. |
    | Yixin Lu | Oct 18, 2021 | Casual player that has some experience in third-person open-world games and card games. | Think Aloud, Cooperative Evaluation | Pass the beginner level, explore the left area try out items and equipment | The player was a bit confused in the beginner level about the objectives of it, the player likes the combat system and thought it was easy to learn and play, he generally like the buildings' layourt in the explored area but he thought it would be better if there were some variation in the shape of terrain. The player liked the UI that mange the items and equipment because it was easy and clear to use. The player found it  was difficult to hit enemies with attack, and the aiming of the ranged weapon was also clunky. | The tutorial level was supposed to teach player the basics of the game but due to the lack of proper user interfaces, the tutorial level cannot fully serve its purposes. The combat system is solid but we can iluustrate some of the details of it betterm such as the critical strike mechanic. For now, the open-wolrd level was build on a  fully falttend terrain, it should be a good idea to add some changes of elevation of the terrain here and there. Due to the limit of resources and time, we cannot implement a manual lock-on system, so, we must use a simpler alternative method to compensate. | Adding and polishing the user interfaces in the tutorial level. Add some variations to the elevation of the terrain if the remaining time permits. We decided to make melee and raged attack automatically locks on the enemy when the enemy is whitin the attack range. |
    |  Yujun Zhang | Oct 17, 2021 | Junior game developer. gamers with extensive experiences in many kinds of games. | Post-task Walkthrough | Explore the right area and middle area, defeat the fire demon boss  | The player find the right area empty because he thought there were not much items to find or enemy to kill, he find the fire demon boss did not have any special ability related to fire, he suggested that we add some relevant mechanic to it. | We can arrange the distribution of the monster and items of some areas to increase the number of objectives for the player to persue. The fire demon looks appealing but for now it does need more special mechanic that we added to the corrupted tree and stone golem bosses to make it special whilst consistent with its apperance. | Arrange the monsters in the proper location after the layout is improved. Add burning ailments to the fire demon's attack which can damage the player's health over time in a period. |
    | Leili Shen | Oct 26, 2021 | Junior game developer. very into Souls games. | Think Aloud | Explore the top area, defeat the icy spirit boss | The player liked the top area' layout but he suggest we could add some NPCs in the town even they can not be interacted with, he also suggest we can refer to Souls game level design to parts of our open-level, he find the icy spirirt boss did not have any special ability related to ice, he suggested that we add some relevant mechanic to it. | Adding NPCs is great but we should consider the limit of time and resources before adding complex systems like this. Level design imporvment is also great but it is demanding on the required time to learn and develop. Icy spirit boss has the similar issues with fire demon boss. | If the remaining time is enough, we would try to add NPCs and achieve relevant requirements. Applying some methodologies that professional level designers use in their game to some linear level in the open world if we have time. Add frozen effect to the icy spirit boss's attack which slows down the player's movement in a short period. |
    | Yunxin Li | Oct 27, 2021 | Intern game designer, very into story-driven and character-driven games regardless of the genre of the games. | Cooperative Evaluation, Post-task Walkthrough | Defeat corrupted tree, try to combat with the elite enemies | The player was like the regenaration mechanic of the coorrupted tree boss because she thought it fits the them of the boss. The player found the elite enemies quite hard to defeat at first, but with the right equipment, she found the difficulty of defeating them was acceptabe. | The corrupted tree boss was a successfully designed boss same as the stone golem boss because their ability is unique and fits their themes and apperances. We can guide the player better on how to defeat the elite enemy by gathering legendary gears and character-strengthen consumables. | Rearrange the positions of the elite enemies and teach player about the  importance of having good gears and items before challenging elite enemies. |
    
### Query Techniques

1. Questionnaire
        
      Questionnaires targeted players that had little experience in third-person shooter games or action games. The questionnaire consists of interweaving close-ended and open-ended questions, where the close-ended questions targeted specific gameplay features and guide the player through the game. The logic employed in this part of the questionnaire is similar to that of unit tests in software engineering. The open-ended questions at the end of the questionnaire are general qualitative questions that prompt the players for feedback on the game holistically. 
        
      - Close-Ended Questions
        
        1. Were you confused about any part of the game?
        2. Was the beginner tutorial easy to follow? Did it provide sufficient introduction to the game such that you had no trouble navigating the remainder of the game?
        3. Were you able to defeat amateur enemies with no problem?
        4. Were you able to defeat the four beasts with no problem?
        5. Were you able to defeat the final boss with no problem?
        6. Were you able to change weapons?
        7. Were you able to dodge attacks from the enemy?
        8. Were you able to attack enemies?
        9. Were you able to use the Portal to go to the next realm?
        10. Were you able to navigate through the First World to each of the 4 arenas with no problem?    

      - Open-Ended Questions
        
        1. What did you think of the game overall?
        2. What do you think can be improved?
        3. Would you play the game in your own time if the game is complete with more levels and become a full-fledged adventure?
        4. Would you recommend this game to people around you? If so, what type of people would you recommend this to and why?
        5. Do you think this game is a good introduction to third-person games? Why or why not?
<br></br>
  2. Interview
        
      Interview targeted players that have prior experience in a plethora of video games and has their own preferences in different categories of video games. These players are likely to have their expectations of what a TPS game should look like and how the gameplay should work. Therefore, the close-ended interview questions were qualitative and focused on the gameplay experience of these veteran players. The open-ended questions provided space for the veteran players to expand on their close-ended answers.

      - Close-Ended Questions
        
        1. Is the game beginner-friendly or not?
        2. Is the game fun and enjoyable or not?
        3. Is the game objective clear and well-specified by the instructions or not?
        4. Does the game controls match my expectations or not?
        5. Is the game bug-free or not?
        6. Is the gameplay polished and highly aligned with the design of the game or not?
        7. Are the game objects clearly visible and distinguishable or not?
        8. Are the game aesthetics consistent or not?
      
      - Open-Ended Questions
        
        1. What did you think of the game overall?
        2. What do you think can be improved?
        3. Would you play the game in your own time if the game is complete with more levels and become a full-fledged adventure?
        4. Would you recommend this game to people around you? If so, what type of people would you recommend this to and why?
<br></br>
   - **Queried Players & Evaluation**
    
      | Participant Name | Date | Persona | Querying Technique | Results | Evaluation | Improvements |
      |---|---|---|---|---|---|---|
      | Leo Han | Oct 13, 2021 | Fan of MOBA games, favourite game is DOTA with 9 years of experience. | Interview | [Video Interview with Leo](https://drive.google.com/file/d/15Vcpjd-ssLtUYmsMavNffPbmw9VgNwNe/view?usp=sharing)| We conducted interview with Leo first in the early phases of our game development, as Leo is an experienced gamer that we expected insightful advices from. His results demonstrated that the biggest flaw of the game at this stage is the lack of instructions, or tutorials, for a beginner. At this stage, we only have a 1-page basic instructions tab that is accessible from the landing screen and nowhere else. From interviewing Leo, we decided to add a tutorial to the game and polish our game design further to reduce the feeling of that the game was buggy in terms of character movement, actions etc.  | Add a tutorial to the beginning of the game for players to familiarise themselves. |
      | Mustafa Awni | Oct 20, 2021 | Fan of Battle Royale games, favourite game is Witchcraft with 5 years of experience.  | Interview | [Video Interview with Mustafa](https://drive.google.com/file/d/1NAhfFTmMDW03xmwJDoJ0RPtcVmbLSlCY/view?usp=sharing) | As a fan of the equipment and combat components of Battle Royale games, Mustafa thoroughly enjoyed our game as it had similarities in terms of allowing characters to pick up and use weapons/supplies. Highlights of the game for Mustafa was the creativity of the 4 arenas guarded by Elemental Beasts, and the ability to level-up into the main game after completing the tutorial section. Mustafa provided specific feedback on a gameplay bug that he found, detailed in the improvement section, and that the gold statue in the game, at this stage, is overly bright compared to its surroundings. Suggested to add music when character is walking around. | Discovered and fixed gameplay bug where players cannot pick-up and equip weapons in the main game, therefore has to combat the Elemental Beasts with their bare hands. Tone down brightness of golden statue. Implement background music throughout the game if possible. |
      | Keith Leonardo  | Oct 27, 2021 | Fan of FPS games, favourite game is Halo with 7 years of experience.  | Interview | [Video Interview with Keith](https://drive.google.com/file/d/19T3VGABVBHQ4lwYIMnE8Qvj0uEJM3loY/view?usp=sharing) | We conducted interview with Keith when our game is quite mature, as Keith is a fan of FPS games which is pretty similar to TPS, so Keith is essentially a good representative of our target audience. He gave largely positive feedbacks for the overall structure and logic of gameplay, and some constructive feedbacks for the graphics and animation of the game. He would recommend this to players that enjoy RPG games like Dark Soul.| Make the graphics and animations more consistent and less clunky, for example, smooth out the transition between different arenas and process of entering portals.|
      | Ayesha Ahmed | Oct 13, 2021 | Fan of sandbox games, 1 years of experience in Minecraft. | Questionnaire | [Link to excel sheet](https://docs.google.com/spreadsheets/d/1r83Bw8mvNn4hyBinYGLTO4H1BAWOxQA6JJbKd7vUxYU/edit?resourcekey#gid=87256782) | We conducted interview with Ayesha in early phases of our game development because Ayesha is a fan of sandbox games like Minecraft and we would appreciate her feedback on the creativity and aesthetic aspects of our game at this stage. Once we confirm that the aesthetics are consistent and of a high standard, we began developing more characters and levels with the same theme.  | Make the beasts slightly smaller and more proportional to the main protagonist.  |
      | Mina Nguyen | Oct 20, 2021 | Fan of sandbox games, 1 years of experience in Minecraft. | Questionnaire | [Link to excel sheet](https://docs.google.com/spreadsheets/d/1r83Bw8mvNn4hyBinYGLTO4H1BAWOxQA6JJbKd7vUxYU/edit?resourcekey#gid=87256782) | Mina is interviewed at around the half-way mark of our development process for her experience in strategic games. We appreciated her feedback in testing the game logic and consistency in design. She found the Elemental Beasts very difficult to defeat even with much strategic thinking throughout the game. However, she loved the colours and theme of the game overall, with the only suggestion being to make the tutorial town slightly darker.  | Make tutorial town slightly darker in their colour schemes, and adjust difficulty level of Elemental Beasts. |
      | Fiona Tran  | Oct 27, 2021 | Fan of online boardgames that are based on creativity, like Skribblio and Gartic Phone. Started playing online boardgames regularly during COVID-19 lockdowns. Little to no experience in other types of video games. Never tried out any combat video games as she always thought they are too difficult.  | Questionnaire | [Link to excel sheet](https://docs.google.com/spreadsheets/d/1r83Bw8mvNn4hyBinYGLTO4H1BAWOxQA6JJbKd7vUxYU/edit?resourcekey#gid=87256782) | We interviewed Fiona towards the end of our game development because we wanted insights from the whole spectrum: with perspective of our target audience (represented by Keith) on one end, and perspective of a beginner with little to no knowledge of combat video games (represented by Fiona) on the other end. Fiona found the game very enjoyable and a good introduction to TPS games for beginners like herself. | Possibly make the characters cuter. |

## Improvements based on Evaluation
- **Lock-on System & Attack-Hit**  

    Some amateur players found it was hard to accurately hit the enemy, specifically, an accurate hit required the players to precisely aim the target with the invisible crosshair in the middle of the screen. Therefore, we added a sphere collider of which radius roughly equalled to the attack range of the player character so that the enemy within the attack range would be immediately detected and made ranged attack projectiles homing for the nearest enemy with its attack range (the player still has to manually aim for a target that is out of the range). Consequently, any enemy within the sphere collider or the range of a ranged weapon can be accurately hit by an attack, regardless of the location of the cursor (which controlled the camera and the invisible crosshair). Furthermore, we increased the size of the weapon and its collider to make hitting enemies easier.
    
- **Tutorial-Level UI**  

    Though the tutorial level was properly designed to get players to familarise the game and teach the players about the basics of the game, such as movement, combat, different types of enemies,etc., many players found the content of the tutorial level needs some visual guidance. Their feeback was right on the point because during the evaluation process, the objectives of each sub-level in the tutorial level was unclear without us explaining them to some of the players, let alone the mechanics used in attempt to teach the players. Therefore, we added some visual user interfaces to the tutorial level, for example, in the sub-level of teaching player to move, we added pictures of relevant keys on the keyboard and text instructions that explain the usage of those keys (`W`,`A`,`S`,`D`,`Shift`, etc.).

- **Elemental Beast Mechanics**  

    According to the feedback of the player, the Fire Beast and Ice Beast were not having any obvious abilities that are relevant to their themes other than their appearances and visual effects such as particle systems. Therefore, we designed an ability for each of them to emphasize their themes. For the fire boss, we gave it an ability to apply burning damage with its attack which would inflict a damage over-time on the player. As for the Ice Beast, it was given a ability to freeze the player. Moreover, the player can also aqcuire and use these abilities after they defeat the corresponding Elemental Beast. We also changed the prefabs of Fire Beast and Ice Beast from elemental creature style to a more demonized hummanoid style, in hopes of increasing their level of intimidation.
    
- **Level Layout**  

    As some of the player pointed out, when the game was evaluated in the early stage and middle stage, some parts of the open-world level was a bit empty and tedious as there were little items to find or enemies to kill. Based on this feedback, and the fact that we found there were too many static prefabs in the level so that the game performance was negatively impacted, we first adjusted the buildings and other static prefabs in the main game level to decrease the complexity of the level slightly. To make exploring the world more interesting, we also adjust the elevation of some parts of the world so that it would not be too predictably flatten throughout the world. Finally, we re-design the arrangements of enemies and items in the world to make the objectives spread evenly in the world.
    
- **Art & Aesthetics**  

    We adjusted the brightness of the colour theme of some parts of the open world level to make it consistent throughout the whole game level as there were some feedback on the colour theme sometimes being inconsistent on its brightness from the evaluation process.

## References
- [Billboard](https://assetstore.unity.com/packages/tools/modeling/lod-billboards-29080)
- [Creation of flow effects](https://catlikecoding.com/unity/tutorials/flow/)
- [Fantasy Wooden GUI](https://assetstore.unity.com/packages/2d/gui/fantasy-wooden-gui-free-103811)
- [Fire Demon](https://assetstore.unity.com/packages/3d/characters/creatures/fire-demon-43668)
- [Free Pixel Font - Thaleah](https://assetstore.unity.com/packages/2d/fonts/free-pixel-font-thaleah-140059)
- [Free RPG Fantasy Spell Icons](https://assetstore.unity.com/packages/2d/gui/icons/free-rpg-fantasy-spell-icons-200511)
- [Free RPG Weapons](https://assetstore.unity.com/packages/3d/props/weapons/free-rpg-weapons-199738)
- [Free Skybox Extended Shader](https://assetstore.unity.com/packages/vfx/shaders/free-skybox-extended-shader-107400)
- [Generic-refraction-simulation](https://developer.nvidia.com/gpugems/gpugems2/part-ii-shading-lighting-and-shadows/chapter-19-generic-refraction-simulation)
- [Lowpoly Environment - Nature Pack](https://assetstore.unity.com/packages/3d/environments/lowpoly-environment-nature-pack-185195)
- [Low-poly-style water shader](https://roystan.net/articles/toon-water.html) 
- [Med Kits + Health Packs](https://assetstore.unity.com/packages/3d/props/med-kits-health-packs-4928)
- [Menu UI Creation](https://www.youtube.com/watch?v=zc8ac_qUXQY)
- [Mini Legion Footman PBR HP Polyart](https://assetstore.unity.com/packages/3d/characters/humanoids/fantasy/mini-legion-footman-pbr-hp-polyart-86576)
- [Mini Legion Grunt PBR HP Polyart](https://assetstore.unity.com/packages/3d/characters/humanoids/fantasy/mini-legion-grunt-pbr-hp-polyart-98187)
- [Mini Legion Lich PBR HP Polyart](https://assetstore.unity.com/packages/3d/characters/humanoids/fantasy/mini-legion-lich-pbr-hp-polyart-91497)
- [Mini Legion Rock Golem PBR HP Polyart](https://assetstore.unity.com/packages/3d/characters/humanoids/fantasy/mini-legion-rock-golem-pbr-hp-polyart-94707)
- [Polygonal - Treant](https://assetstore.unity.com/packages/3d/characters/creatures/polygonal-treant-116319)
- [RPG Character Mecanim Animation Pack](https://assetstore.unity.com/packages/3d/animations/rpg-character-mecanim-animation-pack-63772)
- [RPG Monster Duo PBR Polyart](https://assetstore.unity.com/packages/3d/characters/creatures/rpg-monster-duo-pbr-polyart-157762)
- [RTS Mini Legion Undead PBR](https://assetstore.unity.com/packages/3d/characters/humanoids/fantasy/rts-mini-legion-undead-pbr-151081)
- [Simple Fantasy GUI](https://assetstore.unity.com/packages/2d/gui/simple-fantasy-gui-99451)
- [Titan Town](https://assetstore.unity.com/packages/3d/environments/fantasy/titan-town-47104)

## Project is created with:
* Unity 2021.1.13f1
* Ipsum version: 2.33
* Ament library version: 999


## Task Checklist:

- [x] Read the handout for Project-2 carefully.

- [x] Brief explanation of the game.

- [x] How to use it (especially the user interface aspects).

- [ ] How you designed objects and entities.

- [x] How you handled the graphics pipeline and camera motion.

- [x] The procedural generation technique and/or algorithm used, including a high level description of the implementation details.

- [x] Descriptions of how the custom shaders work (and which two should be marked).

- [x] A description of the particle system you wish to be marked and how to locate it in your Unity project.

- [x] Description of the querying and observational methods used, including a description of the participants (how many, demographics), description of the methodology (which techniques did you use, what did you have participants do, how did you record the data), and feedback gathered.

- [x] Document the changes made to your game based on the information collected during the evaluation.

- [x] References and external resources that you used.

- [ ] A description of the contributions made by each member of the group.





<!-- ## Using Images

You can use images/gif by adding them to a folder in your repo:

<p align="center">
  <img src="Gifs/Q1-1.gif"  width="300" >
</p>

To create a gif from a video you can follow this [link](https://ezgif.com/video-to-gif/ezgif-6-55f4b3b086d4.mov).

## Code Snippets 

You can include a code snippet here, but make sure to explain it! 
Do not just copy all your code, only explain the important parts.

```c#
public class firstPersonController : MonoBehaviour
{
    //This function run once when Unity is in Play
     void Start ()
    {
      standMotion();
    }
}
``` -->




