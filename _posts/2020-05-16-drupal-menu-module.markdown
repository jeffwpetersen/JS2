---
layout: blog
title:  "Menu modification module"
date:   2020-05-16 00:00:19 -0500
categories: posts
excerpt_separator: <!-- more -->
---

Module stuff

<!-- more -->

<pre>
{% highlight php %}

function hook_preprocess_menu__blog_term_menu(&$variables, $hook) {
  $node = \Drupal::routeMatch()->getParameter('node');
  if ($node instanceof \Drupal\node\NodeInterface) {
    $nid = $node->id();
    $node_storage = \Drupal::entityTypeManager()->getStorage('node');
    $node = $node_storage->load($nid);
    $node_target_tid = $node->get('field_content_tags')->target_id;
    if($node_target_tid != NULL ) {
      $items = ($variables['items']);
      foreach ($items as &$item) {
        $menu_id = $item['url']->getRouteParameters();
        if ($node_target_tid == $menu_id['taxonomy_term']) {
          $item['attributes']->addClass('active-category');
        }
      }
    }
  }
}
{% endhighlight %}

</pre>