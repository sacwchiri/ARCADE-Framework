I want to create a small playable farming sim game in Unity 3D.

The game should feature a third-person character in a bright, colorful 3D world with an isometric camera and a pixel-art-inspired visual style. The initial target is desktop, but the project should be designed so it can later be adapted to mobile devices in landscape orientation.

The player should be able to move around the farm, carry one plant at a time, place crops on a grid, care for them, harvest them, and sell them. Some upgrades can be aquired like a hoe(better crop), wheelbarrow (carry multiple items), irrigation (better watering), weather station (up to 5 day climate prediction).

Include 5 crop types with different:
* Grid sizes
* Growth times
* Harvest times
* Water requirements
* Nutrients requirements
* Sale values
* Negative effects

Crop growth should take between 30 minutes and 2 hours of in-game time, but development settings should allow this to be accelerated for testing.

The game should include a day-and-night cycle, with day and night lasting approximately 10 real-world minutes each.

Random rain events should occasionally water crops. The player should receive a warning before rain begins.

All important gameplay values should be configurable through one or more JSON files, including crop properties, time settings, weather probabilities, water requirements, fertilizer requirements, and sale prices.

Plants should only grow during the day. If not harvested during harvest time the plant rots and cant be sold but can be made into fertilizer in a compost bin.

Plants harvested are sold immediatly

Game runs within a simulation, when the player is offline it will track how much time has pased and simulate the time passed but be more forgivng regarding harvest times.