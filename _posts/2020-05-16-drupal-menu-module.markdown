---
layout: blog
title:  "Taxonomy Menu Add Class Attributes Module"
date:   2020-05-16 00:00:19 -0500
categories: posts
excerpt_separator: <!-- more -->
---

I needed a menu based on a taxonomy for a high level sorting of blog posts. I generated a menu using the <a href="https://www.drupal.org/project/taxonomy_menu">Taxonomy Menu</a> module.
This module will add an active trail based on the taxonomy term on the node.

<!-- more -->

{% highlight php %}

/**
* Implements hook_preprocess_menu().
*/

function coupa_8_preprocess_(menu_id)(&$variables, $hook) {
  $node = \Drupal::routeMatch()->getParameter('node');
  if ($node instanceof \Drupal\node\NodeInterface) {
    $nid = $node->id();
    $node_storage = \Drupal::entityTypeManager()->getStorage('node');
    $node = $node_storage->load($nid);
    if($node->getType() == 'blog') {
      $node_target_tid = $node->get('field_content_tags')->target_id;
      if ($node_target_tid != NULL) {
        $items = ($variables['items']);
        foreach ($items as &$item) {
          $menu_id = $item['url']->getRouteParameters();
          if ($node_target_tid == $menu_id['taxonomy_term']) {
            $item['attributes']->addClass('menu-item--active-trail');
          }
        }
      }
    }
  }
}
{% endhighlight %}

Check to see if page is a node.

{% highlight php %}
$node = \Drupal::routeMatch()->getParameter('node');
if ($node instanceof \Drupal\node\NodeInterface) {
  $nid = $node->id();
}
{% endhighlight %}

Load the node.

{% highlight php %}

$node_storage = \Drupal::entityTypeManager()->getStorage('node');
$node = $node_storage->load($nid);

{% endhighlight %}

Check if the node is a blog post.

{% highlight php %}

 if($node->getType() == 'blog') {}

{% endhighlight %}

Load the taxonomy ID of the node. This taxonomy is limited to 1 value.<br/>
use ->target_id method to get the taxonomy ID.

{% highlight php %}

$node_target_tid = $node->get('field_content_tags')->target_id;

{% endhighlight %}

Iterate through the menu items. 

{% highlight php %}

$items = ($variables['items']);
foreach ($items as &$item) {
   $menu_id = $item['url']->getRouteParameters();
}

{% endhighlight %}

Add active trail with ->addClass method.

{% highlight php %}

if ($node_target_tid == $menu_id['taxonomy_term']) {
$item['attributes']->addClass('menu-item--active-trail');
}

{% endhighlight %}
