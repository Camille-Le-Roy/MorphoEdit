---
layout: post
title: "How to make your scientific figures publication-ready (6 tips)"
description: "My compilation of figure design tips to turn raw data plots into clean, publication-ready figures for peer-reviewed journals."
keywords: "scientific figures, publication-ready figures, manuscript figures, data visualization, figure design"
date: 2026-09-12
---

<style>
  :root {
    /* Adjust this value to change baseline desktop body/paragraph font size */
    --body-font-size: 1.1em;
  }

  /* Article body text formatting */
  article {
    font-size: var(--body-font-size);
    line-height: 1.8;
    color: #2c3e50;
  }
  
  article p {
    font-size: var(--body-font-size);
    margin-bottom: 1.5em;
  }

  /* Headings formatting */
  article h1, article h2, article h3 {
    text-transform: none !important;
    font-family: 'Montserrat', sans-serif;
    color: #3F6E93;
    font-weight: 700;
  }

  article h2 {
    margin-top: 2.2em;
    margin-bottom: 0.8em;
    font-size: 1.45em;
    border-bottom: 2px solid #f0f0f0;
    padding-bottom: 8px;
  }

  /* Figure and Image Containers */
  .post-figure {
    margin: 2.5em auto;
    text-align: center;
    background: transparent;
    padding: 0;
    border: none;
    box-sizing: border-box;
  }

  .post-figure.intro-fig {
    width: 75%;   /* Intro image size */
  }

  .post-figure.content-fig {
    width: 65%; /* Figure 1 and 2 size */
  }

  .post-figure.small-fig {
    width: 35%; /* Figure 3 size on desktop */
  }

  .post-figure img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    object-fit: contain;
    box-shadow: none !important;
  }

  .post-caption {
    color: #666;
    font-size: 0.85em;
    line-height: 1.5;
    margin-top: 14px;
    text-align: left;
    max-width: 95%;
    margin-left: auto;
    margin-right: auto;
  }

  /* Call-to-action box without left border */
  .cta-card {
    background-color: #f4f7f9;
    border: none;
    padding: 24px;
    border-radius: 8px;
    text-align: center;
    margin-top: 3em;
    font-size: var(--body-font-size);
  }

  .cta-card a {
    color: #3F6E93;
    font-weight: 700;
    text-decoration: underline;
  }

  /* Responsive Rules for Mobile Devices */
  @media (max-width: 768px) {
    :root {
      --body-font-size: 1.05em; /* Slightly tighter font for small displays */
    }

    /* Reduce post title size on mobile */
    article h1 {
      font-size: 1.6em !important; /* Adjust this value if you want it smaller/larger */
      line-height: 1.25;
      margin-bottom: 15px;
    }

    /* Expand all figure variants to full width on mobile */
    .post-figure.intro-fig,
    .post-figure.content-fig,
    .post-figure.small-fig {
      width: 100% !important;
      padding: 0;
      margin: 1.8em auto;
    }

    .post-caption {
      max-width: 100%;
      font-size: 0.9em;
    }
  }
</style>

<!-- Intro Visual -->
<div class="post-figure intro-fig" style="margin-top: 1em;">
  <img src="{{ site.baseurl }}/img/blogpost_1 intro visual.png" alt="Before and after example of a publication-ready scientific figure">
  <div class="post-caption" style="text-align: right; font-size: 0.70em;">
    Example figure from: 
    <a href="https://doi.org/10.1038/s41467-021-27549-1" target="_blank" style="color: inherit;">
      Le Roy et al. (2021) <em>Nat. Commun.</em> 12(1): 7248.
    </a>
  </div>
</div>

<p style="font-size: calc(var(--body-font-size) * 1.25); color: #3F6E93; font-weight: 700;">
Have you ever stared at a published figure and thought: <em>how did they make it look that good?</em>
</p>

<p>
No one actually nails a polished figure on the first try. The road from your slightly - or really - ugly plot fresh out of R to a polished figure often takes many trials and intermediary versions. Drawing on my own research experience, I’ve compiled six practical tips I always use to make figures clearer and impactful, helping you reach that final, publishable version.
</p>

## 1. One figure, one message

Just like a paragraph, a figure loses power when it tries to say too much at once. When deciding what to combine into panels, think about the figure legend you'll write, and how it will guide the reader through the story. If including multiple panels, they should reflect different elements of the same overall message. The order of your panels matters a lot: if panel A shows a pattern that raises a question, panel B can answer it, thereby satisfying the reader's expectation.

## 2. Make color meaningful and consistent

We all have an inner artist wanting to make figures colorful. Try to channel that urge. If a figure doesn't need color, it's completely fine to keep it in shades of grey. That spares the reader the distracting thought of <em>"what do these colors mean?"</em>.

When you do use color, make sure it carries information: different colors for categories of a variable, or a gradient for a continuous one, in an intuitive direction (warmer = higher temperature, for instance). Also revise your color coding across the whole manuscript: if three colors represent your three treatment conditions in your first figure, keep those same three colors in every figure after that. Finally, it's good practice to pick a colorblind-friendly palette from the start (see <a href="https://journal.r-project.org/articles/RJ-2023-071/" target="_blank" style="color: #3F6E93;">R Journal Palette Guide</a>).

<!-- Figure 1 -->
<div class="post-figure content-fig">
  <img src="{{ site.baseurl }}/img/blogpost_1 consistent color coding.png" alt="Example of consistent color coding across a manuscript">
  <div class="post-caption">
    <strong>Figure 1:</strong> Example of consistent color coding across an article: green indicates forest-dwelling butterflies, blue indicates butterflies from open habitats. Original article: 
    <a href="https://doi.org/10.1242/jeb.243867">Le Roy et al. (2022) <em>J. Exp. Biol.</em> 225(15): jeb243867.</a>
  </div>
</div>

## 3. Layer information by combining color, shape, and size

Journal space is limited, and you probably have more interesting results than room to show them. Keep your figure's main message pointed in one direction, but you can layer in extra information through point color, shape (<code style="color: inherit;">pch</code> in R, <code style="color: inherit;">marker</code> in Python), and size. For example, in the scatterplot below (Figure 2), point size reflects wingbeat frequency while color gradient captures body mass — enriching the core aerodynamic relationship without cluttering the display. We could even layer in sex by using distinct point shapes.

<!-- Figure 2 -->
<div class="post-figure content-fig">
  <img src="{{ site.baseurl }}/img/blogpost_1 points shape and size.png" alt="Example of combined color, size, and inset panel usage">
  <div class="post-caption">
    <strong>Figure 2:</strong> Combining color and point size to convey multiple layers of information: here color reflects body mass, while point size indicates wingbeat frequency. Small inset panels show an additional analysis without adding extra panels. Original article: 
    <a href="https://doi.org/10.1371/journal.pbio.3003473">Le Roy et al. (2026) <em>PLoS Biol.</em> 24(7): e3003473.</a>
  </div>
</div>

## 4. Resize panels based on how much they need to say

If one of your plots is dead simple to interpret, it may only need two tick marks (say, 0 and the max value) and bigger points. Just shrink it. Doing so will free up space for the panels that are more complex and require more interpretive work. Varying panel sizes helps establish hierarchy. It guides the reader’s eye to your primary takeaways and keeps complementary details in supporting roles (see the use of the inset panel in Figure 2 for example).

## 5. Edit your figure outside of R or Python

If you love tweaking axis fonts and border thickness in code, you may disagree with this one. But a fully coded approach tends to feel rigid. My preferred approach: build the core figure in your coding environment, then export it as a vector file (PDF or EPS) and finish the polish in design software (Illustrator, Affinity Designer, Inkscape). Vector format also means infinite scalability — your figure looks equally beautiful as a tiny panel or blown up on a poster. That said, if you're in a rush or prefer to avoid learning design tools, even basic tweaks in PowerPoint can significantly improve your raw figure.

Editing "by hand" lets you adjust almost anything (except the data, of course): element size and position, consistent fonts across panels, and refining colors. You can even draw custom schematics or illustrations to convey complementary details (see Figure 2A). Together, these small adjustments are what actually shape how clearly your result reads.

<!-- Figure 3 -->
<div class="post-figure small-fig">
  <img src="{{ site.baseurl }}/img/blogpost_1 redundant axis.png" alt="Example of minimalist axis tick marks and removing redundant axes">
  <div class="post-caption">
    <strong>Figure 3:</strong> Remove duplicate axes across panels and keep tick marks to a functional minimum. <br> Original article: 
    <a href="https://www.science.org/doi/10.1126/science.1248955" target="_blank" style="color: inherit; text-decoration: underline;">
      Muijres et al. (2014) <em>Science</em>, 344(6180): 172–177.
    </a>
  </div>
</div>

## 6. Find what's unnecessary, and cut it!

You have a figure that's correct and interpretable with some effort. Now ask yourself: <em>what result do I actually want this to convey, and what's standing in the way? </em>&nbsp;Usually, you can easily spot elements to cut, such as:

<ul style="margin-bottom: 1.5em; padding-left: 1.2em; color: #444;">
  <li>Unnecessary frames or heavy outer borders</li>
  <li>Redundant axis or labels</li>
  <li>Overcrowded tick marks</li>
  <li>Large empty spaces breaking up your panel flow</li>
</ul>

Remove all of this! Let the essential message reach your reader's eye as directly as possible.

<div class="cta-card">
  Stuck translating messy data into a clear scientific story?<br> Feel free to 
  <a href="https://tidycal.com/camilleleroy/free-15-minute-call" target="_blank">book a free 15-minute call</a> 
  or send a message via the <a href="https://camille-le-roy.github.io/MorphoEdit/#contact" target="_blank">contact form</a>.<br> We can discuss how to streamline your figures or manuscript!
</div>