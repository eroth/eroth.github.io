---
date: 2013-09-16 13:45:31+00:00
title: iOS project to simulate hydrodynamic flow using GPUs
header:
  image: /assets/images/posts/2013-09-16-ios-project-to-simulate-hydrodynamic-flow-using-gpus/ios-gpu-post-feature.png
teaser_image_path: /assets/images/posts/2013-09-16-ios-project-to-simulate-hydrodynamic-flow-using-gpus/teaser.png
tags:
  - iOS
  - GPU
  - OpenGL
---

This is a really interesting project I came across recently!

[http://rnd.azoft.com/fluid-dynamics-simulation-on-ios/](http://rnd.azoft.com/fluid-dynamics-simulation-on-ios/)

Vladimir Tchernitski from Azoft took physics equations that model hydrodynamic flow, and used OpenGL and the GPU to perform the calculations—as to do so using the CPU would have been too labor-intensive.  In this case, they developed a framework that models the dispersion of paint across the surface of an iPad.

Really great results:

{% include video id="2syPAIfY6R4" provider="youtube" %}

In addition, the article provides a great background about OpenGL and GPU-programming!
