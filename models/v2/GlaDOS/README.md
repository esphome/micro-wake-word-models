# Your Personal GladOS
Here you will find trained tensor models for wake words of GlaDOS (in reference to the character in portal. These wake word models can be used in your home-assistant voice preview edition. Combined with a piper voice model and an llm you can have your very own GlaDOS personal assistant.

Here i have several models to choose from. "Hey Glados", "Glados please ... " and just plain "Glados" I found most success with "Hey Glados" (it's my 'daily driver'). I have also created response sounds. these replace the standard bell sound you here when the wake word is detected. The sounds are acknowledgements from glad indicating she is waiting for your prompt. there are 4 of them for you to choose from "what?", "what is it?", "How can i help you?" and "Oh, you again..."

using my yaml file you get the one of the 4 acknowledgements randomly chosen. The flow works like this:
- You say: "Hey Glados"
- Once recognized you hear: "Oh, you again" or "what is it" etc
- Then you speak your prompt
 - Then glados responds with her well known insulting style responses.

# YAML
if you don't want to use my yaml here are the basics:
### Wake words
find the micro_wake_word section, and in it the models subsection add the following lines:

```
micro_wake_word:
	models:
		id: glados_please
			- model: https://raw.githubusercontent.com/Darkmadda/ha-v-pe/refs/heads/main/glados_please.json
		id: hey_glados
			- model: https://raw.githubusercontent.com/Darkmadda/ha-v-pe/refs/heads/main/hey_glados.json
		id: glados
			- model: https://raw.githubusercontent.com/Darkmadda/ha-v-pe/refs/heads/main/glados.json
```
### Response sounds
find the media_player section, then the files subsection and add the following:
```
- id: wake_word_triggered_sound1
	file: https://github.com/Darkmadda/micro-wake-word-models/raw/main/models/v2/GlaDOS/response_sounds/GlaDOS_oh_you_again.mp3
- id: wake_word_triggered_sound2
	file: https://github.com/Darkmadda/micro-wake-word-models/raw/main/models/v2/GlaDOS/response_sounds/GlaDOS_what_is_it.mp3
- id: wake_word_triggered_sound3
	file: https://github.com/Darkmadda/micro-wake-word-models/raw/main/models/v2/GlaDOS/response_sounds/GlaDOS_how_can_i_help_you.mp3
- id: wake_word_triggered_sound4
	file: https://github.com/Darkmadda/micro-wake-word-models/raw/main/models/v2/GlaDOS/response_sounds/GlaDOS_what.mp3
```

and lastly change the yaml for playing the wake word detected sound
in the on_wake_word_detected section at the bottom change code in the 
```
- script.execute:
	id: play_sound
	priority: true
	sound_file: !lambda |-
		int random_value = rand() % 4; // Generates 0, 1, or 2
		if (random_value == 0) {
			return id(wake_word_triggered_sound1);
		} else if (random_value == 1) {
			return id(wake_word_triggered_sound2);
		} else if (random_value == 2) {
			return id(wake_word_triggered_sound3);
		} else {
			return id(wake_word_triggered_sound4);
		}
	- delay: 1300ms
```
Note that changing the response sound is optional and you may prefer to leave the acknowledgement sound the default

Adding the piper tts and the llm stuff can be done following the tutorial i found [here](https://www.xda-developers.com/glados-controls-smart-home-home-assistant/). that work was not done by me but is a big part of making glados work.

Eventually i think these files will make it into the main repo and when it does i'll alter the urls to point to there but for now this will work.

Here is a little video of these changes in action
[![Demo](https://img.youtube.com/vi/Ezj5yt7BYHQ/0.jpg)](https://www.youtube.com/watch?v=Ezj5yt7BYHQ)