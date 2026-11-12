# aloudly-models

Model files that [Aloudly](https://aloudly.io) downloads the first time a
feature needs them. Aloudly is a dictation app from Aloudly Ltd that runs on
your own computer.

Only the files Aloudly Ltd had to convert or repackage are hosted here, as
release assets. Every other model comes straight from its publisher.
[NOTICE.md](NOTICE.md) lists all of them with their copyright holders,
licences and what was changed, and the licence texts are in
[LICENSES/](LICENSES).

None of these files is Aloudly Ltd's own work. Each stays under the licence
its authors gave it, named below, and is provided as is, without warranty.
Being hosted here does not mean its authors endorse Aloudly.

## parakeet-tdt-0.6b-v3-int8-ext-v1

The encoder of **NVIDIA Parakeet TDT 0.6b v3**, © NVIDIA Corporation, licensed
under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Upstream: https://huggingface.co/nvidia/parakeet-tdt-0.6b-v3

What was changed: NVIDIA's model was converted to ONNX and quantised to int8
by Fangjun Kuang (csukuangfj) for sherpa-onnx, published at
[csukuangfj/sherpa-onnx-nemo-parakeet-tdt-0.6b-v3-int8](https://huggingface.co/csukuangfj/sherpa-onnx-nemo-parakeet-tdt-0.6b-v3-int8).
Aloudly Ltd then re-saved that encoder in ONNX external-data form
(`onnx.save_model(..., save_as_external_data=True, all_tensors_to_one_file=True)`).
That is a change of file layout only. No weight was modified, added or
removed. It lets ONNX Runtime map the weights from disk.

- `encoder.int8.onnx`: the graph (42 MB)
- `encoder.int8.onnx.data`: the weights (610 MB). It must sit next to the
  graph file under this exact name.

The decoder, joiner and tokens are unchanged and are not hosted here.

## fastconformer-ar-int8-v1

**NVIDIA FastConformer Hybrid Large, Arabic**
(`stt_ar_fastconformer_hybrid_large_pcd_v1.0`), © NVIDIA Corporation, licensed
under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Upstream: https://huggingface.co/nvidia/stt_ar_fastconformer_hybrid_large_pcd_v1.0

What was changed: the CTC branch, converted to ONNX and quantised to int8 for
sherpa-onnx, as published by mah92 at
[mah92/sherpa-onnx-nemo-ctc-ar-fastconformer-hybrid-large-pcd-v1.0-non-streaming-int8-2024-12-25](https://huggingface.co/mah92/sherpa-onnx-nemo-ctc-ar-fastconformer-hybrid-large-pcd-v1.0-non-streaming-int8-2024-12-25)
(revision `d45a4313c470`). Aloudly Ltd added the three metadata fields
sherpa-onnx needs to load it (`vocab_size` 1025, `subsampling_factor` 8,
`normalize_type` per_feature). The weights are unchanged.

- `model.int8.onnx` (174 MB)
- `tokens.txt`

## kokoro-espeak-en-v1

The English data files of **eSpeak NG**, © Jonathan Duddington, Reece H. Dunn
and the eSpeak NG contributors, licensed under the
[GNU General Public License, version 3 or later](LICENSES/GPL-3.0.txt).
Upstream: https://github.com/espeak-ng/espeak-ng

What was changed: nothing in any file. These are the compiled data files
(`en_dict`, `phondata`, `phonindex`, `phontab`, `intonations`, `lang/`,
`voices/`) exactly as sherpa-onnx distributes them in
`kokoro-multi-lang-v1_0.tar.bz2`, with the other languages' dictionaries left
out.

**Source.** The files are compiled from `dictsource/` and `phsource/` in
eSpeak NG. sherpa-onnx builds eSpeak NG from
https://github.com/csukuangfj/espeak-ng/tree/ed530aa113046142eb5115cf2fc9157854d0ffe1
and the data's format version (`0x014801`) is the one that source produces.
The licence text is also attached to the release as `COPYING`.

- `espeak-ng-data-en.tar.gz`
