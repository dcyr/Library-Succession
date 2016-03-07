# README
Dominic cyr  
March 7, 2016  

## Landis Biomass Succession - serotinyMod

Serotony is a very important adaptation to fire in the boreal forest. In fact, it plays an important role in one the interaction between Jack pine and Black spruce, one of the most common tree interaction of the boreal forest.

The following summarizes a minor modification that we have done to the code of Landis-II Biomass Succession to make serotiny more realistic for boreal species. The way serotiny is simulated has been changed for all serotinous species, but some changes target specifically Jack pine.

More details about how Landis-II Biomass Succession works in general, and, more specifically, how serotiny is implemented can be found [here][http://www.landis-ii.org/extensions/biomass-succession].

We thank Christian Jauvin and Rob Scheller for their help.

#### Modifications affecting all serotinous species

* Serotiny in general is no more an "on-site" only process. The sites where mature cohorts of any serotinous species were burned are now passed to the Ward dispersal algorithm so that they can disperse seeds outside the pixels that burned.  
    + Any serotinous  species, as specified in the species attributes table, will be affected by this modification.  
    + We haven't change anything to on-site post-fire regen. Post-fire regen (serotiny and sprouting) still precede and override "normal" seeding in the first post-fire time step. However, seeding from burned mature serotinous cohorts is combined with the normal seeding process. Therefore, those seeds compete on the same level as any seeds dispersed from non-serotinous species.  
    + __It only works with the Ward dispersal algorithm.__

#### Modifications affecting only Jack pine

* The strict serotiny of Jack pine was achieved by hard-coding conditions that prevent any kind of reproduction other than seed dispersal from burned cohorts.  
    + __You must use the same species code that we've used so far ("PINU.BAN").__
    + No off-site seed dispersal from mature living cohorts of "PINU.BAN".  
    + No on-site regen from mature living cohorts of "PINU.BAN".
    + Modifying species name or adding others strictly serotinous species require recompiling the succession library and replacing the .dll. (It is only a matter of minutes now that our setup is operational.)  
    + I tried adding another possible value for the "post-fire regen" life attribute instead of hard-coding exceptions, ex. strictSerotiny, but I think that would involve modifying and recompiling the core (not sure).
    
    
Don't hesitate to contact me should you have any questions, comments, suggestions... 

Dominic Cyr  
Yan Boulanger

