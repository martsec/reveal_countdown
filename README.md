# Countdown.js

This plugin let you add a countdown timer to your reveal.js presentations

## Usage

Using the plugin is easy. First, register it in your Reveal.js initialize block.

```javascript

    Reveal.initialize({
        dependencies: [
            ....
          { src: "plugin/countdown/countdown.js" },

        ],
        countdown: { defaultTime: 600, autostart: "no" }
      });

```

Then simply add an element into your presentation:

```html
<section>
  <h1>5 minutes timer</h1>
  <countdown time="300" autostart="yes" />
</section>
```

### Pause/Resume

The defult keybinding to toggle pause/resume the timer is **t**

The timer will also pause when th epresentation is paused by pressing the period dot.

### increase Decrease counter time

Use the **+** and **-** keys to increment decrement timer with tDelta seconds. tDelta can be configured as seen in the next section.

## Configuration

The plugin can be configured with default values and settings in the initialize function:

```javascript
    countdown: { defaultTime: 600, autostart: "no", tDelta: 60 }
```

defaults are:

```javascript
{
  defaultTime: 300,
  autostart: "no",
  tDelta: 30
}
```
