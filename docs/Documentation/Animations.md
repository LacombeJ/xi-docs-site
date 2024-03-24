---
title: Animations
layout: page
parent: Documentation
---

# Animations

####  Delayed Style Update
Styles are not updated immediately after changing class list, so in order to
detect changes, each value that is transitionable is read and recorded on update
and when changed from a previous value, will trigger an animation.

#### Intermediate Animation Change
Remember, animations can re-occur in the middle of a transition, switching from an
intermediate value to another target. In these cases, the animation needs to know
where to "pick up" from so that it can continue a smooth transition while using
the appropriate easing function and an expected duration.
The solution used here will be to determine "location" within animation from the
current value relative to the source and target value. This location will be used
only to determine how much time is left for the animation. (Not sure if this is
the best, but it's the only alternative I can think of besides finding inverses
for all easing functions)
