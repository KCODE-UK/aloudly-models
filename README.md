# aloudly-models

Model files distributed for [Aloudly](https://aloudly.app), a local dictation app.

## Parakeet TDT 0.6b v3 (int8, external-data)

NVIDIA Parakeet TDT 0.6b v3 int8 weights, licensed **CC-BY-4.0, © NVIDIA**.

These are the same weights as
[csukuangfj/sherpa-onnx-nemo-parakeet-tdt-0.6b-v3-int8](https://huggingface.co/csukuangfj/sherpa-onnx-nemo-parakeet-tdt-0.6b-v3-int8)
on Hugging Face, with the encoder converted from a single self-contained ONNX
file to ONNX **external-data** format (`onnx.save_model(...,
save_as_external_data=True, all_tensors_to_one_file=True)`). This is a layout
change only — no weights were modified, added, or removed. External-data
layout lets ONNX Runtime memory-map the weight tensors instead of copying them
into anonymous heap, which is the reason this conversion exists.

Distributed under the original **CC-BY-4.0** licence, with attribution to
NVIDIA and to csukuangfj's conversion.

Release `parakeet-tdt-0.6b-v3-int8-ext-v1` carries two assets:

- `encoder.int8.onnx` — the graph (~40 MB)
- `encoder.int8.onnx.data` — the external weight data (~582 MB), must sit
  next to the graph file with this exact name

`decoder.int8.onnx`, `joiner.int8.onnx`, and `tokens.txt` are unchanged from
the upstream repo and are not re-hosted here.
