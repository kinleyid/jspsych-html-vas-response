# jspsych-html-vas-response plugin

This plugin collects responses to an arbitrary HTML string using a point-and-click visual analogue scale.

## Citation

Kinley, I. (2022, March 7). "A jsPsych plugin for visual analogue scales." Retrieved from psyarxiv.com/avj92. DOI: 10.31234/osf.io/avj92

## Parameters

In addition to the [parameters available in all plugins](https://www.jspsych.org/overview/plugins#parameters-available-in-all-plugins), this plugin accepts the following parameters. Parameters with a default value of *undefined* must be specified. Parameters can be left unspecified if the default value is acceptable.

| Parameter                | Type             | Default Value        | Descripton                               |
| ------------------------ | ---------------- | -------------------- | ---------------------------------------- |
| stimulus                     | HTML string           | `undefined`     | The string to be displayed. |
| labels                     | array of strings           | `[]`     | Specifies the labels to be displayed, equally spaced along the scale, as in jspsych-html-slider-response. |
| ticks                     | Boolean           | `true`     | Specifies whether smaller vertical tick marks should accompany the labels. |
| scale_width | integer | `null` |  The width of the VAS in pixels. If left null, then the width will be equal to the widest element in the display. |
| scale_height | integer | 40 | The height of the clickable region around the VAS in pixels. |
| scale_colour | string | `'black'` | The colour of the scale (the horizontal line). Anything that would make a valid CSS `background` property can be used here; e.g., `'linear-gradient(to right, blue, red)'` |
| scale_cursor | string | `'pointer'` | The style of the cursor when the clickable part of the scale is hovered over. |
| marker_colour | string | `'rgba(0, 0, 0, 0.5)'` | The colour of the participant's response marker. Anything that would make a valid CSS `background` property can be used here; e.g., `'linear-gradient(to top, blue, red)'` |
| tick_colour | string | `'black'` | The colour of the tick marks on the scale. Anything that would make a valid CSS `background` property can be used here; e.g., `'rgba(255, 0, 0, 0.8)'` |
| prompt | HTML string | `null` | The content to be displayed below the stimulus. |
| button_label | string | `'Continue'` | The text of the button that will submit the response. |
| required | Boolean | `false` | If `true`, the participant must select a response on the VAS before the trial can advance. |
| stimulus_duration | integer | `null` | The duration, in milliseconds, for which the stimulus is visible. If `null`, the stimulus is visible for the duration of the trial. |
| trial_duration | integer | `null` | The duration of the trial, in milliseconds. Once this time elapses, the trial ends and any response is recorded. If `null`, the trial continues indefinitely. |
| response_ends_trial | Boolean | `true` | If `false`, the participant's clicking the continue button does not end the trial (but does prevent any changes to the VAS response), and the trial ends when `trial_duration` has elapsed. |

## Data Generated

In addition to the [default data collected by all plugins](https://www.jspsych.org/overview/plugins#data-collected-by-all-plugins), this plugin collects all parameter data described above and the following data for each trial.

| Name             | Type        | Value                                    |
| ---------------- | ----------- | ---------------------------------------- |
| response             | numeric      | The value selected, between 0 and 1. 0 is the leftmost point on the scale, 1 is the rightmost point, and 0.5 is exactly in the middle. |
| rt            | numeric     | The time in milliseconds, between when the trial began and when the paticipant clicked the continue button. |
| stimulus          | string     | The stimulus displayed during the trial. |

## Example

```javascript
var trial = {
  type: jsPsychHtmlVasResponse,
  stimulus: 'What is your temperature?',
  scale_width: 500,
  labels: ['Maximally<br>cold', 'Maximally<br>hot']
};
```