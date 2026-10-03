# ESPHome `micro_wake_word` Model collection

This repository serves to host `micro_wake_word` model files (`.tflite`) for ease of use with the `micro_wake_word` ESPHome component.

## Usage

These files can be used by referencing them by the filename without `.tflite`.

```yaml
micro_wake_word:
  ...
  models:
    - model: okay_nabu
```

## Model Training

See https://github.com/kahrendt/microWakeWord for details and instructions on training your own wake words.

## License

Apache License 2.0 — see [LICENSE](LICENSE) and [NOTICE](NOTICE).

These terms cover the entire contents of this repository, including the trained model weights (`.tflite`) and their manifests (`.json`). There are no separate or additional terms for the model binaries.

Wake word names may refer to products, services, or characters owned by third parties. They identify what each model detects and imply no affiliation or endorsement.
