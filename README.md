# Countdown.js

This plugin let you add a countdown timer to your reveal.js presentations

## Usage

Using the plugin is easy. First, register it in your Reveal.js initialize block.

```javascript
    // Old reveal versions
    Reveal.initialize({
        dependencies: [
            ....
          { src: "plugin/countdown/countdown.js" },

        ],
        countdown: { defaultTime: 600, autostart: "no" }
      });


// New reveal versions 
  Reveal.configure({
    ...
    countdown: {
      defaultTime: 900,
      autostart: "no",
      tDelta: 60,
      playTickSoundLast: 10,
      tickSound: "http://soundbible.com/grab.php?id=2044&type=mp3",
      timeIsUpSound: "http://soundbible.com/grab.php?id=1746&type=mp3"
    }
  })
  
  Reveal.registerPlugin(RevealCountDown)
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

- defaultTime: Default time for a timer if no time is given as attribute to <countodwn/>
- autostart: yes/no wether a timer should auotstart or not when the slide with timer loads
- tDelta: nr of seconds to increase decreas when pressing '+' and '-' key.
- tickSound: Sound to play every second for the last X seconds.
- timesUpSound: Sound to play when the time is up.

```javascript
    countdown: {
      defaultTime: 600,
      autostart: "no",
      tDelta: 60,
      playTickSoundLast: 10,
      tickSound: "http://soundbible.com/grab.php?id=2044&type=mp3",
      timeIsUpSound: "http://soundbible.com/grab.php?id=1746&type=mp3",
      plusKey: 171, //SPANISH keyboard
      minusKey: 173 //SPANISH keyboard
    }
```

defaults are:

```javascript
{
  defaultTime: 300,
  autostart: "no",
  tDelta: 30,
  playTickSoundLast: 10,
  tickSound: "",
  timeIsUpSound: "",
  plusKey: 187,
  minusKey: 189
}
```


## Integration with Custom Controls plugin

You can integrate it with the custom control plugin

```javascript
  Reveal.configure({
    customcontrols: {
      controls: [
        {
          icon: '<i class="fas fa-hourglass-start"></i>',
          title: 'Pause/Unpause timer (T)',
          action: 'RevealCountDown.togglePauseTimer()'
        }
      ]

    countdown: {
      defaultTime: 900,
      autostart: "no",
      tDelta: 60,
      playTickSoundLast: 10,
      tickSound: "http://soundbible.com/grab.php?id=2044&type=mp3",
      timeIsUpSound: "http://soundbible.com/grab.php?id=1746&type=mp3"
    }
  })
  
  const params = new URLSearchParams(window.location.search);
  if (! params.has("print-pdf")) {
    Reveal.registerPlugin(RevealCustomControls)
  }
  Reveal.registerPlugin(RevealCountDown)

```