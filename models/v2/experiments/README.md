# Experiments

These models are experiments for training microWakeWord models. They are minimally trained and tested, and are not supported in any way. Use for fun and at your own risk!

## Usage

To use, you must take control (or adopt) your ESPHome voice assistant and add the following to the YAML:

``` yaml
micro_wake_word:
  models:
    - model: "URL of the model JSON file"
      id: "unique id"
```

For example:

``` yaml
micro_wake_word:
  models:
    - model: "https://raw.githubusercontent.com/esphome/micro-wake-word-models/refs/heads/main/models/v2/experiments/choo_choo_homie.json"
      id: "choo_choo_homie"
```

After rebuilding the ESPHome firmware and updating the device, visit its device info page in Home Assistant to change the active wake word.


## Training

All of these models were trained with the [same notebook](https://github.com/kahrendt/microWakeWord/blob/november-update/notebooks/basic_training_notebook.ipynb) using the default settings.
