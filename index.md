---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: home
---

<script>
  if (navigator.serviceWorker) {
    navigator.serviceWorker.register('/sw.js').then(function(registration) {
    }).catch(function(error) {
      console.log('ServiceWorker registration failed', error);
    });
  };
</script>