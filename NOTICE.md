# Third-party notices

Aloudly is made by Aloudly Ltd. It is built on open-source software and
pre-trained models published by other people. This file names each one, who
holds the copyright, its licence, where Aloudly gets it and what was changed.
The licence texts it names are in the same folder as this file in an
installed copy of Aloudly, and in `LICENSES/` beside the published copy.

This file ships inside Aloudly (Settings, About, Credits, "Open licences
folder") and is published at
https://github.com/KCODE-UK/aloudly-models/blob/main/NOTICE.md.

Everything listed here is provided by its authors "as is", without warranty.
Each licence carries its own disclaimer. Being listed here does not mean any
of these authors endorse Aloudly.

## 1. Models

No model is inside the installer. Aloudly downloads each one to the user's own
computer the first time a feature needs it, from the place named under
"Obtained from", at the pinned revision shown, and checks every file against a
sha256 before using it. Files that Aloudly Ltd hosts itself are release assets
at https://github.com/KCODE-UK/aloudly-models/releases.

### NVIDIA Parakeet-TDT-0.6B-v3

Speech recognition for English and 24 other European languages.

- Copyright: NVIDIA Corporation.
- Licence: Creative Commons Attribution 4.0 International (CC BY 4.0),
  https://creativecommons.org/licenses/by/4.0/ (text: `CC-BY-4.0.txt`).
- Upstream: https://huggingface.co/nvidia/parakeet-tdt-0.6b-v3
- Obtained from: https://huggingface.co/csukuangfj/sherpa-onnx-nemo-parakeet-tdt-0.6b-v3-int8
  at revision `2bda32ec70b0` (decoder, joiner and tokens), and from
  `aloudly-models` release `parakeet-tdt-0.6b-v3-int8-ext-v1` (encoder).
- Changes: converted to ONNX and quantised to int8 by Fangjun Kuang
  (csukuangfj) for sherpa-onnx. Aloudly Ltd then re-saved the encoder in ONNX
  external-data form, as `encoder.int8.onnx` (the graph) and
  `encoder.int8.onnx.data` (the weights). That step changes the file layout
  only. No weight was modified, added or removed.

### NVIDIA FastConformer Hybrid Large (Arabic)

Speech recognition for Arabic. NVIDIA's name for it is
`stt_ar_fastconformer_hybrid_large_pcd_v1.0`.

- Copyright: NVIDIA Corporation.
- Licence: CC BY 4.0, https://creativecommons.org/licenses/by/4.0/
  (text: `CC-BY-4.0.txt`).
- Upstream: https://huggingface.co/nvidia/stt_ar_fastconformer_hybrid_large_pcd_v1.0
- Obtained from: `aloudly-models` release `fastconformer-ar-int8-v1`.
- Changes: the CTC branch, converted to ONNX and quantised to int8 for
  sherpa-onnx, as published by mah92 at
  https://huggingface.co/mah92/sherpa-onnx-nemo-ctc-ar-fastconformer-hybrid-large-pcd-v1.0-non-streaming-int8-2024-12-25
  (revision `d45a4313c470`). Aloudly Ltd added the three metadata fields
  sherpa-onnx needs to load it (`vocab_size`, `subsampling_factor`,
  `normalize_type`). The weights are unchanged.

### DataoceanAI Dolphin (small, CTC)

Speech recognition for Hindi, Japanese, Korean and Chinese.

- Copyright: DataoceanAI.
- Licence: Apache License 2.0 (text: `Apache-2.0.txt`).
- Upstream: https://github.com/DataoceanAI/Dolphin
- Obtained from: https://huggingface.co/csukuangfj/sherpa-onnx-dolphin-small-ctc-multi-lang-int8-2025-04-02
  at revision `c8b6689509ac`.
- Changes: the CTC branch only, converted to ONNX and quantised to int8 by
  Fangjun Kuang. Aloudly uses the files as published there.

### pyannote segmentation-3.0

Finds the stretches of a meeting recording that contain one voice.

- Copyright: (c) 2020 CNRS. Author: Hervé Bredin.
- Licence: MIT (text: `MIT.txt`).
- Upstream: https://huggingface.co/pyannote/segmentation-3.0
- Obtained from: https://huggingface.co/csukuangfj/sherpa-onnx-pyannote-segmentation-3-0
  at revision `9403a6902bb5`.
- Changes: converted to ONNX by Fangjun Kuang. Used as published there.

### NVIDIA NeMo TitaNet (small)

Decides which stretches of a meeting are the same person. Also used for the
optional voice print, which stays on the user's computer.

- Copyright: NVIDIA Corporation.
- Licence: Apache License 2.0 (text: `Apache-2.0.txt`). NVIDIA's model card
  for `titanet_small` says it is covered by the licence of the NeMo toolkit,
  https://github.com/NVIDIA/NeMo/blob/main/LICENSE.
- Upstream: https://catalog.ngc.nvidia.com/orgs/nvidia/teams/nemo/models/titanet_small
- Obtained from: https://huggingface.co/csukuangfj/speaker-embedding-models
  (`nemo_en_titanet_small.onnx`) at revision `0743f301363d`.
- Changes: converted to ONNX by Fangjun Kuang. Used as published there.

### Kokoro-82M

The voices for Read aloud.

- Copyright: hexgrad.
- Licence: Apache License 2.0 (text: `Apache-2.0.txt`).
- Upstream: https://huggingface.co/hexgrad/Kokoro-82M
- Obtained from: https://huggingface.co/csukuangfj/kokoro-multi-lang-v1_0
  at revision `7e9b67b79bfd` (`model.onnx`, `voices.bin`, `tokens.txt`,
  `lexicon-gb-en.txt`).
- Changes: converted to ONNX for sherpa-onnx by Fangjun Kuang. The
  pronunciation lexicon was generated there from hexgrad's misaki data
  (https://github.com/hexgrad/misaki, Apache License 2.0). Used as published.

### eSpeak NG data (English)

Pronunciations for words that Kokoro's lexicon does not contain.

- Copyright: Jonathan Duddington, Reece H. Dunn and the eSpeak NG
  contributors.
- Licence: GNU General Public License, version 3 or later (text:
  `GPL-3.0.txt`).
- Upstream: https://github.com/espeak-ng/espeak-ng
- Obtained from: `aloudly-models` release `kokoro-espeak-en-v1`
  (`espeak-ng-data-en.tar.gz`).
- Changes: none to any file. These are the compiled data files
  (`en_dict`, `phondata`, `phonindex`, `phontab`, `intonations`, `lang/`,
  `voices/`) exactly as sherpa-onnx distributes them in
  `kokoro-multi-lang-v1_0.tar.bz2`, with the other languages' dictionaries
  left out.
- Source: the files are compiled from `dictsource/` and `phsource/` in
  eSpeak NG. sherpa-onnx builds eSpeak NG from
  https://github.com/csukuangfj/espeak-ng/tree/ed530aa113046142eb5115cf2fc9157854d0ffe1
  and the data's format version (`0x014801`) is the one that source produces.

### Meta Llama 3.2 (1B Instruct and 3B Instruct)

The Summarize button. The 1B model is the "Fast" choice and the 3B model is
the "Better" one. Neither is used for speech recognition or for the text
Aloudly pastes.

Llama 3.2 is licensed under the Llama 3.2 Community License, Copyright ©
Meta Platforms, Inc. All Rights Reserved.

- Licence: Llama 3.2 Community License (text:
  `Llama-3.2-Community-License.txt`). Built with Llama.
- Use of these models must follow Meta's Acceptable Use Policy (text:
  `Llama-3.2-Acceptable-Use-Policy.md`, from
  https://www.llama.com/llama3_2/use-policy).
- Upstream: https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct and
  https://huggingface.co/meta-llama/Llama-3.2-3B-Instruct
- Obtained from: https://huggingface.co/onnx-community/Llama-3.2-1B-Instruct
  at revision `14007543b6dc92de88daf96a9aa85d2f95ace6ef`, and
  https://huggingface.co/onnx-community/Llama-3.2-3B-Instruct-ONNX at
  revision `20a709c49b57c1bbd761a54344a8b5eb5ad8939c`.
- Changes: converted to ONNX and quantised by the ONNX Community for
  Transformers.js. Used as published there.

## 2. Software inside the installer

### sherpa-onnx 1.13.8

Runs the speech, diarization and voice models.

- By the k2-fsa project (Next-gen Kaldi), https://github.com/k2-fsa/sherpa-onnx
- Licence: Apache License 2.0 (text: `Apache-2.0.txt`).
- Aloudly ships the prebuilt libraries from the npm packages
  `sherpa-onnx-node`, `sherpa-onnx-darwin-arm64` and `sherpa-onnx-win-x64`,
  unmodified.

Those prebuilt libraries contain other projects, built in by sherpa-onnx:

- **ONNX Runtime.** Copyright (c) Microsoft Corporation. MIT (text:
  `MIT.txt`). https://github.com/microsoft/onnxruntime
- **eSpeak NG.** Copyright Jonathan Duddington, Reece H. Dunn and the eSpeak
  NG contributors. GNU General Public License, version 3 or later (text:
  `GPL-3.0.txt`). It is compiled into `libsherpa-onnx-c-api.dylib` and
  `sherpa-onnx-c-api.dll`. Source:
  https://github.com/csukuangfj/espeak-ng/tree/ed530aa113046142eb5115cf2fc9157854d0ffe1
- The smaller libraries sherpa-onnx builds in are named, each with its source,
  in the `cmake/` folder of
  https://github.com/k2-fsa/sherpa-onnx/tree/v1.13.8

### uiohook-napi 1.5.5 and libuiohook

Listens for the dictation hotkey.

- uiohook-napi: Copyright (c) 2020 Alexander Drozdov. MIT.
  https://github.com/SnosMe/uiohook-napi
- libuiohook, which uiohook-napi contains: Copyright (C) 2006-2023 Alexander
  Barker. GNU Lesser General Public License, version 3 or later (texts:
  `LGPL-3.0.txt` and `GPL-3.0.txt`). https://github.com/kwhat/libuiohook

Aloudly uses libuiohook under the LGPL. Nothing in Aloudly's own terms
restricts modifying libuiohook or reverse engineering Aloudly to debug such a
modification.

**Replacing libuiohook.** Aloudly reaches libuiohook only through one file,
`uiohook-napi.node`, which sits outside the application archive:

- macOS: `Aloudly.app/Contents/Resources/app.asar.unpacked/node_modules/uiohook-napi/prebuilds/darwin-arm64/`
- Windows: `resources\app.asar.unpacked\node_modules\uiohook-napi\prebuilds\win32-x64\`
  in the folder Aloudly is installed to

To run Aloudly with a modified libuiohook, build uiohook-napi 1.5.5 from its
source against your version and put the resulting file there. On macOS the
change breaks the app's code signature, so sign it again for your own
computer: `codesign --force --deep --sign - /Applications/Aloudly.app`.

### Electron and Chromium

The application shell.

- Electron: Copyright (c) Electron contributors, Copyright (c) 2013-2020
  GitHub Inc. MIT. The text is `LICENSE.electron.txt`.
- Chromium and the projects it contains: `LICENSES.chromium.html`.

On Windows both files are in the folder Aloudly is installed to, next to
`Aloudly.exe`. On macOS they are in `Aloudly.app/Contents/Resources`.

### Transformers.js and ONNX Runtime Web

Run the Summarize models.

- Transformers.js: by Hugging Face. Apache License 2.0.
  https://github.com/huggingface/transformers.js
- ONNX Runtime Web: Copyright (c) Microsoft Corporation. MIT.

### Fonts

All four are under the SIL Open Font License, version 1.1. The licence text
is in `npm-packages.txt`, once under each font.

- Jost: Copyright 2020 The Jost Project Authors
  (https://github.com/indestructible-type/Jost)
- Outfit: Copyright 2021 The Outfit Project Authors
  (https://github.com/Outfitio/Outfit-Fonts)
- Arimo: Copyright 2020 The Arimo Project Authors
  (https://github.com/googlefonts/arimo)
- JetBrains Mono: Copyright 2020 The JetBrains Mono Project Authors
  (https://github.com/JetBrains/JetBrainsMono)

### Everything else from npm

React, electron-updater and the other npm packages Aloudly is built from are
listed in `npm-packages.txt`, each with its version, licence and the licence
file from its own package, copyright line included. That file is written when
Aloudly is built, so it exists in an installed copy and not in the published
copy of this folder.
