---
layout: post
title:  "Tracing changes along filaments: New additions to FilFinder"
date:   2016-04-16 12:00:00 -0800
categories: research
---


The [FilFinder][filfinder_repo] algorithm continues to evolve, slowly... There are still many interesting aspects to explore in the ever-evolving story of filament extraction, and I've recently added a new one to FilFinder: width profiles along the main extent of filaments.

The code is still in development (generalized, robust fitting is non-trivial), but the basic functionality works great! Its biggest limitation is the need for a single connected skeleton, which greatly reduces the difficulty in deriving the normal vectors at each pixel. Because of this, the longest path skeletons should be used. Or individual branches, though the usefulness of short branches is limited (the first and last few pixels are skipped due to how the normal vector is found).

This addition allows investigation of how the profiles change along the filament extent. Exploring these properties are key to understanding how filament properties change near cores (presumably linear mass density here is gravitationally unstable) to the faint 'striations' (magnetically-mediated support?). With spectroscopic info, the nature of the flows can also be explored with the changing profiles, similar to what was done by [Liu et al (2016)][liu_paper] (which is also the first external publication to make use of FilFinder!). 

I've added a [new example script][example_script] for how to use the code, based on the same simulated data used in the rest of the [FilFinder tutorial][tutorial]. Here is an example profile (from one of the less crowded regions):

![Pretty profile!]({{ site.url }}/images/sim_filament_profile_041616.png)

The asymmetry in the profile looks quite interesting, and since the simulated data is simply a turbulent box, is likely due to supersonic shocks. Cool! Modeling this effect, and minimizing the influence of unassociated filaments in crowded regions, are the next goals to address for this new addition to the code base.

Bugs and issues with FilFinder can be reported on [GitHub][issues].


[filfinder_repo] : https://github.com/e-koch/FilFinder
[example_script] : https://github.com/e-koch/FilFinder/blob/master/examples/example_filament_profile.py
[tutorial] : http://fil-finder.readthedocs.org/en/latest/tutorial.html
[liu_paper] : http://adsabs.harvard.edu/abs/2016arXiv160403548L
[issues] : https://github.com/e-koch/FilFinder/issues