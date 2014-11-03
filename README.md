-------------------------------------------------------------------------------
CIS565: Project 5: WebGL
-------------------------------------------------------------------------------
Fall 2014
-------------------------------------------------------------------------------
Jiatong He
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
PART 1 - Mesh Vertex Shader
-------------------------------------------------------------------------------
###Implemented Features

*Implemented a sin wave in the vertex shader in vert_wave.html.
Implemented custom color selection using dat.GUI, and basic color interpolation for between the high and low points on the grid.

*Implemented a centered wave in the vertex shader in vert_ripple.html.
>This wave spreads out from the center and has an exponential falloff in height as it moves away from the center.
>The sin function is based on distance from the center of the grid.

-------------------------------------------------------------------------------
PART 2 - Globe Fragment Shader
-------------------------------------------------------------------------------
###Implemented Features

####Night-time lights on the dark side of the globe
![night lighting]()
The sphere began with just daylight texture implemented, so I added the code for nighttime texture and added a mix to blend daylight and nighttime.  The mix I used keeps full dayColor until the diffuse term < 0.5, and full nightColor on the back of the sphere.

####Specular mapping
![specular lighting]()
The sphere originally had specular lighting on all areas.  I changed that so that only the water has specular highlights by reading from the specular map.

####Moving clouds
![clouds]()
Implemented moving clouds by reading in from the cloud map and offsetting texture coordinates by a time value.

####Bump mapped terrain
![bump mapping]()
Implemented bump mapping by reading in the current position, one unit up, and one unit right, and calculating a new normal using those values.

####Rim lighting to simulate atmosphere
![rim lighting]()
Simple rim lighting using a dot product between the normal and position.

###Extra Feature: Cloud Shadows
![cloud shadows]()
I implemented a rather basic cloud shadow technique for the globe.  The logic behind these shadows is that the light (the lit part of the globe) should cast long visible shadows near the day-night borders, and nearly no visible shadows where the globe is closest to the light.  You can see this in the image below.

![clouds shadows left]()
Clouds cast shadows to the left on the left (with respect to the light) of the globe
![clouds shadows right]()
right on the right,
![clouds shadows center]()
and none in the center.

All I did to implement this was to sample the cloud density some distance along the direction of light - position, and shifted the density to range from [0.5, 1].  Then I used it as a multiplier on the base daylight texture color.  The [0.5, 1] range was chosen because I didn't want the shadows to be too dark.

-------------------------------------------------------------------------------
GH-PAGES
-------------------------------------------------------------------------------
Since this assignment is in WebGL you will make your project easily viewable by 
taking advantage of GitHub's project pages feature.

Once you are done you will need to create a new branch named gh-pages:

`git branch gh-pages`

Switch to your new branch:

`git checkout gh-pages`

Create an index.html file that is either your renamed frag_globe.html or 
contains a link to it, commit, and then push as usual. Now you can go to 

`<user_name>.github.io/<project_name>` 

to see your beautiful globe from anywhere.

-------------------------------------------------------------------------------
PERFORMANCE EVALUATION
-------------------------------------------------------------------------------
The performance evaluation is where you will investigate how to make your 
program more efficient using the skills you've learned in class. You must have
performed at least one experiment on your code to investigate the positive or
negative effects on performance. 

We encourage you to get creative with your tweaks. Consider places in your code
that could be considered bottlenecks and try to improve them. 

Each student should provide no more than a one page summary of their
optimizations along with tables and or graphs to visually explain any
performance differences.

In this homework, we do not expect crazy performance evaluation in terms of
optimizations.  However, it would be good to take performance benchmarks at
every step in this assignment to see how complicated fragment shaders affect the
overall speed.  You can do this by using stats.js.

---
SUBMISSION
---
As with the previous project, you should fork this project and work inside of
your fork. Upon completion, commit your finished project back to your fork, and
make a pull request to the master repository.  You should include a README.md
file in the root directory detailing the following

* A brief description of the project and specific features you implemented
* At least one screenshot of your project running.
* A link to a video of your project running.
* Instructions for building and running your project if they differ from the
  base code.
* A performance writeup as detailed above.
* A list of all third-party code used.
* This Readme file edited as described above in the README section.
