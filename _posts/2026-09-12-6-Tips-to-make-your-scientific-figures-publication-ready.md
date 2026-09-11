---
layout: post
title: "Six tips to make your scientific figures publication-ready"
date: 2026-09-11
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
    width: 70%; /* Figure 1 size */
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

  /* Call-to-action box */
  .cta-card {
    background-color: #f4f7f9;
    border-left: 4px solid #3F6E93;
    padding: 24px;
    border-radius: 0 8px 8px 0;
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

    .post-figure.intro-fig,
    .post-figure.content-fig {
      width: 100%; /* Stretch figures to full width on mobile */
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
  <div class="post-caption" style="text-align: center;">
    Example figure from: Le Roy et al. (2021) Nat. Commun. 12(1): 7248
  </div>
</div>

<p style="font-size: calc(var(--body-font-size) * 1.25); color: #3F6E93; font-weight: 700;">
Have you ever stared at a published figure and thought: <em>how did they make it look that good?</em>
</p>

<p>
The truth is that no one nails a polished figure on the first try. The road from your slightly ugly plot fresh out of R to that perfected version can be long, full of dead ends, trial, and error. Built from my research experience, here I’ve compiled six practical tips that I personally follow all the time, which can greatly improve the impact of your manuscript.
</p>

## 1. One figure, one message

Just like a paragraph, a figure loses power when it tries to say too much at once. When deciding what to combine into panels, think about the figure legend you'll write, and how it will guide the reader through the story. If including multiple panels, they should reflect different elements of the same overall message. The order of your panels matters a lot: if panel A shows a pattern that raises a question, panel B can answer it, hence satisfying the reader's expectation.

## 2. Make color meaningful and consistent

We all have an inner artist wanting to make figures colorful. Try to channel that urge. If a figure doesn't need color, it's completely fine to keep it in shades of grey. That spares the reader the distracting thought of <em>"what do these colors mean?"</em>.

When you do use color, make sure it carries information: different colors for categories of a variable, or a gradient for a continuous one, in an intuitive direction (warmer = higher temperature, for instance). Also revise your color coding across the whole manuscript: if three colors represent your three treatment conditions in your first figure, keep those same three colors in every figure after that. Finally, it's good practice to pick a colorblind-friendly palette from the start (see <a href="https://journal.r-project.org/articles/RJ-2023-071/" target="_blank" style="color: #3F6E93; font-weight: 600;">R Journal Palette Guide</a>).

<!-- Figure 1 -->
<div class="post-figure content-fig">
  <img src="{{ site.baseurl }}/img/blogpost_1 consistent color coding.png" alt="Example of consistent color coding across a manuscript">
  <div class="post-caption">
    <strong>Figure 1:</strong> Example of color consistency across an article. Here, green indicates butterflies living in the forest while blue indicates butterflies living in open habitat. Original article: Le Roy et al. (2022) J. Exp. Biol. 225(15): jeb243867.
  </div>
</div>

## 3. Layer information by combining color, shape, and size

Journal space is limited, and you probably have more interesting results than room to show them. Keep your figure's main message pointed in one direction, but you can layer in extra information through point color, shape (<code>pch</code> in R, <code>marker</code> in Python), and size. For example: a scatterplot of your two key variables, colored by species, shaped by sex, and sized by body mass. This gives you three extra dimensions of information while keeping the story in one clean plot.

<!-- Figure 2 -->
<div class="post-figure content-fig">
  <img src="{{ site.baseurl }}/img/blogpost_1 points shape and size.png" alt="Example of combined color, size, and inset panel usage">
  <div class="post-caption">
    <strong>Figure 2:</strong> Combined use of color and size to convey several layers of information without overcrowding the figure. Here, the color gradient reflects variation in body mass and point size indicates wingbeat frequency. These additional layers of information are juxtaposed in the scatterplots. Note the use of a small inset in the bottom right of each panel, showing an additional analysis without adding extra panels. Original article: Le Roy et al. (2026) PLoS Biol. 24(7): e3003473.
  </div>
</div>

## 4. Resize panels based on how much they need to say

If one of your plots is dead simple to interpret, it may only need two tick marks (say, 0 and the max value) and bigger points. Just shrink it. Doing so will free up space for the panels that are more complex and require more interpretive work. Varying panel sizes helps establish hierarchy. It guides the reader’s eye to your primary takeaways and keeps complementary details in supporting roles (see the use of the inset panel in Figure 2 for example).

## 5. Edit your figure outside of R or Python

If you love tweaking axis fonts and border thickness in code, you may disagree with this one. But a fully coded approach tends to feel rigid. My preferred approach: build the core figure in your coding environment, then export it as a vector file (PDF or EPS) and finish the polish in design software (Illustrator, Affinity Designer, Inkscape, or even PowerPoint!). Vector format also means infinite scalability — your figure looks equally sharp as a tiny panel or blown up on a poster.

Editing "by hand" lets you adjust almost anything (except the data, of course): element size and position, consistent fonts across panels, and refining colors. You can even draw custom schematics or illustrations to convey complementary details. Together, these small adjustments are what actually shape how clearly your result reads.

## 6. Find what's unnecessary, and cut it!

You have a figure that's correct and interpretable with some effort. Now ask yourself: <em>what result do I actually want this to convey, and what's standing in the way?</em> Usually, you can easily spot things like an unnecessary frame, overcrowded tick marks, repeated axis labels across panels, big empty spaces, or heavy, ugly borders. Remove all of this! Let the essential message reach your reader's eye as directly as possible.

<div class="cta-card">
  If you're stuck turning messy results into a figure (or a full manuscript) that tells a clear story, 
  <a href="https://tidycal.com/camilleleroy/free-15-minute-call" target="_blank">
    book a free 15-minute call
  </a> — I'd love to help you get unstuck.
</div>