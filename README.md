# WIP 
<https://github.com/chavinlo/musicgen_trainer> implementations:

- Load previously trained .pt model and use it with the correct model (small, medium, large)> **Done**
- Training UI/Tab> **WIP**
- Progress bar
- Parameters presets selection
- Music visualiser

# audiocraft-webui![UI_sample](https://github.com/FeelTheFonk/audiocraft-webui/assets/134219563/4eb1ac3d-d4e7-4a79-9273-d9878b0f685e)

Local webui for Facebook's Audiocraft model: <https://github.com/facebookresearch/audiocraft>


## Features:

- **Long Audio**: Make audio as long as you like.
- **Segmented audio**: Generate audio in segments (potentially faster than longer audio)
- **Processing Queue**: Add as many different prompts to the processing queue as you like, go have a cup of coffee, come back to sweet sweet audio.

- **Segmented Prompting**: *On the gradio version <https://github.com/CoffeeVampir3/audiocraft-webui/tree/gradio-version>* Use multiple different prompts per audio segment.

## Install:

If you'd like gpu acceleration and do not have torch installed, visit https://pytorch.org/get-started/locally/ for instructions on installing gpu torch correctly.

`pip install -r requirements.txt`
(If you encounter errors with audiocraft installing, please refer to their docs here: <https://github.com/facebookresearch/audiocraft>)

## Run:
`python webui.py`

There's no need to download any external models, pick a model in the dropdown and when you hit run for the first time it will be automatically downloaded via audiocraft. If you want to use the melody mode, select the Melody model and a selector for your melody audio file will appear.

## Notes:
Files are saved to the `statc/audio/` directory.

The currently active model stays loaded in memory by default, if you want it to be unloaded after each generation, launch with `python webui.py --unload-after-gen`

The UI is in desperate need of an actual UI design if anyone wants to take on the task.

## Parameters:

- **Top-K**: Unclear how it affects generation, needs more testing.
- **Top-P**: Same as above.
- **Duration**: Length of generated music.
- **Classifier Free Guidance**: Controls creativity, lower number = "more creative freedom" in theory at least.
- **Temperature**: Also a sort of creativity guide, your outputs will be terrible if this is too high.
- **Segments**: Number of segments to generate. Each segment will be (duration-overlap) long, so if duration is 30 seconds and overlap is 5 seconds, with 3 segments, you will get 75 seconds of audio out.
- **Overlap**: The overlap for the segment, as explained above. More overlap = more consistent music between segments.
