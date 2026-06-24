# PlanetfallEffects
Planet particle effects mod for KSP


**Planet Fall Effects -- examples on stock bodies.**

A body may have MORE THAN ONE PFE_PRECIPITATION node. Add a `biomes` line to
restrict a node to specific biomes; omit it and the node covers the whole
body. When nodes overlap on one body the most specific wins: a matching
biome-restricted node beats a whole-body node. (Per-biome precipitation --
the weather analogue of per-biome scatters.)

For Laythe: Applies to the entire planet.

**PFE_PRECIPITATION**
{
    body = Laythe
    type = Rain
    maxAltitude = 4000
    emissionRate = 1000
}

For Kerbin: snow ONLY over the icd  biomes, this is the per-biome feature.
Everywhere else on Kerbin stays clear.

**PFE_PRECIPITATION**
{
    body = Kerbin
    type = Snow
    biomes = Ice Caps, Northern Ice Shelf, Southern Ice Shelf
    maxAltitude = 4000
    fallSpeed = 2.5
    emissionRate = 500
}

_*Keys*_

**PFE_PRECIPITATION**
{
    body = Duna              // internal body name (must match exactly)
    type = Snow              // Snow or Rain - sets all the per-type defaults below

    // --- Region (optional) -----------------------------------------
    biomes = Poles           // comma-separated, or repeat the key; omit = whole body

    // --- Activation envelope ---------------------------------------
    maxAltitude = 6000       // effect active below this ASL altitude (m)
    fadeFraction = 0.25      // emission fades over the top 25% of that band
    maxSurfaceSpeed = 250    // disables above this surface speed (m/s)

    // --- Motion ----------------------------------------------------
    fallSpeed = 1.0          // terminal fall speed along local gravity (m/s)
    windSpeed = 1.5          // mean horizontal wind (m/s); gusts via Perlin noise
    velocityJitter = 0.25    // random per-particle velocity spread (m/s)
    flutter = 0.7            // particle tumble via noise module (snow ~0.5-1, rain 0)

    // --- Appearance ------------------------------------------------
    sizeMin = 0.03           // particle size range (m)
    sizeMax = 0.09
    color = 1.0, 1.0, 1.0, 0.9   // RGBA, 0-1
    texture =                // optional texture path; blank = soft dot
    streakScale = 0.0        // rain only: velocity-stretch for streaks (e.g. 0.06)

    // --- Spawn volume around the camera ----------------------------
    areaRadius = 45          // spawn disc radius (m)
    spawnHeight = 25         // spawn height above camera (m)
    killDepth = 35           // lifetime cutoff below camera (m)

    // --- Throughput ------------------------------------------------
    emissionRate = 350       // particles per second at full intensity
}
