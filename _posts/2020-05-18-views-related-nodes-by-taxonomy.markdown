---
layout: blog
title:  "Drupal 8 related taxonomy contextual filter on nodes for a views block"
date:   2020-05-18 00:00:01 -0500
categories: posts
excerpt_separator: <!-- more -->
permalink: drupal/drupal-8-related-taxonomy-coutextual-filter-node-views-block.html
---
<p>
For 2 nodes labeled with the same taxonomy, configure a block to show content tagged with that taxonomy.
Example: If you have a node tagged with the taxonomy shirts and you want to show a block that would display a related shirt.
Create a block to display related content tagged by taxonomy using views.</p>

<!-- more -->

<p>
Create a block view with the appropriate Filter Criteria: Content Type etc...
<b>Under the Advanced menu add two contextual filters.</b></p>
<img src="/images/views-contextual-filters/drupal-related-taxonomy-contextual-filter.jpg">

<img src="/images/views-contextual-filters/id-contextual-filter-drupal.jpg">

    
- Contextual Filters - Content: ID</lh>
- Select provide a default value and choose Content ID from URL.<p class="gray">this does what it does</p></li>
- Under More tab - Check next to Exclude<p class="gray">this does what it does</p></li>
    



<img src="/images/views-contextual-filters/views-contextual-filter-content-id.jpg">



- Contextual Filter - Content: Has taxonomy term ID
- When filter is not available - Provide a default value - Taxonomy term ID from url
- Uncheck, load default filter from term page
- Check, Load default filter from node page, that's good for related taxonomy block
- Multiple value handling:&nbsp;<strong>Filter to items that share any value</strong>
- Check, Reduce Duplicates
- Under more tab check:&nbsp;<strong>Allow multiple values</strong>&nbsp;and&nbsp;<strong>Allow multiple values to work together.</strong>


<img src="/images/views-contextual-filters/taxonomy-term-views-contextual-filter.jpg">

<h4>Result:</h4>

Now I have 2 nodes that are labeled with the same taxonomy as the node being viewed as a footer.

<img src="/images/views-contextual-filters/related-nodes-drupal-taxonomy-views.jpg">