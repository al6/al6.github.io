# [Live Site](https://albertlee.io "My website homepage")

This is my personal site, built with HTML5Up's Prologue Template found [here](https://html5up.net/prologue "HTML5UP Prologue Website Template")

There was one minor bug that I didn't want to fix but it bugged me enough to fix after all (ba dum tss! I'm sorry).
When you click on one of the navigation links to scroll to a different part of the page, the other nav buttons flicker and the wrong ones get toggled occasionally, even in the template's live demo.

I spent more time fixing this bug than I want to admit, so here's the code in case you want to fix the same bug, located in the main.js file.

## main.js file (abridged from original)

```javascript
(function($) {
  ...
  $nav_a
    ...
    .on("click", function(e) {
      ...
      // Deactivate and unlock all links.
      $nav_a.removeClass("active");
      $nav_a.removeClass("active-lock");
      ...
    })
    .each(function() {
      ...
      $section.scrollex({
        ...
        // Adjusted top and bottom values to account for different page lengths
        top: "-3vh",
        bottom: "-3vh",
        initialize: function() {
          ...
        },
        enter: function() {
          ...
          //DELETE BELOW COMMENTED LINES
          // Otherwise, if this section's link is the one that's locked, unlock it.
					// else if ($this.hasClass('active-locked'))
					// $this.removeClass('active-locked');
        }
      });
    });
...
})(jQuery);
```
