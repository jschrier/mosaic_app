An experiment revisiting my [mosaic material calculator](https://jschrier.github.io/blog/2025/01/19/Estimating-mosaic-material-costs-from-an-image.html) but using [OpenAI Codex CLI](https://developers.openai.com/codex/cli/features/) with `gpt-5.2-codex` to create it as an HTML single-page app.  This took about $0.90 of API credits to generate through a few back and forth iterations.    

# See the results

Deployed via [Github pages](https://docs.github.com/en/pages) as [https://jschrier.github.io/mosaic_app](https://jschrier.github.io/mosaic_app)

# Input prompts 

(Rendered from the session log using [conex-timeline](https://tools.simonwillison.net/codex-timeline) )

```
<environment_context>
  <cwd>/Users/jschrier/Documents/GitHub/mosaic_app</cwd>
  <shell>bash</shell>
</environment_context>

Create an HTML5 single-page application that has the following capabilities: 1. Use

1. Allow user to drag/drop an image from their local computer; 2. Specify the area (width and height) that the image should occupy; 3. Compute the fraction of pixels of each color in the image ; 4. Display the fraction and the images in a list.  For reference consider https://jschrier.github.io/blog/2025/01/19/Estimating-mosaic-material-costs-from-an-image.html showing a possible implementation in another language

This is on the right track. Make the following modifications: 1. Add a slider that allows the user to control the color quantization (top N). 2. Change the height and width inputs to be in feet; 3. When a user selects a color, it will be highlighted in the image (dims or grays out all other colors that are not that pixel; 4. Add a "kg/square foot" input box, with the default setting of 1.5; 5. Compute an additional column int ehd data table that multiplies the fraction of pixels of the color times the area (height x width) times the "kg/square foot" numerical entry; 5. At the bottom of the column, include a total which is the sum of the masses

Add a "Recalculate" button  near the data entry panel which will keep the loaded image, but recompute the entries in the data table when the user enters a new width, height, kg/square foor or quantization choice.  Better yet: If it is possible to recalculate this on the fly any of those boxes are changed then do that.

Reimplement the quantization.  Pixels whose euclidean distance (in RGB space) are within 0.01 should be lumped together for the display.

No, revert the last change.

Adjust the UI.  Keep the image with color hilighting, but also add another version of this which shows only the highlighted color on a neutral (white) background.  Both of these images get updated when a color is selected.
```