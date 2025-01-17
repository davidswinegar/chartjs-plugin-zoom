# chartjs-plugin-zoom

A zoom and pan plugin for Chart.js. Currently requires Chart.js >= 2.6.0

Panning can be done via the mouse or with a finger.
Zooming is done via the mouse wheel or via a pinch gesture. [Hammer.js](https://hammerjs.github.io/) is used for gesture recognition.

[Live Codepen Demo](https://codepen.io/pen/PGabEK)

## Installation

Run `npm install --save chartjs-plugin-zoom` to install with `npm`.

If including via a `<script>` tag, make sure to include `Hammer.js` as well:

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
<script src="https://cdn.jsdelivr.net/npm/hammerjs@2.0.8"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-zoom@0.7.0"></script>
```

## Configuration

To configure the zoom and pan plugin, you can simply add new config options to your chart config.

```javascript
plugins: {
	zoom: {
		// Container for pan options
		pan: {
			// Boolean to enable panning
			enabled: true,

			// Panning directions. Remove the appropriate direction to disable
			// Eg. 'y' would only allow panning in the y direction
			mode: 'xy',
			rangeMin: {
				// Format of min pan range depends on scale type
				x: null,
				y: null
			},
			rangeMax: {
				// Format of max pan range depends on scale type
				x: null,
				y: null
			},
			// Function called once panning is completed
			// Useful for dynamic data loading
			onPan: function({chart}) { console.log(`I was panned!!!`); }
		},

		// Container for zoom options
		zoom: {
			// Boolean to enable zooming
			enabled: true,

			// Enable drag-to-zoom behavior
			drag: true,

			// Drag-to-zoom rectangle style can be customized
			// drag: {
			// 	 borderColor: 'rgba(225,225,225,0.3)'
			// 	 borderWidth: 5,
			// 	 backgroundColor: 'rgb(225,225,225)'
			// },

			// Zooming directions. Remove the appropriate direction to disable
			// Eg. 'y' would only allow zooming in the y direction
			mode: 'xy',

			// Optional function for disabling the enabled mode, given an event.
			// Allows disabling modes based on other keyboard properties.
			// Ex. disabling the 'y' direction when a particular key is pressed.
			// event: nullable DOM event
			// direction: 'x' or 'y'
			isModeEnabledOverrideFn: (event, direction) => true,

			rangeMin: {
				// Format of min zoom range depends on scale type
				x: null,
				y: null
			},
			rangeMax: {
				// Format of max zoom range depends on scale type
				x: null,
				y: null
			},

			// Speed of zoom via mouse wheel
			// (percentage of zoom on a wheel event)
			speed: 0.1,

			// Function called once zooming is completed
			// Useful for dynamic data loading
			onZoom: function({chart}) { console.log(`I was zoomed!!!`); }
		}
	}
}
```

## API

### chart.resetZoom()

Programmatically resets the zoom to the default state. See [samples/zoom-time.html](samples/zoom-time.html) for an example.

## Installation

To download a zip, go to the chartjs-plugin-zoom.js on Github

To install via npm / bower:

```bash
npm install chartjs-plugin-zoom --save
```

Prior to v0.4.0, this plugin was known as 'Chart.Zoom.js'. Old versions are still available on npm under that name.

## Documentation

You can find documentation for Chart.js at [www.chartjs.org/docs](https://www.chartjs.org/docs).

Examples for this plugin are available in the [samples folder](samples).

## Contributing

Before submitting an issue or a pull request to the project, please take a moment to look over the [contributing guidelines](CONTRIBUTING.md) first.

## License

chartjs-plugin-zoom.js is available under the [MIT license](https://opensource.org/licenses/MIT).
